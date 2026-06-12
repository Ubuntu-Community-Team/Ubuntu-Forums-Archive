---
title: "Stability? Hmmm...."
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by spenny on 2006-09-25
OK, perhaps it's because I'm a complete beginner, but I've installed Ubuntu 6.06 on an AMD 1Ghz w/ 256Mb RAM, dual boot with Windows XP (XP on disk 1, Ubuntu on disk 2) and have had 2 system freezes in 3 days.

Not a good start.

The first freeze was with the screensaver (!). It had just stopped and there was nothing I could do to get out of it.

The second was just now using Google Earth. I was marking out a path and it just froze again.

Coming from an OS X background, I'm used to being able to force-quit the problematic application without compromising the other open apps nor the OS. Can this be done in Ubuntu? If so, how?

Has anyone else had problems with Google Earth? Or the screensaver for that matter? An even bigger question is, is it normal? I'd always thought Linux was very, very stable. I've had 2 more system freezes in 3 days than I've had in 4 years with OS X!

Any help, consoling, whatever, is much appreciated.

Andrew.

---

### Post by RobsterUK on 2006-09-25
I can't help you with the specific software mentioned, but if a program hangs, you can close it using system monitor:
System > Administration > System Monitor

You are right that if you close an application it shouldn't affect anything else.

hope this helps

---

### Post by xpod on 2006-09-25
> Any help, consoling, whatever

Dont worry:D 

Just joking mate.Had a few freezes myself recently but nothing a reboot...or 2 did`nt fix..
Not the sort of answer you mabey want but as i have found
"IF it does not compute.....you must reboot"

You can close sparate items in system monitor i think...:-k

---

### Post by spenny on 2006-09-25
> **RobsterUK said:**
> I can't help you with the specific software mentioned, but if a program hangs, you can close it using system monitor:
System > Administration > System Monitor

You are right that if you close an application it shouldn't affect anything else.

hope this helps

I can't even get control of the system menus! The cursor moves around fine, but clicking brings no response from anything.

---

### Post by srt4play on 2006-09-25
> **spenny said:**
> I can't even get control of the system menus! The cursor moves around fine, but clicking brings no response from anything.

What graphics card do you have?

---

### Post by spenny on 2006-09-25
> **xpod said:**
> Dont worry:D 

Just joking mate.Had a few freezes myself recently but nothing a reboot...or 2 did`nt fix..
Not the sort of answer you mabey want but as i have found
"IF it does not compute.....you must reboot"

You can close sparate items in system monitor i think...:-k


Sounds like the Windows way. ;-)

I wish I could bring up the system monitor in some way (Ctrl-Alt-Del, for instance?). 

I couldn't do anything. Nada. Let's hope it's just teething problems.

---

### Post by spenny on 2006-09-25
> **srt4play said:**
> What graphics card do you have?

An RV280 [Radeon 9200 SE]...ATI.

---

### Post by Old Pink on 2006-09-25
Hold "Alt" tap "F2" and type "xkill" in the box that appears. 

Press enter, and click the non responding application. ;)

--- 

As for CTRL + ALT + DEL, get automatix, and select that option. :)

---

### Post by srt4play on 2006-09-25
Are you using the proprietary ATI (fglrx) driver?

---

### Post by Brunellus on 2006-09-25
What happens if you hit CTRL + ALT + F1?  Does that get you to a text mode login?

---

### Post by srt4play on 2006-09-25
My guess is it's related to 3d acceleration (driver).  The only time I've had lockups was during 3d stuff (GL screensavers for example) when using the stock driver on a fresh install.  After installing the proprietary drivers (nvidia in my case) everything was fine.

---

### Post by bulldog on 2006-09-25
To say something too,and no offence,but your system spec's are not to say respectable.

I hope you made a swap.

I think you expect too much from your computer,it should run fine but if you open some apps and Google Earth it could be to much for your system.

I suggest to stick a liitle more RAM to it up to 1 GBor so,and I think it runs much smoother.

---

### Post by spenny on 2006-09-25
> **Matt.H said:**
> Hold "Alt" tap "F2" and type "xkill" in the box that appears. 

Press enter, and click the non responding application. ;)

--- 

As for CTRL + ALT + DEL, get automatix, and select that option. :)

OK, I'll have to try the alt-F2 + xkill next time. (If there is a next time).

I've already downloaded the Ctrl-Alt-Del option from Automatix.

---

### Post by spenny on 2006-09-25
> **Matt.H said:**
> Hold "Alt" tap "F2" and type "xkill" in the box that appears. 

Press enter, and click the non responding application. ;)

--- 

As for CTRL + ALT + DEL, get automatix, and select that option. :)

> **srt4play said:**
> Are you using the proprietary ATI (fglrx) driver?

Not sure. How can I check?

---

### Post by spenny on 2006-09-25
> **bulldog said:**
> To say something too,and no offence,but your system spec's are not to say respectable.

I hope you made a swap.

I think you expect too much from your computer,it should run fine but if you open some apps and Google Earth it could be to much for your system.

I suggest to stick a liitle more RAM to it up to 1 GBor so,and I think it runs much smoother.

No offence taken! You could be right, there. I am expecting too much of it, probably! It's a 4-5 year old box which I've used for Windoze apps I can't get for the Mac. It was about to go into storage when I discovered Linux and found a new lease of life for it.

I'll fiddle around with Google Earth again to see if I can replicate the freeze then try the suggestions posted here. If I can't get a solution, I'll just say my system is not up to spec and so not try to do the impossible.

Cheers,
Andrew.

---

### Post by spenny on 2006-09-25
> **srt4play said:**
> My guess is it's related to 3d acceleration (driver).  The only time I've had lockups was during 3d stuff (GL screensavers for example) when using the stock driver on a fresh install.  After installing the proprietary drivers (nvidia in my case) everything was fine.

Yeah, could be. It's what both events seem to have in common.

OK, how would I install the proprietary drivers?

Thanks.

---

### Post by srt4play on 2006-09-25
> **spenny said:**
> Yeah, could be. It's what both events seem to have in common.

OK, how would I install the proprietary drivers?

Thanks.

There are a few guides , for example here is one:

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

For others, search for "fglrx install" or similar.

I only have experience with nvidia, sorry I can't help specifically with the installation.

---

### Post by geezerone on 2006-09-27
Having lockup problems when screensaver runs or even just looking at screensaver options from system menu. I user ATI 9800pro and this is a new install with all updates applied.

---

### Post by thunderkyss on 2007-05-30
> **Old Pink said:**
> Hold "Alt" tap "F2" and type "xkill" in the box that appears. 

Press enter, and click the non responding application. ;)

--- 

As for CTRL + ALT + DEL, get automatix, and select that option. :)

this is not working for me guys... anything else I should try??

---

### Post by Acglaphotis on 2007-05-30
I've got xkill mapped to a shorcut if that happens... havent used it :P.

---

