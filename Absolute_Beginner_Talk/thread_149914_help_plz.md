---
title: "help plz"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by LORD_PoLvO on 2006-03-24
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")
on this i am up to step 10 and i am stuck i have had to log of my ubuntu and into xp so i can post this firstly can i continue straight fropm step 10 or do i have to go again also the file is located on my desktop but i dont know the "directory" can someone please tell me becasue i want this to work for me

---

### Post by akiro.yamamoto on 2006-03-24
The directory when you log in is ```
 ~/Desktop
```
If when you log on to Ubuntu the Display Manager (GUI LogOn Screen) refuses to
come up. Just enter your user name and password and do:
```

sudo /etc/init.d/gdm stop  (Ensures that the Display manager is stopped)
cd ~/Desktop
su 
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
sudo sh NV*.run -q

```
Then continue with the rest of the install as described in the linked post....
Hope this helps.

---

