---
title: "Intermittant boot problems-Feisty"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by anishd on 2007-05-24
Hello friends,
Thank you in showing interest in my problem...let me explain it..
I have a Pentium IV computer with 512 MB ram. I dual boot ubuntu with Win XP.
I was using Dapper drake and it was working fine...last week i obtained one copy of feisty and done a clean install of it after formatting the dapper.
but the problem is that it does not boot up correctly sometimes. If i am booting in feisty, it opens correctly only once in two times. What happens is that, after showing the boot screen (written ubuntu and a progress bar progressing...this is more beautiful in feisty when compared to dapper. i mean in full resolution), the screen goes blank. the mouse or keyboard does not work. ctrl-alt-backspace does not work. sometimes i can hear the startup sound, sometimes not. sometimes it boots up correctly and asks for the login. if i boot it in second option in the GRUB menu (root/administrator mode), it boots correctly. I have formatted and reinstalled the feisty three times, but of no use. dont know what to do..please help me.

One more problem...if it is of some connection with screen resolution. My monitor is a samsung syncmaster 793s (17"). while booting from hard disk or live cd, the ubuntu opens in 1280x1024 pixals (60 refresh rate). the other resolutions possible below are 1024x768 and 800x600. 1024x768 is too big for me whereas 1280x1024 is too small to see. i use windows xp in 1152x864 which is comfortable to me. i am not able to use this resolution as it is not listed in the available screen resolutions in the menu (however, it is listed as one of the resolutions in the xorg.conf file). i know that ubuntu has problems with screen resolutions...but would like to use it. dapper had same resolution problem..however, this boot problem was not there..should i revert myself to dapper.
plese help me..if any body knows what is the problem.

---

### Post by ggaaron on 2007-05-24
What is your video card?

---

### Post by Adramelech on 2007-05-24
Try looking into your logs to see if there is any problem reported.
Log can be found on /var/log , look for dmesg and X.org logs

---

