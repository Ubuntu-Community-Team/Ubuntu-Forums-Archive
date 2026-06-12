---
title: "[SOLVED] splash image external hd"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-08-03
Hello, I've been trying to get the splash image to load.

Questions (details are below)?
Why the .gz, why not just .xpm files.  Isn't .gz compressed?

Secondnly, can I load multiple splashimage lines to get one to work?

Is the error in the directory tree or the file itself?  One of those two.

The image could be wrong (corrupt, wrong file type) or some funky hdx,y stuff could be happenign because I'm booting from an external hd.  

I've tried the following configurations in menu.lst (5 seperate boots):

splashimage=(hd1,0)boot/grub/images/debian.xpm
splashimage=(hd1,1)boot/grub/images/debian.xpm
splashimage=(hd1,1)boot/grub/images/space.xpm
splashimage=(hd1,1)boot/grub/images/space.xpm.gz
splashimage=(hd1,1)grub/images/space.xpm.gz

My root title is:

title		[hd0,0]_windows_xp_me_
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

---

### Post by johntkucz on 2007-08-03
okay, how have all these tutorials been completely TOTALLY WRONG!!????!!

All the splash image tutorials say the menu.lst format looks like:

(hdx,y)boot/grub/splashimage.xpm.gz.

That's WRONG! it doesn't work!?? How is that no one pointed that inaccuracy out?!! I went through about a dozen reboots to try to get it to reboot with various file times and directory tree structures.

It's (hdx,y)/ (Slash -- as in "/")boot/grub/splash.xpm.gz

!!!

How has no one posted that!! Ridiculous.  Well, Atleast I solved it (on my own, once again, although I rarely recieve answers from anyone other than myself, posting to this board feel remarkably helpful.  I couldn't have solved most of these bugs and problems without posting -- that jumpstarts the solution of sorts, I guess!).

---

### Post by johntkucz on 2007-08-03
okay I guess I must have found one tutorial with the wrong directory directory tree (missing hte first splash). others seem to have it.

---

