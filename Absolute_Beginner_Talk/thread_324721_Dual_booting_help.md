---
title: "Dual booting help"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by intimaAcE on 2006-12-24
Hey, last night I installed ubuntu onto a fresh new 250 GB hard drive.  I also have a 160 GB hard drive that I keep XP and all of my media on. Only thing is, when I installed ubuntu the old 160 GB hard drive had packed up, and I was trying to fix it using my laptop and an external HDD caddy.

So, getting to the point, ubuntu installed thinking it was the only OS that I would be using, and therefore didn't even offer me any dual boot options. Now when I had fixed my old hard drive and put it back in, it booted straight into Windows. So currently whenever I want to switch OS I have to go into the BIOS and alter the HDD boot priority. I have looked at a bunch of dual booting tutorials and I'm still in the dark as to how I go about setting up this dual boot. Any help would be greatly appreciated!

---

### Post by Sef on 2006-12-24
Read [Recovering Ubuntu]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after installing Windows.

---

### Post by intimaAcE on 2006-12-24
Blimey, that was quick! Thanks very much, I'll try that now. One more thing thats just occurred to me is that I would like a media partition so I can share music and pictures etc. between the two OS's. Am I right in saying that if I make a FAT32 partition on the ubuntu (250 GB) hard drive that both OS's will be able to read it?

Thanks again

---

### Post by Sef on 2006-12-24
> Am I right in saying that if I make a FAT32 partition on the ubuntu (250 GB) hard drive that both OS's will be able to read it?


Yes, but you could also make an ext2 or ext3 partition.   They are more stable than FAT32.  Ext2 and ext3 are the same except ext3 has journaling.  Read about [journaling]("http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/di8k-debian/node29.html").

---

### Post by intimaAcE on 2006-12-24
Yeah, but with FAT32 I don't have to muck around installing drivers for windows just to be able to read/write to it. Thanks for the advice by the way, don't think I'm not grateful for your help! 

What I'm gonna do is create a new FAT32 partition on the ubuntu HDD, copy all my music etc. over in Windows, then boot into ubuntu and set up GRUB using that link you gave me. Once thats all sorted do I need to mount the new FAT32 partition in ubuntu for it to recognise it? Or should it do it automatically?

---

### Post by gn2 on 2006-12-24
> **intimaAcE said:**
> 

So, getting to the point, ubuntu installed thinking it was the only OS that I would be using, and therefore didn't even offer me any dual boot options. Now when I had fixed my old hard drive and put it back in, it booted straight into Windows. So currently whenever I want to switch OS I have to go into the BIOS and alter the HDD boot priority. I have looked at a bunch of dual booting tutorials and I'm still in the dark as to how I go about setting up this dual boot. Any help would be greatly appreciated!

It is possible that you would have been able to select which OS to boot by pressing F8 (or whatever key depending on BIOS) to bring up a "Boot device Selection Menu" This has the benefit of keeping Grub off the Windows drive, and is a much simpler way of achieving a dual boot system.

If your hardware will support it I would recommend virtualisation with VMWare Server or Parallels instead of dual-booting which is a P.I.T.A.

---

