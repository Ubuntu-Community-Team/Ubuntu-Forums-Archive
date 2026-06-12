---
title: "Restart Problem"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by hangster on 2006-05-19
I've I've recently installed Ubuntu Brizzy Badger 5.10 on my Sony VGN-FS675P/H laptop.  I had major issues with restarting and hibernation.  Out of perhaps the 30 times it restarted, only 2 were successful.  The unsuccessful tries were all frozen at the words "restarting.".  In those cases, I always had to manually shut my laptop down.  For hibernation, my computer never comes out of it and also freezes after it retrieves the data on the hardrive.  Shutting down was less of a problem but it sometimes freezes as well.  I've updated everything that was suppose to and it still had the problems.  Could someone please help me?  Thanks.

P.S.  I'm a beginner and have no experience w.Linux.

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=hangster]I've I've recently installed Ubuntu Brizzy Badger 5.10 on my Sony VGN-FS675P/H laptop.  I had major issues with restarting and hibernation.  Out of perhaps the 30 times it restarted, only 2 were successful.  The unsuccessful tries were all frozen at the words "restarting.".  In those cases, I always had to manually shut my laptop down.  For hibernation, my computer never comes out of it and also freezes after it retrieves the data on the hardrive.  Shutting down was less of a problem but it sometimes freezes as well.  I've updated everything that was suppose to and it still had the problems.  Could someone please help me?  Thanks.

P.S.  I'm a beginner and have no experience w.Linux.[/QUOTE]
Hibernation does not work with all laptops so that it not unusual. Dapper has much better hardware support so I bet it will work in 2 weeks. As for the restart, can you type:
> sudo reboot
in terminal and see if it works ?

---

### Post by hangster on 2006-05-20
[QUOTE=MasterChief1234]Hibernation does not work with all laptops so that it not unusual. Dapper has much better hardware support so I bet it will work in 2 weeks. As for the restart, can you type:

in terminal and see if it works ?[/QUOTE]


Uhm, I've tried and the only difference is that no words were displayed, only a blank screen, it still freezes however.  Also if the newer version of Dapper comes out can I automatically upgrade to it with in Brizzy?  Thanks.

---

### Post by Jagot on 2006-05-20
You could try this from terminal:

```
sudo shutdown -r now
```

You will indeed be able to upgrade directly from Breezy:

[https://wiki.ubuntu.com/DapperRC#head-926c82826296cbf2d63cb5dfbf7e5ba5d4e814c1](https://wiki.ubuntu.com/DapperRC#head-926c82826296cbf2d63cb5dfbf7e5ba5d4e814c1)

---

### Post by hangster on 2006-05-20
[QUOTE=Jagot]You could try this from terminal:

```
sudo shutdown -r now
```

You will indeed be able to upgrade directly from Breezy:

[https://wiki.ubuntu.com/DapperRC#head-926c82826296cbf2d63cb5dfbf7e5ba5d4e814c1](https://wiki.ubuntu.com/DapperRC#head-926c82826296cbf2d63cb5dfbf7e5ba5d4e814c1)[/QUOTE]


I tried that too, it still didn't work...  restart had a blank screen and never restarted.  When I shutdown done, however, it works.  Just restarting that's the problem...

---

### Post by sailor2001 on 2006-05-20
a suggestion:  ctrl+backspace to get splash and then click reboot at bottom left of screen.........That has always speeded up a reboot for me

---

### Post by sailor2001 on 2006-05-20
edit"  ctrl/alt+ backspace

---

### Post by hangster on 2006-05-20
[QUOTE=sailor2001]edit"  ctrl/alt+ backspace[/QUOTE]


I tried your suggestion, but the problem still persisted, my computer still freezes at restart.  It so frustrating, shutting down works but restarting....  Arrhhh...

---

### Post by Ecthelion on 2006-05-22
Maybe this can help you.
I Quote of auburn in this topic:
[http://ubuntuforums.org/showthread.php?t=178978]("http://ubuntuforums.org/showthread.php?t=178978")

[QUOTE=auburn]run levels are really cool. They're synonymous with F8 boot options in windows.For example, run level 1 is equivalent to "safe mode". When i first started linux, with debian, I didn't know how to shutdown until I learned you can simply tell it to change to run level 0... like this: $sudo init 0
rebooting is: $sudo init 6[/QUOTE]

---

