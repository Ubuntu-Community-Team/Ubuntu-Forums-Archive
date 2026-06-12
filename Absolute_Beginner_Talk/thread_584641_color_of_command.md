---
title: "color of command"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-21
I was wondering if there was a way to change the color of the output of a command.

for example if I wanted all the output of ls to be green then is there a way to do this?

perhaps something like:
```
 ls --color=green 
```

---

### Post by Hospadar on 2007-10-21
well.  you have a couple options.  there is a file somewhere (I honestly don't know where) to configure ls that lets you change all the colors for different filetypes to whatever you want.

Other than that, there might be something in your .bashrc file to change the colors.

Or you might be able to find a program that reads from stdin and outputs to a certain color.  I don't know what that program might be, but it seems likely it would exist.  you'd use the | operator to do the piping for something like this (the same way you pipe output to grep)

I would imagine it would look something like this:
ls | colorchanger -green

---

