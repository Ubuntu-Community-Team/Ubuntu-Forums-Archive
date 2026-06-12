---
title: "Uninstalling Ubuntu"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by xangelo on 2007-09-20
Hey everyone, 
recently I found the need to uninstall ubuntu (yes it's actually necessary) and reinstall my old operating system Windows XP Pro. However, since my laptop came with an OEM license my copy is securely locked away in a 5GB partition on my harddrive. 

I've tried uninstalling Ubuntu but that just doesn't seem to work (GRUB Error 22), and the FIXMBR solution won't really be able to work for me since I don't have an actual cd. I'm just wondering how exactly I could go about this, as it's really slowing down my work. If someone could please help me out it would be great. 

I'm running on an IBM R60 (if that helps) and am using Ubuntu Feisty.

Thanks..

---

### Post by kellemes on 2007-09-20
You can get a copy of SuperGrubDisk (google) and restore GRUB so it will load Windows..
This works pretty fine.

Edit: For many more options see [http://www.users.bigpond.net.au/hermanzone/p18.htm]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by Pumalite on 2007-09-20
You can also get an OEM XP CD for ten bucks and use serial # stamped in your machine, but I think Super Grub is a great idea: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by xangelo on 2007-09-20
Thanks a lot, right as I posted that I actually found SGD and I burnt me a copy, I'm going yto try an restore the windows boot loader right now, wish me luck.

---

### Post by Pumalite on 2007-09-20
Good luck.

---

### Post by xangelo on 2007-09-20
Well. the SGD worked like a charm, I managed to get rid of GRUB and load on the XP boot loader as well as boot to the other partition where my OEM info is. XP is loaded and is installing the "factory default" information, I'm just going to wait till it's done before messing with it again. Thanks for all the quick replies!

---

