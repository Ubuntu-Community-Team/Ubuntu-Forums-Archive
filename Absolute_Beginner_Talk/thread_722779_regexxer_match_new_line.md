---
title: "regexxer match new line"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by ralphz on 2008-03-12
Hi

Does anyone know how to match new line in the regexxer program?

I'm trying to find all occurrences of '{' presided by new line.

I tried many combinations and it seems like I have no luck. In theory '\n{' should work but it does not :(

Ralph

---

### Post by lloyd_b on 2008-03-12
> **ralphz said:**
> Hi

Does anyone know how to match new line in the regexxer program?

I'm trying to find all occurrences of '{' presided by new line.

I tried many combinations and it seems like I have no luck. In theory '\n{' should work but it does not :(

Ralph

Try "^{".  This is not exactly what you asked for - it detects a "{" character immediately following the start of a line (the "^").  It's different from what you asked for in that it will match if there's a "{" as the first character of the first line, where a search for "<newline>}" would not.

Lloyd B.

---

### Post by ralphz on 2008-03-12
Hi

Thank you for response. What I'm really trying to do is to if to match new line and curly brace something like this:

function FOO()
{


and replace new line with nothing to get something like this:

function FOO(){

that would be the first step then I can add regex expression to match whitespace between curly brace and beginning of the line.

Ralph

---

### Post by lloyd_b on 2008-03-12
> **ralphz said:**
> Hi

Thank you for response. What I'm really trying to do is to if to match new line and curly brace something like this:

function FOO()
{


and replace new line with nothing to get something like this:

function FOO(){

that would be the first step then I can add regex expression to match whitespace between curly brace and beginning of the line.

Ralph

Did some googling, and found the following:
```
sed ':a;N;$!ba;s/\n{/{/g' file
```

Which does seem to do what you want.  Please don't ask me to explain why it works because I don't really understand it.  It seems to be a standard solution to the "can't find newlines in regexes", so hopefully it will work for you.

Lloyd B.

---

### Post by ralphz on 2008-03-13
Hi

Sorry it does not work fro me :(

---

