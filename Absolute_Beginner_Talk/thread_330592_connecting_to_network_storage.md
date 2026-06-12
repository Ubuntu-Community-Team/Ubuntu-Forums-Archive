---
title: "connecting to network storage"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Ba66e77 on 2007-01-03
Alright, I'm new to linux and know drek about networking, but...

I have a Buffalo LinkStation ([http://www.buffalotech.com/products/network-storage/linkstation/linkstation-pro/](http://www.buffalotech.com/products/network-storage/linkstation/linkstation-pro/)) connected to my Ubuntu 6.10 desktop vi cabled connection through a router.  

Now, under WinXP, it was basically plug-and-play.  I plugged the drive in, Windows found it, and I didn't have to do much besides map a drive letter to it.  

Ubuntu, though, isn't being so helpful.  It finds the workgroup in the network places, but says it can't display it.  I trolled the posts on similar issues, but frankly, they're over my head.  Can anyone walk me through getting things setup?

---

### Post by kebes on 2007-01-03
I would try making a network connection directly to it (instead of trying to search for it on the network).

So open Nautilus, and go "File > Connect to Server..." then fill in the proper information. Your hardware appears to support SMB (Windows Share) and FTP. There is a way to make this permanent, so it's just an icon you click on and the connection opens up.

Does that work? (My apologies if this is exactly what you've already tried... if it is, have you tried both SMB and FTP?)

---

### Post by palladium on 2007-01-11
I also have a LinkStation Pro connected to a laptop running Ubuntu 6.10. I can access it through Nautilus by clicking Go > Location > Location=smb://192.168.0.200 (which is the IP of my LinkStation). 

I can drag and drop files from the laptop to the LinkStation. My problem is that the connection is very very slow. It took 411 seconds to copy a 2.1Mb file. This was 5 times slower than it took to download the file from the Internet to the laptop using exactly the same router, cables etc just moments before. If I copy the same file to the LinkStation from a Windows machine it appears to copy instantaneously. 

I have tried the suggestions by "aleska" ([http://www.ubuntuforums.org/showthread.php?t=213824&page=2](http://www.ubuntuforums.org/showthread.php?t=213824&page=2)) to mount the drive but have not succeeded in getting this to work. 

Can anyone suggest how to speed up the connection between Ubuntu and the LinkStation?

---

### Post by palladium on 2007-01-15
> **palladium said:**
> I have tried the suggestions by "aleska" ([http://www.ubuntuforums.org/showthread.php?t=213824&page=2](http://www.ubuntuforums.org/showthread.php?t=213824&page=2)) to mount the drive but have not succeeded in getting this to work. 

Can anyone suggest how to speed up the connection between Ubuntu and the LinkStation?

I have resolved my problem. I had not realised that smbfs was not already installed. Now I can mount the drive. 

I was able to speed up the connection by disabling PCI Express Link ASPM in the BIOS of the laptop or using another computer.

---

