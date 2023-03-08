
```Typescript
type A = string;
```

```mermaid
graph TB
    p["program"]
    p--> statement
    --> tad["Type Alias Declaration"]
    --> n["name"]
    --> id["Identifier (text: 'A')"]
    tad--> type["type = StringKeyword"]
```


```TypeScript
import { readFile } from "fs";
const myFunc = async (x: string): Promise<string> => {
  return x + ' world!';
};
```

```mermaid
graph TB
    p["program"] --> s[["statements[]"]]
    s .-> ImportDeclaration
    s .-> VariableStatement
    ImportDeclaration -- importClause --> ImportClause
    ImportClause -- namedBindings --> NamedImports
    NamedImports .- ee[["elements[]"]] .->
    ImportSpecifier -- name --> id2[Identifier]
    id2 -. escapedText .-> rf(("'readFile'"))
    ImportClause -- moduleSpecifier --> StringLiteral
    .-> tt(("'fs'"))
    VariableStatement -- declarationList --> VariableDeclarationList
    .-> dd[["declarations[]"]] .-> VariableDeclaration
    -- name --> i[Identifier] -. escapedText .-> mf(("'myFunc'"))
    VariableDeclaration -- initializer --> ArrowFunction
    ArrowFunction --> mods[["modifiers[]"]]
    mods .-> AsyncKeyword
    ArrowFunction -- type --> TypeReference
    -- typeName --> idn[Identifier] -. escapedText .-> pp(("'Promise'"))
    TypeReference .-> ta["typeArguments[]"]
    ta .-> StringKeyword
    ArrowFunction .-> params[["parameters[]"]]
    params .-> Parameter
    Parameter -- name --> id3[Identifier] -. escapedText .- x(("'x'"))
    Parameter -- type --> sk2[StringKeyword]
    ArrowFunction -- body --> Block -->
    s2[["statements[]"]]
    s2 .-> ReturnStatement
    ReturnStatement -- expression --> BinaryExpression
    -- left --> id4[Identifier] -. escapedText .-> et5(("'x'"))
    BinaryExpression -- operatorToken --> PlusToken
    BinaryExpression -- right --> sl3[StringLiteral] -. text .-> t((' world!'))
```
