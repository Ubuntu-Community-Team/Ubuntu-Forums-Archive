---
title: "No Screen @ Startup"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-11-20
lright fresh install of ubuntu , installed nvidia restricted drivers, at reboot I have no screen at the startup, my monitor states taht I have an unsupported mode, I cant go any further. Any ideas? Thanks

---

### Post by tzulberti on 2007-11-20
Go to a terminal and run "sudo dpkg-reconfigure xserver-xorg". After a few steps you would be able to configure the resolution of you monitor...

After that, run "sudo /etc/init.d/gdm restart"

---

### Post by NthgToFear on 2007-11-20
> **prodigalson666 said:**
> lright fresh install of ubuntu , installed nvidia restricted drivers, at reboot I have no screen at the startup, my monitor states taht I have an unsupported mode, I cant go any further. Any ideas? Thanks

My install does that too. Although eventually it comes up. I think it has something to do with having a widescreen monitor.

---

### Post by prodigalson666 on 2007-11-22
thanks, reconfigure did the trick, everything is fine now. cheers

---

