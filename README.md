# @smidhonza/pipe

A tiny TypeScript `pipe` helper for passing a value through functions from left to right.

It is useful when nested function calls start looking like a bowl of spaghetti and you would rather read the steps in the order they happen.

## Install

```sh
npm i @smidhonza/pipe
```

## Usage

```ts
import { pipe } from "@smidhonza/pipe";

const result = pipe(
    " hello pipe ",
    (value) => value.trim(),
    (value) => value.toUpperCase(),
    (value) => `${value}!`,
);

console.log(result);
// "HELLO PIPE!"
```

Each function receives the return value of the previous one:

```ts
const count = pipe(
    ["tea", "coffee", "water"],
    (drinks) => drinks.filter((drink) => drink.length > 3),
    (drinks) => drinks.length,
);

// count is typed as number
```

## Why?

Instead of this:

```ts
const result = shout(trim(input));
```

You can write this:

```ts
const result = pipe(input, trim, shout);
```

That way the code reads like a small recipe: take this value, do this, then this, then done.

## Types

`pipe` is fully typed for up to 11 transformation functions.

That should be enough for most reasonable pipelines. If you need more than that, your code might be asking for a snack break and a refactor.
