---
title: "yet another GRUB issue &lt;- will I ever learn?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Kulgan on 2007-01-03
hello again all...

I installed sabayon recently - on a new partition, of course... so I have ubuntu on hda1, sabayon on hda2 and some other junk in between.

now, this sabayon installer went and overwrote my mbr, and unlike ubuntu, had no respect in the least for other O/Ses. Or I might have done something wrong, but that's beside the point... The issue remains. 

Last time something like this happened, I went to /boot/grub/menu.lst and added the configuration that was missing, following the comments. This time, I copied it straight from the other installation - obviously, I can mount the ubuntu partition from sabayon - and copied the section. It contained:
```
title Ubuntu 6.06
root (hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot
```
That gave me a bunch of nonsense about a "file not found"... Error 15... 

After that, I went to the sabayon IRC, and was told to boot the live dvd and start the installer, and there was something to fix the grub list. It was there, but it gave me Error 13: Invalid or unsupported executable format. Yay.

The ubuntu section that was added by the grub "fixer" was:
```
rootnoverify(hd0,0)
chainloader +1
```

So, here I am with no ubuntu. And school starting :-| 

Might there be a typo somewhere? Something that needs to be changed becuase it's now got a non-buntu O/S in it? (however unlikely that would seem... :-? )

Thanks for ANY suggestions :D

-K

---

### Post by meng on 2007-01-03
What about
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Kulgan on 2007-01-03
bookmarked, PMed to self, booting livecd...

cheers.
-K

---

### Post by rsambuca on 2007-01-03
I had the same problem before when I loaded Sabayon 3.2.  Like you, I just copied stuff from the old ubuntu menu.lst and put it into the Sabayon menu.lst.  For some reason that I do not understand, it didn't work until I removed the savedefault and boot lines.

---

### Post by Kulgan on 2007-01-03
I'll try that as well, then. Good thing i hadn't started all ready :D

again, 
ta

-K

---

### Post by Kulgan on 2007-01-03
awesome. It worked! I'm in ubuntu now, with a gui that's actually sober. Thanks :D

---

