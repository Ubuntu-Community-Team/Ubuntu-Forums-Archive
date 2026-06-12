---
title: "importing Vista .MIG file into Ubuntu"
date: 2011-08-25
forum: Any Other OS
---

### Post by michael2009 on 2011-08-25
I saved all my files and settings from Vista onto my USB stick using Easy Transfer, which created an .MIG file. Is it possible to access this from my Ubuntu OS? I had no success with Wine yet, by the way. I am running Ubuntu 10.10. 

My (big) problem is that I had planned to set up a dual boot system with Vista and Ubuntu, but I wanted to reinstall Vista first. Having partitioned my hard drive, my reinstallation disk failed to reinstall due to missing or corrupted files on the reinstallation CD. Bummer... So I installed Ubuntu anyway, but now I have no Vista OS and cannot restore my 300MB of files from the old Vista system. 

So that's why I need to find a way to restore these files. The easy transfer .MIG doesn't work with XP, so I can't retrieve them on my laptop running XP. Anyone got any ideas?

---

### Post by NightwishFan on 2011-08-25
Can you use the file command on the .mig file so we can see what type it is? (Might just be a cab file). Here is an example:
```
file '/home/jin/Documents/ISO/Debian/debian-31r1-i386-binary-1.iso' 
/home/jin/Documents/ISO/Debian/debian-31r1-i386-binary-1.iso: ISO 9660 CD-ROM filesystem data 'Debian 3.1 r1 i386 Bin-1       ' (bootable)
```

---

### Post by michael2009 on 2011-08-25
ok this is the command I got:

file '/home/muhsin/IMG00001.MIG'
/home/muhsin/IMG00001.MIG: data


So it's a data file... ?

---

### Post by NightwishFan on 2011-08-26
Yeah it doesn't know what it is. I guess it isnt a cab file. Sorry. :(

I do not know anything about windows so I guess just wait for someone who does.

---

### Post by michael2009 on 2011-08-26
That's OK :) Thanks for trying to be helpful anyway :)

---

### Post by michael2009 on 2011-08-26
Can anyone else offer any solutions to my problem?  ...please?

---

### Post by NightwishFan on 2011-08-26
Have you searched for any MIG recovery utilities? I am quite sure there will be none for Ubuntu so you may need to do so on a Windows machine.

---

