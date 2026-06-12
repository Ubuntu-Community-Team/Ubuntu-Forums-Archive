---
title: "Sound problem"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by k-i-m on 2007-10-24
Hi! 
I just updated to 7.10, and Iam very satisfied. almost everything works fine. but my sound is gone! it has nothing to do with the upgrade..I did a mistake, i tried to fix a bug with a "ghost-cd". so i deleted sound-juicer for some reason??  and after that my sound is gone..
all i did was "sudo apt-get autoremove sound-juicer" i tried to install it again but my sound is still gone:S

---

### Post by DutyDuty on 2007-10-24
OK, first, if you have a Toshiba, definitely read this this :  [http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

If not, run ```
sudo asoundconf list
```
Then: ```
sudo asoundconf set-default-card (whatever the first result is from the previous code)
```
 
Test your sound. If that fails, run: ```
alsamixer -c 0
```
Check to see if master is muted (if it has an "MM" under it, it's muted. If it has "00", then check the other volumes.)

If the three of those, don't work, sorry.

---

