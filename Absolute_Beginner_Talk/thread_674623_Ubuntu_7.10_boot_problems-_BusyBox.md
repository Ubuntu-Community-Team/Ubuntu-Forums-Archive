---
title: "Ubuntu 7.10 boot problems- BusyBox"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by darkcodemonkey on 2008-01-21
I'm a very BIG fan of Ubuntu, but have a dreadful problem.
When I turn on my machine, the Ubuntu logo shows with the loading bar below. It acts as if it will load fine, but suddenly switches to a black and white screen which shows:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I personally don't want to mess with this without info on how to fix it.

Note: before I shut down the computer the last time, I couldn't access anything on my computer when clicked. I eventually took a look at it with the LiveCD and found that it was set to just list files

Please Help me!!!

Thanks to any who reply.

---

### Post by bodymind on 2008-01-21
i think ubuntu can't find any harddisk on your computer

---

### Post by darkcodemonkey on 2008-01-21
Could you explain a little more...
Atleast in a way I can fix this

---

### Post by nkoi on 2008-01-21
i have the same problem. what happens is i insert the CD, it brings me to the nice menu shown here
[img]http://debianadmin.com/copper/albums/kubuntu/thumb_1.png[/img]
then the bar bounces back and forth a few times, and boom. busybox. this also happens for any other option i choose that involves booting kubuntu. btw, i did a disc error check and it showed like 18 errors. ill get an exact list later

ps the hd is defiantly there because i just booted windows before installing

---

### Post by jcwmoore on 2008-01-21
I have had similar problems with ubuntu and my iMac G4 (power PC)...  now the solution was to do the following once you got to busybox
```
modprobe ide_core
```
and then
```
exit
```

after that ubuntu finished booting up just fine

[http://ubuntuforums.org/showthread.php?t=581280]("http://ubuntuforums.org/showthread.php?t=581280")

---

### Post by nkoi on 2008-01-21
nope, didnt work =\

ps, ctrl+alt+f1 bring up this error message:

cp:unable to open 'root/var/log/':no such file or directory
mount: mounting root/dev on /dev/.static/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem dosent have /sbin/init
target filesystem dosent have /sbin/init

---

### Post by darkcodemonkey on 2008-01-22
Well, the thing is, I CAN boot the liveCD, but I can't boot from my hard drive.
BTW, I tried what jcwmoore suggested, and just got the same thing:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

---

