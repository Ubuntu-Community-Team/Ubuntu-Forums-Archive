---
title: "accessing conf files in rescue mode"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by dbclinton on 2008-01-10
I've crashed my xorg.conf file and I'm trying to recover in rescue mode but running commands like 

sudo nano /etc/x11/xorg.conf 
or 
dpkg-reconfigure xserver-xorg

aren't working - I get "file doesn't exist" error messages (or something similar).

By the way, is there an equivalent of Windows' graphic "safe mode" for ubuntu? That was very convenient for the comman-line challenged.
Thanks,
David

---

### Post by taurus on 2008-01-10
Try it with capital X this time.

```
nano /etc/**[COLOR="Blue"]X[/COLOR]**11/xorg.conf
```

---

### Post by dbclinton on 2008-01-10
Wow. Spelling counts!
I'll try that to see if it works.
Thanks so much!

---

### Post by wolfen69 on 2008-01-10
yeah, it has to be CAPITAL X.

---

### Post by nowshining on 2008-01-10
here is a tip for u - pressing tab on ur keyboard auto-completes

example typing

/et

then the tab key will result

/etc/

then 

X

tab

/etc/X11

tjem

/etc/X11/xo

tab

/etc/X11/xorg.conf

if tab doesn't work pressing TAB twice in a row will show u more optional words that start with that/those letters, keep adding a letter until none of the others but one match it.

also in the currect direcoty

ls
(yes small L) shows the current directoy items, 

ls -a

shows all incl. hidden files.

Hidden files are with a DOT in front of them

.hidden

in nautilus they are not shown and neither are backup files

Press CTRL +h on ur keyboard to show them

backuped files show a ~ after them, when u make a new document and save they are auto-backed up example

creat a new document hi

save

open it up again and edit it, press save and a hidden file named hi~ is created.

By the way linux does NOT care much about file name extensions so no need to put it after the file name, if it's a script it will know it, or just a plain txt file, etc.. and so forth..

---

### Post by buccaneere on 2008-01-10
> **dbclinton said:**
> I've crashed my xorg.conf file and I'm trying to recover in rescue mode but running commands like 

sudo nano /etc/x11/xorg.conf 
or 
dpkg-reconfigure xserver-xorg

aren't working - I get "file doesn't exist" error messages (or something similar).

By the way, is there an equivalent of Windows' graphic "safe mode" for ubuntu? That was very convenient for the comman-line challenged.
Thanks,
David

[HTML]sudo dpkg-reconfigure -phigh xserver-xorg
[/HTML]

---

### Post by dbclinton on 2008-01-11
Hi,
I'll assume paying more attention to syntax would have done the trick, but, before I tried that, I gave 

sudo dpkg-reconfigure xserver-xorg

one more try (yes, I think that's the actual command I typed) and it got the job done perfectly (it seems that the framebuffer setting was the problem).
Thanks to everyone - I'll make good note of all the syntax tips and I hope other people will be helped too.
David

---

### Post by dbclinton on 2008-01-11
>  here is a tip for u - pressing tab on ur keyboard auto-completes
>  example typing
>  /et
>  then the tab key will result
...

It's a shame that this information isn't visually available when in rescue mode...

---

