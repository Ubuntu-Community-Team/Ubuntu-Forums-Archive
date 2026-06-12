---
title: "updating ndiswrapper now, need command help, please!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by doobey on 2007-06-13
I am following these directions for my wireless card ( [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28bcm4318%29%7C%28broadcom%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28bcm4318%29%7C%28broadcom%29) ) and I unpacked ndiswrapper-1.47 to my desktop.

now I need to change directory to that folder

is it this cd ndiswrapper-1.47/

it says no such directory. should I move it somewhere first?

Thanks, 

I am in LiveCD to see if this works....

~d

---

### Post by Seisen on 2007-06-13
Did you go to your desktop then to that directory? Also you don't need to add that slash mark either.

---

### Post by doobey on 2007-06-13
do u mean cd desktop?

I can see the folder on the desktop

maybe its because I am using LiveCD???

---

### Post by doobey on 2007-06-13
i also used 

tar -xzvf ndiswrapper-1,47.tar.gz

same result. but i see the folder in desktop, perhaps it should be somewhere else? or must work from installed ubuntu?

---

### Post by Bachstelze on 2007-06-13
To browse to your desktop in the terminal :

```
cd ~/Desktop
```

You can then use *ls* (it's lowercase *LS*, for ***l**i**s**t*, not *is* !) to see what you have in the current dir.

---

