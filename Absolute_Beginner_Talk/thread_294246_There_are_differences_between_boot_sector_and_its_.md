---
title: "There are differences between boot sector and its backup."
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by podunk on 2006-11-06
Edit - I was able to resolve this one I had the machine up and running good enough to do a restore of my backup, so it's a a software problem not a hardware one.

My second problem here is while booting i get the following error:
```

There are differences between boot sector and its backup.
Differences: (offset:original/backup)

```

There is something basically wrong here. The first time i set up dapper on the machine it came right up, no problems. It was pretty snappy. This time it won't start into the desktop and it is S_O_L_W, the Live dvd runs faster than the installed system.

I just reformatted root (I have /home on it's own partition) and reinstalled, and have the same problems, can't get to the desktop as normal user but can as root, extreemly slow

I found a how to here, trouble is it is a mandriva Linux one:
[http://club.mandriva.com/xwiki/bin/view/KB/AdminArecov3](http://club.mandriva.com/xwiki/bin/view/KB/AdminArecov3)

and it recommends booting from a cd, switching root from the virtual file sytem to my hard drive and executing:
```
grub-install /dev/hda
```

Will this work?

---

### Post by ZipoTe on 2007-01-08
Ei man!! same trouble here! :P

I don't know what happendeb but my brother's computer has the same problem. What can i do for solving that?

---

### Post by lnxnubie on 2007-01-16
hey 
[COLOR="Red"][FONT="Courier New"]dosfsck -arv /dev/hda1[/FONT][/COLOR]
worked for me !!:p

---

### Post by cool on 2007-01-18
> **lnxnubie said:**
> hey 
[COLOR="Red"][FONT="Courier New"]dosfsck -arv /dev/hda1[/FONT][/COLOR]
worked for me !!:p

hello, I want to ask U. Yesterday, I get some trouble like that. And this is the firts time I use Linux. So, could U explain to me where I must write that code, to solve my problem. Thank you very much... :p :p :p

---

### Post by John Wiersba on 2007-01-19
[COLOR="Red"]dosfsck -arv /dev/hda1[/COLOR]

You probably don't need to do that.  What I did was to skip checking FAT32 drives when I boot, since it takes a long time and is apparently not totally accurate (witness the boot sector/backup error message).  To skip running fsck on FAT32 drives, you can change the sixth (last) field for the vfat (i.e. FAT32) entries in /etc/fstab.  The sixth field is currently a 1 or 2.  If you change it to 0, it will skip running fsck during boot for those partitions.  Instructions:

sudo gedit /etc/fstab
Look for lines that say vfat; those are the ones which are mounting FAT32 partitions.  Change the 6th column to 0 (from a 1 or 2).
Save the file.
Reboot and check that fsck isn't running for those disk partitions.  On my system, I used Ctrl-Alt-F8 to see the boot messages and Ctrl-Alt-F7 to get back to the normal ubuntu GUI screen.

---

### Post by prince_niceguy on 2007-01-25
hi john wiersba...

thanks... that speed up my boot up like anything... but am little worried should the fschk be run to check the integrity of the file system???

thanks agian... do reply when you get time...

---

### Post by turezky on 2008-02-04
Hm.. Yep, got this problem too, so i just set the 6th column to "0" like **John** advised, but have the same hesitations as **prince_niceguy**...
any ideas, whether the *file system check* **really should** have take place???

---

