---
title: "Screen Saver - Lockout - Passwor Field won't get focus"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by adampyre on 2007-04-26
Hi,

I like having the lock out feature for my screen saver so no one will go on my computer and give me like a wallpapaer of rosanne barr in a swimsuit....... but when I click to disable the screen saver, the password box won't accept focus... can't get a cursor. I tried typing my password several times just in case it was there, just not showing feedback, but no dice.

I have a feeling this may be a Beryl setting issue. Anyone out there know a fix for this? THANKS!!!:guitar:


PS I should add that if I go to unlock it shortly (like a minute or two) after the screen saver loads it works fine, but if I let it sit for say 5 minutes or more...... problem\

PPS I am also noticing that only mouse clicks seem to turn off screen saver.. keyboard strokes do not... but the screensaver starts locking up when I hit the keybaord... I have a feeling the desktop has the foxus and things are opening up behind the screen saver.. and god knows what else i did....

PPPS The funny thing is is that ctrl+alt+backspace work as well... witch is kind of screwed up.... doesn't that pose a security risk in some way or at the very least a minor annoyance? I assume this is probably a reported bug....

PPPPS And finally after restarting X..... it lets me log in and starts loading gnome and beryl and locks up! yay.

---

### Post by adampyre on 2007-04-29
Bump

---

### Post by schlehmil on 2007-05-02
same problem for me. no idea to solve it.

---

### Post by adampyre on 2007-05-02
I figured out a fix: format the hard drive and reinstall windows xp. 

ok, so this is  a joke, but i am sad that ubuntu is not compatible with a lot of my equipment....... it runs better on a dell c610 laptop w a p III, 16 mb video card and 256MB of ram than it does on my desktop with a p4, 1 GB of ram and a 512MB video card....

---

### Post by starcraft.man on 2007-05-02
Sorry that no one responded to try and help for five days, someone usually catches old posts.

It seems to me you just had a bad set up with your drivers/beryl. Unfortunately you already reinstalled XP, if you are happy with that and really don't want to have to go through trouble with Ubuntu, maybe its best for you to stay with XP.

If you want to give it another try, I and I am sure others would be here to help.

All the best to you. :)

---

### Post by adampyre on 2007-05-02
I'm keeping XP on my desktop so I can get the "full" potential out of the hardware that I have. I am not saying Ubuntu cannot utilize it to it's fullest potential, but I am afraid that I am not going to be able to set Ubuntu up to be able to use my hard ware to its fullest potential... like I said, they funny this is that I installed Ubuntu onto an old pIII dell laptop and everything worked right away! Everything but the wireless card and ndiswrapper took care of that (i think, half the time i didn't know what i was doing, just blindly following directions) and suddenly it started working.

So, while I am using Ubuntu with my laptop, I don't think my desktop is quite ready to go Ubuntu only....my family, who are completely computer inept, didn't like the constant crashing and locking up... even firefox would crash! I never saw anything like it...... well, I did but that was with IE and XP..... :p

---

### Post by ulgor on 2007-07-08
I am having the same problem. No solution so far!

Every time I try to get back to work after closing the lid of my laptop or after it went to standby automatically, I get the usual "unlock" screen. The keyboard seems to be working, because I can navigate the buttons below the password text field. I just can´t focus the password field by clicking on it, even TAB-ing focus doesn´t work... So I can not login! I can go to switch user, but since I am the only user I always get back to the buggy unlock screen!!! The only way out of this is to reboot...

I am using Feisty with Beryl with ATI mobile graphics, I guess it´s a Beryl problem??

---

### Post by subdigit on 2007-07-25
I get the same issue when some program usually crashes beryl in the background while the screensaver is running.  For me, I sudo/log into a terminal  (ctrl-alt-F1) as root and do a "killall gnome-screensaver".  That will kill the screensaver and gets me back to the desktop (ctrl-alt-F7) which I typically find has crashed out of Beryl into Metacity.  Don't have a real solution for how to stop it from crashing though...

---

### Post by mihail on 2007-08-10
I have this same problem as well, and I have managed to find out at least some sort of source of this problem: gnome-settings-manager & Beryl.

Just like one week ago, I installed Beryl and it was functioning otherwise perfectly, but Gnome Theme icons (and couple of other Theme related settings) didn't show up correctly. I find this:
[http://ubuntuforums.org/archive/index.php/t-379696.html](http://ubuntuforums.org/archive/index.php/t-379696.html)

So... I added gnome-settings-daemon to System->Sessions. This fixed the Gnome theme related issue when running Beryl, but my screensaver stopped functioning: when screensaver activated, I was unable to enter my password (no focus). I tried to stop gnome-settings-daemon and screensaver started to work again.

Also: when gnome-settings-daemon is running with Beryl, my laptop's GPU overheats REALLY easily (over 105C!) ...but this is totally separate issue...

---

### Post by sr4794 on 2008-01-16
See my post at... [http://ubuntuforums.org/showthread.php?t=533159](http://ubuntuforums.org/showthread.php?t=533159)

It should work

---

