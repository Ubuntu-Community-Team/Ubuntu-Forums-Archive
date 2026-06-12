---
title: "[SOLVED] how to add application to startup programs"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by angel_zone on 2008-03-27
hi i would like yo add AWN to the startup menu i do searched the forum but i really still doesn't get it :oops: i would like to know how to do it step by step please:lolflag:

---

### Post by spiderbatdad on 2008-03-27
I think the simplest method is to have awn running, then navigate to System>>Preferences>>Sessions>>Session Options>> click remember currently running applications.

---

### Post by angel_zone on 2008-03-27
> **spiderbatdad said:**
> I think the simplest method is to have awn running, then navigate to System>>Preferences>>Sessions>>Session Options>> click remember currently running applications.

Hmm..:-k without needing startup program o.k i'll give that atry:)

---

### Post by angel_zone on 2008-03-27
o.k it didn't work i think i should add it to the startup menu any ideas????

---

### Post by spiderbatdad on 2008-03-27
Sorry I havent used awn.
You can try...System>>Preferences>>Sessions>>Start Up Programs>> click the ADD button and name it awn...for the command use the browse button to locate awn. Look in file sytem>>/bin/awn (is my guess) the command is the path to the file. It maybe in /usr/bin/awn or /usr/sbin/awn...once you have found it, just click it and it will fill in the field for you. After its added to the menu, make sure it is checked.

---

### Post by angel_zone on 2008-03-27
> **spiderbatdad said:**
> Sorry I havent used awn.
You can try...System>>Preferences>>Sessions>>Start Up Programs>> click the ADD button and name it awn...for the command use the browse button to locate awn. Look in file sytem>>/bin/awn (is my guess) the command is the path to the file. It maybe in /usr/bin/awn or /usr/sbin/awn...once you have found it, just click it and it will fill in the field for you. After its added to the menu, make sure it is checked.

i can't find the awn file in any of these paths??!! actually i can't find the bin file

---

### Post by spiderbatdad on 2008-03-27
bin should be the first folder in the file system

or run ```
sudo updatedb
locate awn
```

---

### Post by angel_zone on 2008-03-27
> **spiderbatdad said:**
> bin should be the first folder in the file system

or run ```
sudo updatedb
locate awn
```

i'm sorry i found the bin file in file system but the awn wasn't there.and i could't find user/bin even after showing hidin files

---

### Post by spiderbatdad on 2008-03-27
[http://ubuntuforums.org/showthread.php?t=692555](http://ubuntuforums.org/showthread.php?t=692555)

avant-windows-manager...see above link
:)

BTW the startup manager is quirky and sometimes takes several tries before it sticks.

---

### Post by angel_zone on 2008-03-27
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=692555](http://ubuntuforums.org/showthread.php?t=692555)

avant-windows-manager...see above link
:)

BTW the startup manager is quirky and sometimes takes several tries before it sticks.

thank you it worked from first shoot:lolflag: by the way i had question how do i know where my newly installed application exactly go, in windows i just simply open c drive and found all of them there

---

### Post by smartboyathome on 2008-03-27
They usually go to /usr/share with run files in /usr/bin and /usr/sbin. Source files go in /usr/local.

---

