---
title: "Gutsy on a MacPro 8 core?"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by mert on 2007-10-18
I just read a few posts where people are saying they've installed Gusty on their 8 core MacPro boxes.  I was thinking of installing it on my MacPro at work once its officially released.  How did you do the install? I have an unused hard disk that I can use for Gutsy so I don't think I need Bootcamp.  Can I just install rEFIt and then follow the documentation for a [macbook install]("https://help.ubuntu.com/community/MacBook")? The volume that Mac OS is on is set up with mirrored RAID using two other drives in the machine.  Anyone know if that will cause problems?
Cheers

---

### Post by jamieno10 on 2007-10-20
Hi,

I have a mac pro with 4 HDD and I did the following:

1. formatted everything on all 4 HDD

2. installed Mac OS X to one HDD

3. partitioned the other 3 HDD freespace or MS-DOS

4. installed rEFIt in Mac OS

5. Installed ubuntu to one HDD using 'guided' option, making sure the GRUB installed to that HDD.

6. I found that - for me at least - if I partitioned anything in ubuntu (during or after the installation), I can't boot it up. Hence, I made sure that everything is set-up during the Mac OS installation.

I'm not sure if the RAID setup will affect booting ubuntu up, but in principle, it shouldn't. I can't really comment on that though since I have not tried this setup.

Hope it helps.

If you don't mind, please report back the results; it would be good to know if ubuntu installs/boots up well with the raid set-up.

---

### Post by nikitavfx on 2007-10-24
Hey mert,

here are some howtos I've written concerning the Mac Pro: [http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/)

Cheers

---

