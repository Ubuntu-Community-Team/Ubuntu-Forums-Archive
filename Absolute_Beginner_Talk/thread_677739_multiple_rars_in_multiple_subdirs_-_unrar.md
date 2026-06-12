---
title: "multiple rars in multiple subdirs - unrar?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by yrufset on 2008-01-25
Hello all.
let's say iv'e got a dir called ABC, and it contains the next subdirs: ABC1, ABC2... ABC19.
in any of the ABC1..19 i got rar archives (rar, r00...r19).

you can look at it as if it's the whole season of McGyver or something, and every dir' is one episode.

my goal is to unrar all of the subdirs to ONE folder, in the shortest way.

what i'm doing now, is Extract Here... for every subdir (which take decades), and then go dir' by dir', copying the extracted file into the new dir'.

in windows there used to be an app which lets you r-click a dir, then choosing 'search for archives' which would generate a new window with all of the archives found on that dir', and then you could unrar them all to a new location with one click.

any help will be much appriciated :)

---

### Post by renzokuken on 2008-01-25
sounds like a job for a quick shell script. sadly i suck at writing scripts but there are infinitely clever people on here who could help you mash one up.

you could run one script then go away for a bit while it does its job.

---

### Post by gvartser on 2008-01-25
Try this out.

Prereq's:

*REMOVED*


Good luck,
/g

---

### Post by yrufset on 2008-01-25
First of all i would like to thank you for the fast response.
second, i saved the code, called it ultrar.
i copied it to ABC folder, opened a terminal and run: ./ultrar /home/myuser/down
and i got: 
bash: ./ultrar: Permission denied

tried to sudo. no luck there too: 
sudo: ./ultrar: command not found

any suggestions?

thanks again....

---

### Post by gvartser on 2008-01-25
Yes you must make it executable:

*(All files that you want to make executable/runnable you need to attach the x permission bit on.) *

_How to make it executable/runnable:_
```
chmod +x ultrar
```

Best regz,
/G

---

### Post by yrufset on 2008-01-25
Well, i did the chmod (how newbie of me to forget that :)), and yet i got:
./ultrar: 32: Syntax error: Bad substitution

anyway, i found a soultion!!
it was in an old post about some other question, but it did the trick:
i used the 'find'  command to search the whole dir' and along with the -exec parametr i unrar every file that was found.

code:
find -type f -name '*.rar' -exec unrar x {} \;

**_Thanks a lot_** for your effort any way...
much appriciated!

---

