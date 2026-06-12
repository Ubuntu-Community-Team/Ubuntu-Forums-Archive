---
title: "how do I check the md5 of a burnt feisty CD?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-21
I have got my Feisty 7.04 64-bit CD in my CD drive. What program can I use to check the data is all as it should be?

I looked and saw a file full of md5's but they seem to be for individual files.

I've actually installed successfully off this CD before, but have encountered a couple of strange minor bugs in the weeks since installing the OS.. so just before I do a full reinstall I wanted to double check everything is as it should be.

I think I remember there's a check-cd-for-defects option on the cd when it boots.. but is there anything else that I could check the whole CD with.

---

### Post by ruscoe on 2007-06-21
You're best booting from the CD and selecting the disk test option. It doesn't take too long.

There are md5s that you can download from the same place as the isos, but those are only good for checking the iso before you burn it.

---

### Post by ecs_pf5 on 2007-06-21
Out of interest, does that boot option to check the CD make use of that md5 list that's in the root of the CD?

'md5sum.txt'

---

### Post by ruscoe on 2007-06-21
Probably.

---

### Post by EagleRock on 2007-06-21
If you were having trouble with the burnt CD, you might want to test the .iso you downloaded as well.  I don't know if you have access to Linux right now, but checking an md5sum is as easy as:

```
md5sum ubuntu-7.04-desktop-i386.iso
```

Then, read off the md5sum on the site and make sure you downloaded it fine.  Then you can burn and test CD if you want.

---

### Post by ecs_pf5 on 2007-06-21
Thanks guys, CD seems fine, it ran straight through the boot menu disk check then declared itself valid.

I want to reinstall with exactly the same settings as I have now pretty much, so what config files might be worth backing up before I trash the current install?

I'm thinking

grub files (I customised grub a little)
xserver config files (I had to reconfigure xorg.conf & load the fglrx driver for my ati card)

anything else spring immediately to mind before I go for it?

already done all my progs / data

---

### Post by EagleRock on 2007-06-21
Only other thing I can think of is all of the hidden folders in your /home directory (You might just want to copy your /home directly).  Other than that, you should be good.  If you hit an "ls -l ~" you can see all of your settings files/directories that might be of interest.

---

### Post by Yoooder on 2007-06-21
> **ecs_pf5 said:**
> Thanks guys, CD seems fine, it ran straight through the boot menu disk check then declared itself valid.

I want to reinstall with exactly the same settings as I have now pretty much, so what config files might be worth backing up before I trash the current install?

I'm thinking

grub files (I customised grub a little)
xserver config files (I had to reconfigure xorg.conf & load the fglrx driver for my ati card)

anything else spring immediately to mind before I go for it?

already done all my progs / data

depending on the size of your /etc folder you may just want to back the whole thing up.  It stores the majority of system config files, and (backup space permitting) could save some hassle with the fresh install.

---

### Post by swoll1980 on 2007-06-21
If you have windows you have to install md5sum [www.download.com/md5sum](www.download.com/md5sum)

---

