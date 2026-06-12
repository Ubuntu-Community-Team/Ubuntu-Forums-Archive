---
title: "Quick terminal question on specifying file ranges"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by SlaughterDog on 2007-10-28
Let's say I have a folder with a bunch of files. I want to hide most of them. How can I do this via the terminal? Last time I did this, I typed mv file .file and that took forever. I would think I should be able to just specify a range and have it add a . to the beginning of each file, yes?

---

### Post by disturbedite on 2007-10-28
you could use a mass renaming utility.  there are a few of them, but i prefer gwenrename.

---

### Post by nick_h on 2007-10-28
Something like:
```
for f in *; do mv "$f" ."$f"; done
```
changing the wildcard to suit your needs.

---

### Post by erginemr on 2007-10-28
> **nick_h said:**
> Something like:
```
for f in *; do mv "$f" ."$f"; done
```
changing the wildcard to suit your needs.

Nice move. But out of curiosity, how can we do it backwards? That is, how can we drop the preceding dots from a bunch of hidden files using bash?

---

### Post by nick_h on 2007-10-28
With something like:
```
for f in .[^.]*; do mv "$f" "${f#.}"; done
```
you made me think about that one :)

There is also the option to use the rename command.

---

### Post by erginemr on 2007-10-28
Thanks bro for your excellent tip. That renewed my faith in the power of bash.

---

### Post by SlaughterDog on 2007-10-29
I must say I don't really follow that (hence why I'm posting in the ABT forum) but wouldn't that do all of the files in the folder? I there's several I don't want to rename.

---

### Post by nick_h on 2007-10-29
I'm sorry this has got a bit complicated for ABT.  I was trying to demonstrate that you can use a loop in a script or at the command line.

The example I gave will act on all files that don't start with a "." because that is what "*" will expand to.

If you wanted all ".jpg" files, for example, you would use "*.jpg".

For all files beginning with "a", "b", or "c" you would use "[a-c]*".
For all files ending with "x", or "q" you would use "*[xq]".

My last example used ".[^.]*" meaning files starting with a "." followed by any character that is not a "." followed by any characters.

You can get even more complex if required.

For documentation type:
```
yelp man:bash
```
and read the section "Pathname Expansion".

If you want to test a pattern I suggest you use:
```
for f in *; do echo "$f"; done
```
(Replace the "*" with the pattern you want to test.)
This will just print the files matched to the terminal.

If you need any more help post here again and I'll try to help.

---

### Post by stroyan on 2007-10-29
nick_h- You don't need to use sed for removing "." from a file name like-
   for f in .[^.]*; do mv "$f" `echo $f | sed 's/\.//'`; done

Bash can do simple string substitutions itself.
${f#pattern} will remove a pattern from the front of $f.
${f%pattern} will remove a pattern from the back of $f.
This command will rename all files that start with "." and
a non-dot character.

   for f in .[^.]*; do mv "$f" "${f#.}";done

---

### Post by nick_h on 2007-10-29
Good point.  I think I need to read the parameter expansion section of the man page myself. :)

---

