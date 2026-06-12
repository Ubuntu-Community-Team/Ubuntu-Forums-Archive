---
title: "running both xp and ubuntu"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by chang3andrew on 2008-02-22
Can anyone give me any advice as to how to partition my hard drive so I can run both Ubuntu AND XP... like when it boots it will give me an option to run one or the other? I like ubuntu and I think it's simpler to use it for wireless/internet, but for other kinds of stuff I kind of need to use XP..

I tried to partition it one time and I ended up formatting the whole drive... drove me nuts to see so much data lost. ARRGH

Anyways, Give me some tips! I love tips.

---

### Post by S15_88 on 2008-02-22
Yes you will get what is called GRUB it's a list that shows all available OS's.  I installed XP then partitioned my drive then installed ubuntu and it's worked great for me!  there's plenty of tutorials out there on how to partition
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy")

Thanks, ALain

---

### Post by suibhne on 2008-02-22
Have you tried using gparted?

burn a disc-partition your machine-install your proprietary system first, then ubuntu, then you're flying-you'll get a list of options when you reboot your machine concerning which OS you want

 [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by S15_88 on 2008-02-22
if you're going to burn gparted i suggest getting super grub, it's got grub stuff and gparted on it.  very handy to have

Thanks, ALain

---

### Post by chang3andrew on 2008-02-22
Well the problem is I already have XP installed... and right now I'm at the disk partitioner in the installer for Ubuntu

I have tried to use "sda 5" which is my D Drive from where I store my personal files. But it kept saying "no root file is defined"

What does it mean and what do I do to be able to use it?

---

### Post by Duck2006 on 2008-02-22
This may help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by chang3andrew on 2008-02-22
thanks that helped

I now have super grub... one question. do I have to use the CD every time I want to change which os I want to boot?

---

### Post by Duck2006 on 2008-02-22
No you should be able to repair your grub from the disk so you don't have to use it every time you boot.

---

### Post by jbaerbock on 2008-02-22
Basically install WinXP first on your full HD. Then when ready go into the Ubuntu LiveCD and use GParted to reduce your WinXP partition to whatever size you want for it (the resulting empty space will be Ubuntu space). Once that is done run the installer on the LiveCD and select "Use largest continiuous free space" and it will install and partition for you the free space winXP is no longer using. Then when you reboot GRUB will give you the option to boot to one or the other, simple as pie.

---

