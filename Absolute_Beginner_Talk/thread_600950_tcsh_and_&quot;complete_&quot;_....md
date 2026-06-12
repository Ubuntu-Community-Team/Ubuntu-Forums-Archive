---
title: "tcsh and &quot;complete &quot; ..."
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by hoaf on 2007-11-02
Not sure if this is the right place to ask this question, but ...

... I'm having a pretty rough time wrestling with the "complete" command in **tcsh**.

Basically, I have a script that is being accessed using a "complete" statement, and I want to use the very same script to help determine its own tab-complete options.

It works pretty well for my purposes, but I'm stumped as to how to pass an indetermanent (sp?) amount of command line options to the script in **tcsh**'s "complete" syntax.

Here's what I have so far:

```
complete xxx \
    'c/--/(area help)/' \
    'c/-/(h a)/' \
    'n/{-h,--help}/x:HELP\!\!1\!1\!\!/' \
    'n@{-a,--area}@`myscript.py xxx -q **$:1 $:2 $:3 $:4 $:5 $:6 $:7 $:8**`@' \
    'p@*@`myscript xxx -q **$:1 $:2 $:3 $:4 $:5 $:6 $:7 $:8**`@'
```

(The "-q" option tells the script to parse/verify/print the appropriate info back to the screen, and all of the numbered arguments are used by the script at run time.)

Is there any way I can collapse the $:1 $:2 ... $:8 down to something that'll allow me an "infinite" amount of command line options?

Again, I apologize if this isn't the right place to ask this question -- and I'd really appreciate any help.

Cheers!

---

