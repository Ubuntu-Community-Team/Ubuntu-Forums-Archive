---
title: "OS X wants to format my ubuntu"
date: 2009-10-06
forum: Apple Hardware Users
---

### Post by X5-655 on 2009-10-06
I installed a second hard drive into my Mac Pro, and installed Ubuntu on that.  Worked great.

However, everytime I boot into OS X, it wants to format my ubuntu HD, saying it's not readable.

I tried asking the apple forums, got nothing.

Is there any way to prevent this?  I tried installing MacFuse with an ext plugin, no dice.  Still asks upon every boot about formatting my ubuntu HD.

---

### Post by hantechbl on 2009-10-06
I'm not a Mac user but if you can find something about your hdd's and try to get the os not to look at that drive.  The reason why it's not reading it is because there is no driver integrated into the os for that File system.

---

### Post by bug67 on 2009-10-08
I know this isn't gonna help but, I just hit "ignore" and continue on about my business.  I've also noticed that if I don't do anything, the pop-up window goes away on its own after awhile.

It would be nice if OS X could see my Ubuntu drive and recognize it as a readable drive though.  So, if anyone has a solution, I'm all ears.  :)

---

### Post by fela on 2009-10-08
All you need is a driver for OSX that reads the filesystem that Ubuntu is installed on, whichever that may be (default is ext3 in all versions up to karmic, in karmic the default is ext4).

---

