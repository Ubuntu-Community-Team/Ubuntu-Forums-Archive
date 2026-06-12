---
title: "home schooled"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Anoobiz on 2006-11-21
so ive recently discovered vimtutor and man what a lifesaver and plz dnt ban me 4 asking but is there a "sedtutor" or "greptutor" God knows ive tryd but maybe just maybe the tutor has a diff name... anybody? thx 4 the help agen ppl :)

---

### Post by Anoobiz on 2006-11-21
im guesing man is the only man to consult on this topic... thx neway ppl :p

---

### Post by IYY on 2006-11-21
I don't think there is a tutor like that for grep and sed... However, there are many tutorials online you can look at. Grep is actually a very simple tool and you can figure it out quickly by just reading the manual (man grep). sed can be trickier, and you can search for online tutorials, or go to the library and read the book on sed and awk (it's from O'Reily). 

Of course, feel free to ask questions on these forums about these commands. If you don't know anything at all about sed and grep, here are the two most basic uses:

To display all lines in the file filename.txt that contain the word 'somestuff', use

```
grep somestuff filename.txt
```

The same can be done using a pipe, to demonstrate reading from standard input:

```
cat filename.txt | grep somestuff
```

Replace somestuff with the following to make only the lines that *start* with somestuff appear:

```
^somestuff
```

And for the lines that end with somestuff:

```
somestuff$
```

The character . (period) can be used to represent a single wildcard character. So you could use the following to match somestuff, samestuff, s1stuff, s&stuff, etc:

```
s.mestuff
```

To allow any sort of space, you can use .* (any character, repeated any number of times). Here's a complex search pattern that will give you all lines that start with 'some', end with 'stuff' and have anything in between.

```
^some**.***stuff$
```

I don't use sed often, but here's a command that's very handy. To replace all instances of the word 'some' with the word 'stuff' in a file somefile.txt, just use:

```
sed s/some/stuff/g somefile.txt
```

Note that the above also works in vi, with a slight modification:

```
**:%**s/some/stuff/g
```

Note that the sed example prints out to the screen. You can redirect it to a new file using 

```
sed s/some/stuff/g somefile.txt **> newfile.txt**
```

but you might often want to make the changes in place in somefile. For this, use:

```
sed **-i** s/some/stuff/g somefile.txt
```

To be perfectly honest, that's all I know about grep and sed from memory. If I need anything else, I look at a tutorial or check the man pages.

---

