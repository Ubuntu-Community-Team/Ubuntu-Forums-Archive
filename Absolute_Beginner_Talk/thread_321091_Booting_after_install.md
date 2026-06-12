---
title: "Booting after install"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by percyr on 2006-12-18
I have installed a 80 gig slave harddrive exclusively for my Ubuntu 6.10 install.  The Ubuntu installation went well, however I am unable to boot into Ubuntu.  Windows XP loads OK when selected, but when I select Ubuntu, all I get is a blinking cursor up near the top left hand corner of my screen - and it just continues to blink forever.  No messages - nothing.  

Can any one help please

---

### Post by taurus on 2006-12-18
Sounds like Ubuntu is having a small technical difficulty with your graphic card!  Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

p.s.  what graphic/video card do you have anyway?

---

### Post by percyr on 2006-12-18
I have an Intel mobo with an Intel 82845 Graphics Controller, if that is any help.

I am new to Linux, although I have been around computers since the DOS days, so I know a bit about command lines, etc.

The code you quoted above, is that just typed at the command prompt after booting into recovery mode?

I also failed tomention in my other post that the slave is a new Seagate 80 gig drive.  After I installed it, I can see it in the BIOS, and also in the XP Device Manager, but it does not appear in Explorer or My Computer.  Does that mean anything?

---

### Post by taurus on 2006-12-18
Wait for it to finish booting into recovery mode and at the prompt, type those two commands to see if you get your GUI login screen.

---

### Post by percyr on 2006-12-18
Tried that, but it came back and said:

"xservice-xorg is not installed"

---

### Post by percyr on 2006-12-18
Problem solved - I had been trying to install version 6.10 from a magazine cover disk, but then dug up a previous disk with version 6.06 - no problems.

Perhaps there was a problem with the original magazine disk.

Thanks Taurus for your help - I hope to get on top of Linux.

---

