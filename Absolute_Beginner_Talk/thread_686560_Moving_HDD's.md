---
title: "Moving HDD's"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by DragoneyeIIVX on 2008-02-03
Just yesterday I bought my friends box from him, and am now trying to move my HD's in there. 
(One is a 160 that has a partition of linux and another of XP. The second HD is 40 and I use it as 'layover' space that both can access. A friend set that up for me, I have no idea how to do it on my own). 

I move my two HD's in and take his old one out, it went smoothly enough (although sometimes I wonder who designs these cases...), and try to boot it up. I get an error message that says - 
"bcm43xx_microcode2.fw not available or failed to load" - 
Or at least something very similar. 

I looked into it and it seemed like it was a wireless error. So I took the wireless card out of my old computer and replaced the new one with it. I go to boot up again and I get to this point - 
"Running local boot scripts (/etc/rc.local)                 [OK]" - 

I looked into that also and the only thing I could find was installation problems (which I'm not doing, just trying to get an existing Ubuntu Gutsy to run) and many people saying to press Enter to give it a little 'kickstart.' I tried the Enter key and nothing happened. 

Help? Many thanks in advance, huge new guy here.

---

### Post by ichbinesderelch on 2008-02-03
have you tried booting with the recovery mode option from the grub menu?

---

### Post by DragoneyeIIVX on 2008-02-03
Yup, I get - 
"root@name-desktop:~# 
The problem is I haven't a clue what I would (or should) do from there.

---

### Post by ichbinesderelch on 2008-02-03
try running gdm, look in /etc/rc4.d/ for gdm and just start it, and lets see what happens

---

### Post by DragoneyeIIVX on 2008-02-03
cd /etc/rc4.d/

A bunch of s(number)(variable) came up, one was S30gdm. 

Tried typing in 's30gdm' and nothing happened. How do I run it?

---

### Post by ichbinesderelch on 2008-02-03
"/etc/rc4.d/S30dm start" .. did you insert some new graphic card when in the new pc btw?

---

### Post by DragoneyeIIVX on 2008-02-03
The HD's are running into completely new Hardware (besides the wireless). I'll be having a splendid time with drivers once I get setup, I'm sure.  :) What concern do you have? 

- Typed in what you said - 
Starting GNOME display manager [OK]

then it just gives me my place again
root@name-desktop:/etc/rc4.d/#

---

### Post by ichbinesderelch on 2008-02-03
that you cant start the xserver cause of your xorg.conf using wrong drivers n stuff ;) but this should give you some error like "no screens found".. what graphic card is in it now?

try startx and look for the output

---

### Post by DragoneyeIIVX on 2008-02-03
Beneath a few things that said xorg. I ran into (EE) no devices detected. Is that what you're looking for? Although I may be blind with it, I didn't see anything that mentioned outputs specifically. 

Graphics card is a 8500 nvidia GE, if memory serves.

---

### Post by ichbinesderelch on 2008-02-03
not sure about that but i think you need to change xorg.conf, in section device there should be something like 

> Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
 EndSection

and 

> Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

did u use any nvidia card before? if not maybe trey nv driver instead of nvidia

---

### Post by DragoneyeIIVX on 2008-02-03
My other card was a nvidia, yeah. 
[[IMG]http://img174.imageshack.us/img174/5290/s7300161gc1.th.jpg[/IMG]](http://img174.imageshack.us/my.php?image=s7300161gc1.jpg)

That's what I'm seeing right now. How can I 'scroll up' with it? (*feels so noob...*)

---

### Post by ichbinesderelch on 2008-02-03
try running 'nvidia-xconfig', you should have this tool installed when used nvidia with ubuntu before.. this should write a new xorg.conf file which checks your card. than try to startx again, no need to scroll up there ;)

---

### Post by DragoneyeIIVX on 2008-02-03
It prompted me to 
apt-get install <selected package> - so I did. (apt-get install nvidia-xconfig)
It couldn't get all the files, so it prompted me to 'apt update ' - so I did. 

startx brings up the same screen as the one I posted.

---

### Post by ichbinesderelch on 2008-02-03
you installed and executed nvidia-xconfig, try starting ubuntu normal than without safe mode

---

### Post by DragoneyeIIVX on 2008-02-03
It gets to the same point, - 

"Running local boot scripts (/etc/rc.local) [OK]"

Then nothing. Dead halt.

---

### Post by ichbinesderelch on 2008-02-03
running out of ideas as i'm nooby myself ;) but i think all those new hardware kinda killed the configuration and i have no idea howto change that easily.. reinstalling the whole system will probably make everything allrite again, but maybe some other more expirienced user could help here ;)

---

### Post by DragoneyeIIVX on 2008-02-03
Thanks for all the help, nonetheless.

---

### Post by ichbinesderelch on 2008-02-04
if you still having the problem try "dpkg-reconfigure xserver-xorg" and reboot in normal mode!

---

