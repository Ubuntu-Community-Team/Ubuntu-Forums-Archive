---
title: "Please Help, &quot;Missing Operating Systm&quot; error"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by marcosg on 2007-09-29
Hello, I'm very new to linux and eager to learn. 

Recently I tried installing Ubuntu on my computer using a live cd. When it was done installing it asked me to restart which I did and now when I turn my computer on it says "missing operating system." 

What do I do to make this work? My BIOS is up to date, I have two hard drives, neither of which have windows on them, with a pentium III processor with 768 MB of RAM?

Thank you for your help!:)

---

### Post by arochester on 2007-09-29
When you use a Live-CD the boot order needs to be CD-Rom first. After you install the boot order should be Hard Drive first. Have you changed the BIOS back?

---

### Post by bigken on 2007-09-29
you also boot from the live cd again and use gparted to check your hdd has a bootable flag

---

### Post by wormser on 2007-09-29
I think the problem is with Grub.  You probably installed it somewhere besides the MBR.  The first 2 posts in this [thread]("http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub") have guides on how to fix Grub.

---

### Post by marcosg on 2007-09-29
Thank you, everyone! 

It worked, however now I get another error now, "Error 17"? I looked it up on some of the other posts and it said that the grub might not be installed? So I opened up a terminal window and typed in grub which took me to the grub program? I'm not sure what to change exactly or even if the problem is here. Thank you again everyone you guys are a big help.

---

