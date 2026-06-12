---
title: "Permissions Problem"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by NMZmaster on 2007-03-07
Well, here I was thinking that I'd gotten off easy after my first day of Linux, but somehow this problem cropped up which is beyond my meager ability to solve.

When I attempt to log in, I am told that my home directory is listed as "/home/kirk," which is correct, but that "it doesn't exist."  I'm asked to log in as root, instead, to which I agree.  I'm then told that "$HOME/.dmrc" is being ignored, and it should have 644 permissions set.  I press Okay (my only option) and am told that my session lasted less than 10 seconds, so there may have been an installation error or something of the sort.

Does anyone have any ideas on how to help?  I'm out of my league with this... one afternoon has me interested in Ubuntu, but I'm still at a crawl.  And for now, I'm locked out.

---

### Post by daveoily on 2007-03-08
can you get to a command line?

if so, you could set the root password (not recommended on security grounds apparently, but i reckon having access to the root account helps with so much stuff that i went and did it anyway!) using sudo...

I forget the exact commands, but they're on the forum somewhere...

from inside the root account you could change the permissions of whatever file you need to :)

---

### Post by Mr. C. on 2007-03-08
Type Ctrl-Alt-F1 and this will bring you to a command shell.

Enter your username and password at the command line.  This will log you in, despite not having a home directory.  Enter the following commands after you login:

```
sudo mkdir -m 755 /home/kirk
sudo chown kirk:kirk /home/kirk
```

Then you can type exit to leave the command shell, and return to the graphical login with Ctrl-Alt-7 .  Try your login again.

MrC

---

### Post by Archmage on 2007-03-08
It seems that you haven't mount the /home-Partition at all.

---

### Post by Mr. C. on 2007-03-08
Only if a separate partition for /home was created during the installation.

Most will have /home being the / file system.

MrC

---

### Post by NMZmaster on 2007-03-08
Okay, I booted into the command line instead of GNOME and was able to enter that code as root; everything is back to working the way it was before.  Thanks so much!

---

### Post by Mr. C. on 2007-03-08
You're welcome.  Glad things are up and running again.

Best of luck,
MrC

---

