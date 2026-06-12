---
title: "Grub menu item missing?"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-05-06
Hi all! Yesterday 05/05/06 i updated the PC with new updates(67) and rebooted.
It was then I noticed that the Mepis boot details were missing (dual boot system). I have since re-added the boot details to the menu list and all is ok! Would the updates have caused the boot detaills to change. or could there  have been another reason?:-k

---

### Post by dermotti on 2006-05-06
If the updates included a new kernel, it will rewrite the menu.lst to add the kernel

---

### Post by Sbarton on 2006-05-06
[QUOTE=dermotti]If the updates included a new kernel, it will rewrite the menu.lst to add the kernel[/QUOTE]

Ah! There was a new kernel added! So it was the updates? I suppose then that the Mepis entry will have to be added each time a kernel update takes place, is this so? Pity the update doesn't just re-write the Ubuntu part and leave the other existing entries.
Thanks

---

### Post by dermotti on 2006-05-06
You can put your custom grub entries under this line in you menu.lst

### END DEBIAN AUTOMAGIC KERNELS LIST

and they should not be overwritten.

---

### Post by Sbarton on 2006-05-06
[QUOTE=dermotti]You can put your custom grub entries under this line in you menu.lst

### END DEBIAN AUTOMAGIC KERNELS LIST

and they should not be overwritten.[/QUOTE]

Ok! Thanks for that dermotti!:)

---

### Post by fabtep on 2006-05-06
Umm, thats bad :-( 

I had cut my WinXP entry recently and pasted it to the top, because I still want it to be the automatic boot option (sorry guys), so now its gone and unfortunately there's no old version of the list in the backup file either. 

My Windows partitions C and D (both NTFS) are on /dev/hda1 and /dev/hda2, while ubuntu's ext3 is on /dev/hda5 and the swap on /dev/hda5. As there's only one hard disk my device map has just the entry "(hd0)	/dev/hda" and the menu.lst boots all ubuntu options from hd0,2.

Before I try anything harmfully wrong, can anybody please tell me what the XP entry is supposed to look like? And is there any better solution for future kernel updates than having a backup file with the default boot order and always restoring it before updating?

Thanks in advance,

Fabian

(p.s. I chose this thread because it seems to be the most recent one that already focusses on my problem. I did not consciously choose this subforum.)

---

### Post by confused57 on 2006-05-06
You might want to put your windows GRUB entry above the line:

###BEGIN AUTOMAGIC KERNEL LIST

and leave the default  0

That's what I've done, dual booting 2 hd's with Ubuntu master, Windows slave; but should work whether dual booting from a single hd or windows master, Ubuntu slave.

---

### Post by fabtep on 2006-05-06
Hmm, I thought I had done that last time, but I might be wrong there. However I had not thought about the "default" value so far, so I'll try that one first. Thanks a lot!

There's still my question of how the Win XP boot option should look like, though. It would probably contain root (hd0,0) or (hd0,1) (which one?) at the beginning and boot at the end. But which entrys should it have between those two?

EDIT: I just saw the example and I'll have a go at that one. I suppose I was wrong about having put the entry above the beginning line indeed. ;-)

---

### Post by confused57 on 2006-05-06
I'm definitely not an expert using Grub(editing menu.lst), see if this thread can answer your question:


[http://www.ubuntuforums.org/showthread.php?t=161950&highlight=dual+boot](http://www.ubuntuforums.org/showthread.php?t=161950&highlight=dual+boot)

---

### Post by fabtep on 2006-05-06
I used the example included in the menu.lst and it worked just fine, thanks again :)

---

