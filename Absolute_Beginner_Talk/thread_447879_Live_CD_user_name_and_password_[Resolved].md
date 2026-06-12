---
title: "Live CD user name and password [Resolved]"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by nowawakened on 2007-05-18
Hello,

I am a beginner user of Ubuntu and Linux in general. I downloaded the desktop edition of Ubuntu 7.04 and after burning the CD, attempted to boot using the CD. However, when the machine boots up in Ubuntu, I get prompted for a user name and password. Of course, I did not create any users yet. I tried several different combinations that struck to me as obvious but nothing seems to work.

Here are some combinations I have tried:

Username Password
Ubuntu     Ubuntu
root          Ubuntu
root         <blank>
Ubuntu    <blank>
ubuntu     ubuntu
ubuntu    <blank>
sudo        password

and so on and so forth. 

Any help will be appreciated.

Thanks in advance.

---

### Post by homergreg on 2007-05-18
Does this do this every time you boot off the Live CD?  It asked for a password one time on me, and I was in the same boat as you, I tried all the obvious ones, then I just tried rebooting, and the CD came up normally, no password.  The live CD should boot right into the desktop.  Does this do this every boot?

---

### Post by starcraft.man on 2007-05-18
Sounds like a flakey CD. It should boot straight past the log in screen. If reboot doesn't work, follow this [guide]("https://help.ubuntu.com/community/BurningIsoHowto") and check the md5 sums at every step. If it continues to persist for some unknown reason, use the alternate installer, it requires no live boot at all.

---

### Post by nowawakened on 2007-05-18
Hi homergreg,

Well I tried booting 3 times and every time I do so, I get prompted for a user name and password.

---

### Post by starcraft.man on 2007-05-18
> **nowawakened said:**
> Hi homergreg,

Well I tried booting 3 times and every time I do so, I get prompted for a user name and password.

That definitely must be a bad burn... try again, and redownload the ISO, and be sure to check its hash upon download then again upon burn as detailed in the link.

---

### Post by nowawakened on 2007-05-18
Ok, I will re-download the iso, burn a new CD make sure its md5 matches up and let you all know what happened. Thanks.

---

### Post by fastpakr on 2007-05-18
Make sure you burn at a slow rate, i.e. 4x or 8x.

---

### Post by nowawakened on 2007-05-20
Hi all,

Thanks a lot for all of the replies. As suggested by many, I redownloaded and burnt the disk making sure the md5 matched and burnt it at a slow speed 10x. That seemed to do the trick. This post is being written from Ubuntu live CD. Wireless, sound, everything works great!

Thanks again for your help

---

### Post by starcraft.man on 2007-05-20
> **nowawakened said:**
> Hi all,

Thanks a lot for all of the replies. As suggested by many, I redownloaded and burnt the disk making sure the md5 matched and burnt it at a slow speed 10x. That seemed to do the trick. This post is being written from Ubuntu live CD. Wireless, sound, everything works great!

Thanks again for your help

No problem man, you are most welcome.

Have fun with Ubuntu, its not hard, you can do anything you want and then some :p

---

