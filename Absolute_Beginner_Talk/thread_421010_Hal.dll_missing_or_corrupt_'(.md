---
title: "Hal.dll missing or corrupt :'("
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Smashed_187 on 2007-04-24
I have the fabled hal.dll missing error upon trying to boot XP from GRUB. I checked System32, and the file's there.

I had Windows XP installed on a 80GB partition on the harddrive, then I installed Ubuntu 7.04 onto the remaining 40GB.  Got Ubuntu updated, running and in a nutshell: Perfect.

Unfortunately the rest of my family's PC knowledge amounts to that of your common eggplant so they're all comfortable with XP rather than Ubuntu (Regardless that all they have to do is double click the shortcuts I painstakingly set up with wine for their common Windows Apps).

Now, I know of a few ways to fix this, which all involve booting off the XP disc and repairing the MBR. I don't want to do this because I don't want to kill my Ubuntu build and I'm not knowledgable enough to spend time fiddling and making GRUB work again.

Is there a simple way to fix this, without messing up the GRUB bootloader?

Cheers.

---

### Post by lassegs on 2007-04-24
I dunno. It isnt that hard to reinstall GRUB if you dont find any other option than to let the windows CD "fix" the MBR.

---

### Post by slayerboy on 2007-04-24
have a look [here]("http://www.kellys-korner-xp.com/xp_haldll_missing.htm") ( [http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm) ), [here]("http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm") ( [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm) ), and [here]("http://www.computerhope.com/issues/ch000490.htm") ( [http://www.computerhope.com/issues/ch000490.htm](http://www.computerhope.com/issues/ch000490.htm) ) and see if it helps.  This is one of those errors in XP that I HATED with a passion because it was so hard to diagnose.  I usually gave up and reformatted and it all worked, hopefully you won't have to do that.

Just a quick reminder, not just for you, but for anyone really....Google is your friend.  I found all three of the above resources in my search for "[XP missing hal.dll]("http://www.google.com/search?q=xp+missing+hal.dll")" in the first three results!:KS

---

### Post by ukripper on 2007-06-06
I had the same problem. Error message you get is very misleading it should be boot.ini not hal.dll but anyhow, I have resolved it by following steps:

1. Boot into XP Cd.
2. Go to recovery
3. Recovery console type: **bootcfg /rebuild**  and then press enter
4. The first prompt asks Add installation to boot list? (Yes/No/All )  Type **Y** press enter
5. Enter Load Identifier:: Windows XP press enter
6. Enter OS Load options:.
Type** /Fastdetec**t  and press Enter. 
7. Exit and reboot.

Hope it works for you as well.

---

