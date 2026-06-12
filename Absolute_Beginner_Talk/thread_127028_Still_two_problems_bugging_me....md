---
title: "Still two problems bugging me..."
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by sniffass on 2006-02-08
Kubuntu system is running nicely and I've eliminated most of the concerns with the excellent help from this forum - so I want to say a BIG thank you too all of the community and especially the people directly assisting me!

right,
1 - I can now mount my external lacie usb drive (it is ntfs) but when I try to access it says I don't have permission which is a bit of a bugger 'cos i bought it. The entry for it in fstab has the same settings for user privelages as my usb flashdrive (which is fat32 formatted). What must I change to get permission on it?

2 - This is really annoying - no matter whether I use ubuntu or kubuntu 5.1 the volume control on the desktop has absolutely no effect. The volume control in media playing application is also similarly useless. The only thing that seems to alter volume is to open up the mixer and control the pcm volume.
Actually while i'm about it I want to mention SuSe 10 has the same problem too, and SuSe 9.3 can't even use my sound.
I'm using a Sony Vaio FS115E but i don't really have a clue what sound system is has. I'm guessing some Intel trash. Can I fix thid and is it also possible to use the Fn keys to control volume/screen brightness in kubuntu?

Thanks again people, the forums and help is what makes ubuntu choice OS for me.

---

### Post by gord on 2006-02-08
ntfs filesystems are barly supported in linux, you can read but not write, i would suggest formating it to fat32 if you can. 

im not sure about the audio problem but it might be the interface to the sound card that is the problem, (oss, alsa that lot). but like i said im not sure

---

### Post by yabbadabbadont on 2006-02-08
I don't have a suggestion for problem 2, but to fix 1 just add the uid, gid, and umask options to fstab.

If you only have one user on the machine, then add uid=1000,gid=1000,umask=0222 to the existing options in your fstab for your ntfs partition(s).  Another possibly useful option is nls=utf8.  It lets filenames with international characters be displayed properly.

---

