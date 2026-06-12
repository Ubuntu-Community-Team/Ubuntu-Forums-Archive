---
title: "installed kernel 5.10 ppc"
date: 2006-10-28
forum: Apple PPC Users
---

### Post by kansaibear on 2006-10-28
1. Could someone explain why the kernel needs to be copied to the os9 volume for bootx to use? I installed debian and it was unnecessary on that distro. What is different in Ubuntu?

2. I couldnt successfully copy the installed kernel to OS9 volume on install from the terminal before rebooting. Any good ideas on how to get the kernel out of the ubuntu volume now?

Thanks for putting up with us noobies, Barry

---

### Post by abtabt on 2006-10-28
1. why ??? if you install yld 3,0  you have two diffrent kernel one for install and one for boot i dont now how it will be in debian ??
but 5.10 dont support old world but you can get it working on a old world

but you must do the copy of the kernel and the image in the boot folder and get it to the mac side (system folder) and in the bootex folder 

if you have g3 and a lot of memory you can use ubuntu but if you dont have it 
use ubuntulite or xubuntu

2. if you have the live cd you can use that or do a  reinstall 
i hope that you have read OLD WOLD WIKI if not read it

---

### Post by HaroldJohnson on 2006-10-29
If you were using BootX to install Debian, then you *must* have placed your kernel on your OS 9 partition (where BootX also resides).  BootX is simply an application which -- once installed on Mac OS 9 -- allows your OldWorld Mac to boot into (and install) linux.  ("OldWorld" is a term applied to a particular generation of Macs, including many of the early PowerBook G3 systems; "NewWorld" is applied to a more recent generation.  I don't believe NewWorld Macs require BootX, though they may require another type of boot application, like yaboot or something.)

---

### Post by kansaibear on 2006-10-29
I see that I could have used a little better english.. been in Japan to long I suppose. The issue is why do I have to use the ACTUAL installed kernel copied back to bootx. Of course bootx requires a kernel but with debian, the kernel used in the install boot can be left. With ubuntu, I have to copy the ACTUAl istalled kernel back to bootx and REPLACE the kernel or it wont boot. That is different than with debian apparently as debian booted up after install with the same kernel. I was hoping someone could tell me why.

I did have ubuntu installed before but killed it a while back to clean install everything.

And I was hoping that someone could give me a way to get that kernel off the ubuntu volume (ext3) to the os9 or osX volumes (hfs+)

---

### Post by HaroldJohnson on 2006-10-29
Thanks for clarifying -- I really wish I knew the answer to this, too, because I find myself copying my kernel (the file "vmlinux") and its accompanying initrd.img file to my OS 9 partition quite often (changing the name of the initrd.img file to "ramdisk.image.gz", of course) and I'm also not certain why I have to do this -- or even if I have to do this at all!

I'm "playing it safe", however, copying the new kernel and initrd.img files over to OS 9 after any major change I make to my Ubuntu system.  You see, I copy these files over to OS 9's System Folder each and every time I apply an 'apt-get dist-upgrade' -- and sometimes, after a simple 'apt-get upgrade' -- again, just to play it safe.  The reason?  Because I'm thinking the kernel is altered/replaced each time I apply these commands, and I'm also thinking it's necessary to move the new kernel (and the initrd.img file) to the OS 9 partition so that I'll be able to boot into my altered Ubuntu system again after these changes.

Yet I'm not certain I really need to copy these files over to my OS 9 partition after each 'apt-get dist-upgrade' or 'apt-get upgrade' command I apply; I'm simply doing it to be extra cautious.  I really wish I knew whether or not it's necessary for me to be doing this each time I upgrade my system.  Do I really need to move these files after applying an 'apt-get dist-upgrade'?  Or can I use the previous kernel after running this?

In any case, I hope someone else can help answer your question(s), as the answer will likely help me out, too.

---

