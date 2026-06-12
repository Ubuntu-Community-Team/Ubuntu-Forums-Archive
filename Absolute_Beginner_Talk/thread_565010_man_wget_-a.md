---
title: "man wget -a"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-01
If you write in the command line

```
man wget -a
```

Then, once you quit the first page, it prompts you again with the same page (page 1). Is this a bug or something?

---

### Post by bodhi.zazen on 2007-10-01
looks like it ...

---

### Post by Dr Small on 2007-10-01
You could report it on Launchpad.net

---

### Post by FranMichaels on 2007-10-01
> **Fixman said:**
> If you write in the command line

```
man wget -a
```

Then, once you quit the first page, it prompts you again with the same page (page 1). Is this a bug or something?

Why aren't you putting 
man wget

:confused:

Do not file a bug on this. It is not one. 
It's just taking "man wget" then whatever you put after it as a parameter for man.
If you want to filter results out, use grep.

man wget | grep -e -a

This will return every line with -a in it. grep is a great tool, but I'm still a novice with it :KS

You can also do
man wget
then type /-a. hit enter. 
Works as a search just like in Firefox. :)
/ then enter will search again.

wget --help 
is also good. I forgot that one! :razz:
wget --help | grep -e -a
Still works too.

P.S. Ok, for sure it is not a bug.
I did
man man
and turns out -a shows the intro pages
> 
man -a intro
           Display,  in  succession,  all  of the available intro manual pages
           contained within the  manual.   It  is  possible  to  quit  between
           successive displays or skip any of them.

:biggrin:

---

