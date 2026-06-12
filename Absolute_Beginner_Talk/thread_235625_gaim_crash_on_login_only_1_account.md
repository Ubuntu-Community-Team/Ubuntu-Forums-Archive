---
title: "gaim crash on login: only 1 account"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by imaiden22 on 2006-08-13
alright, well I recently finished the problem with flash having no sound in my firefox, but as soon as that problem was finished this problem sprung up. Everytime I click GAIM from my panel it crashes as soon as I sign on. I tried running it in the terminal and this is the output.
```

nick@nick-desktop:~$ gaim
Creating link /home/nick/.kde/socket-nick-desktop.
can't create mcop directory

```
and it surprises me because im on 32 bit Ubuntu (w/ GNOME of course) on an AMD64 processor.


Any help would truly be appreciated.

---

### Post by jordilin on 2006-08-13
> **imaiden22 said:**
> alright, well I recently finished the problem with flash having no sound in my firefox, but as soon as that problem was finished this problem sprung up. Everytime I click GAIM from my panel it crashes as soon as I sign on. I tried running it in the terminal and this is the output.
```

nick@nick-desktop:~$ gaim
Creating link /home/nick/.kde/socket-nick-desktop.
can't create mcop directory

```
and it surprises me because im on 32 bit Ubuntu (w/ GNOME of course) on an AMD64 processor.


Any help would truly be appreciated.

32 bit Ubuntu in a 64 bit platform? Why don't you try installing the 64 bit Ubuntu version? Perhaps that's the reason you are getting the errors.

---

### Post by imaiden22 on 2006-08-13
I doubt that's the problem because for about 5 days prior to today gaim was working fine, and it Gaim 2 beta and i've had no problems until today...could it possibly be because i disabled ESD sounds to get my flash in firefox working? But yeah i've tried the 64 bit version of kubuntu on the same processor and i didn't like having to force install and search for buggy 64 bit versions of programs

---

### Post by Loco_gr on 2006-08-20
I have the same problem with Gaim 1.5 !!

That is what i get when i run it from terminal:

```

thanasis@linux:~$ gaim
Gaim has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

It is possible that this bug is already fixed in CVS.
If you can reproduce the crash, please notify the gaim
maintainers by reporting a bug at
http://gaim.sourceforge.net/bug.php

Please make sure to specify what you were doing at the time,
and post the backtrace from the core file. If you do not know
how to get the backtrace, please get instructions at
http://gaim.sourceforge.net/gdb.php. If you need further
assistance, please IM either SeanEgn or LSchiere and
they can help you.
Aborted


```

I am downloading right now the Gaim 2.0 beta3 to see if it's going to work.

---

### Post by Slade Winstone on 2006-08-22
I get sudden crashes with Gaim as well.  Running Gaim in a console I also get "can't create mcop directory".

It seems like this is a known libao (arts) problem.

[https://launchpad.net/distros/ubuntu/+source/libao/+bug/38353](https://launchpad.net/distros/ubuntu/+source/libao/+bug/38353)

Try this fix:

1) Go to: Preferences > Sounds
2) Change the sound method to something other than "Arts" or "Automatic".  I used ESD.

This fixes the problem for me...

Slade.

---

### Post by Slade Winstone on 2006-08-22
Sorry just noticed you'd switched off ESD... somebody also seems to have had some success manually creating the mcop directory.

[http://beranger.org/index.php?article=1378](http://beranger.org/index.php?article=1378)

Hope one of these helps

Slade.

---

