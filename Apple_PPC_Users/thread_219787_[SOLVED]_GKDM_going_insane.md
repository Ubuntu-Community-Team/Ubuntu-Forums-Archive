---
title: "[SOLVED] G/KDM going insane"
date: 2006-07-20
forum: Apple PPC Users
---

### Post by RavenOfOdin on 2006-07-20
The title says it all.

Neither of them will start up after boot, I get dumped to a console window, and when I try to restart them through /etc/init.d
the bootsplash screen comes up and gives me the message "Resetting usplash timeout" - then after that the little bar below the bootsplash
picture just sits there and doesn't move.  Neither DE has been able to start.

I've reinstalled both display environments clean from the archives, and run them separately.

(EDIT: dpkg-reconfigure of both kdm and xserver-xorg doesn't work either)

I would reinstall the entire system but thanks to certain people *cough* the 6.06 CD's don't work on my iMac 
and when I try to use any installers, give me "Cannot allocate initial device-tree chunk" when dumping me to 
an OpenFirmware prompt.

I've remained quiet up until recently, but I'm honestly getting tired of the problems.

---

### Post by iamhugeinjapan on 2006-07-21
G3 400 Powerbook Lombard with 256 RAM here.

I started to have this problem sometimes when i installed the kubuntu-desktop package over top of Ubuntu. It also happened with the Kubuntu desktop CD when booting that.

When I also put xubuntu-desktop over Kubuntu it happened everytime. For some reason it kept a kubuntu boot splash though. 

I was able to start a gui session by typing 'startx' in the console. It was never quite stable though.

In the end I downloaded the Xubuntu 'alternate' cd and installed clean that way. It's significantly faster and boots clean every time now. (and has the xubuntu boot splash of course).

---

