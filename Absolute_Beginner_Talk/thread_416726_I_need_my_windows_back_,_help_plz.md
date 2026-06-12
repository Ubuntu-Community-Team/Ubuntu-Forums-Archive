---
title: "I need my windows back , help plz"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by medya on 2007-04-21
Hey I have two hard disks (first for windows , second for ubuntu)
because of a [Serious Bug in Feist Fawn]("http://ubuntuforums.org/showthread.php?t=415041&page=4"), Feity coulndt be installed on my PC normally , so I had to un-plug my first hard disk and then I installed it on my Second hard disk.

now Windows is gone .  because of that Bug in Feist Fawn if I reconnect my windows hard disk , the ubuntu wont load ...

whatever ...now I want to un-plug the ubuntu hard disk and just make my windows boot again.
what should I do  ?
is there any program in windows or in linux that make windows partition bootable agian ?

---

### Post by Legionox on 2007-04-21
Boot from your Windows Installation Disk and go into Recovery Console by pressing "R" or something like that (it'll direct you), select your Windows Partition by number (most likely to be "0" or "1"), then type in your Administrator password for that partition (assuming you have windows xp). Then type the command ```
fixmbr
``` into the recovery console and say Yes when it ask you whether you want to continue or not. Then after thats finished type ```
exit
``` and your computer should restart into windows (make sure you take out the windows cd while the POST in running). :)

---

### Post by antoz on 2007-04-21
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The above link offers a few solutions

---

