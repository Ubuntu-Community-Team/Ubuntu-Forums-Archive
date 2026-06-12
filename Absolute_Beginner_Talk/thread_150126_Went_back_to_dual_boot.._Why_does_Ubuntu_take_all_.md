---
title: "Went back to dual boot.. Why does Ubuntu take all available space?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by Danny Boy on 2006-03-25
This was my third time installing Ubuntu with a dual boot setup. I decided to put Windows back on my my machine because I cannot get the file print sharing to work in Ubuntu, so I figured even if I boot into Windows only to have other people print/grab files that would be enough. 

I have an 80 GB hard drive, after I install Windows and my nessecary apps/docs I'm using about 10 GB. 

When I install Ubuntu, I tell it to take 25% of available free space which should be roughly 20 GB if you include the swap. After the install is done and I boot into Ubuntu it tells me the file system has 50 GB available, then I boot back into Windows do double check and Win only has 20 GB on it's partition. 

I know I'm not messing up because it happened the first two times I installed it. This time I just let Windows format again and haven't installed Ubuntu because I don't want Ubuntu take most of my HD space. 

Is this a known bug with the installer? Am I doing something wrong?

Thanks in advance, 

Dan

---

### Post by aysiu on 2006-03-25
I don't know if this is a bug, but you're welcome to [file a bug report on it.](https://launchpad.net/malone)

If you manually edit the partition table instead of asking Ubuntu to take up the free space, you have more control over how much space it uses.

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) should help you with that.

---

### Post by taurus on 2006-03-25
No, there is no bug with the installer.  If you want Ubuntu to use 20GB of your harddrive, why don't you make two partitions when you install XP.  Have XP install on the first partition and when you install Ubuntu, tell it to use the second partition instead of telling Ubuntu to use 25% of the space!!!

---

### Post by John.Michael.Kane on 2006-03-25
This may help you get the linux print file sharing up and going if you still want to try.
[http://www.linuxheadquarters.com/howto/networking/samba.shtml](http://www.linuxheadquarters.com/howto/networking/samba.shtml)
[http://www.tldp.org/HOWTO/SMB-HOWTO-9.html](http://www.tldp.org/HOWTO/SMB-HOWTO-9.html)
[http://www.aboutdebian.com/lan.htm](http://www.aboutdebian.com/lan.htm)
[http://www.tldp.org/HOWTO/Networking-Overview-HOWTO-5.html](http://www.tldp.org/HOWTO/Networking-Overview-HOWTO-5.html)
[http://users.pandora.be/sim/linux/samba.htm](http://users.pandora.be/sim/linux/samba.htm)

---

