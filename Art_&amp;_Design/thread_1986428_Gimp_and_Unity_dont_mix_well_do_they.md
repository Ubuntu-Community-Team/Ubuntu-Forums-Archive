---
title: "Gimp and Unity dont mix well do they?"
date: 2012-05-24
forum: Art &amp; Design
---

### Post by MadmanRB on 2012-05-24
Okay I have my own issue with Unity and gimp that didnt seem to pop up during a serach.
Now I know of the issue that Gimp 2.6 has in ubuntu 12.04 with the magically disappearing launcher icon, I decided to give Gimp 2.8 a shot and it has an entirely different issue, I can get it running in my launcher without it vanishing for no reason but now its not in the unity dash menu!
Its simply gone, even manually adding it in using the menu editor does diddly squat.
I have to either A: pin it to my launcher and that is not good as I dont use it that often and only use it for the occasional image editing
B: manually search for it in the dash
C: Just use another DE or something.
This is a bizzare issue with unity as if unity doesnt have enough issues.

---

### Post by zombifier25 on 2012-05-29
Dunno about you but I can find it just fine, anywhere.

---

### Post by na5h on 2012-05-29
I had some problems with the launcher for 2.8 too...you should try to completely remove GIMP and then re-install it. Here's how I did it:

Remove GIMP
```
sudo apt-get purge GIMP
sudo apt-get autoremove
```

Install GIMP 2.8
```

sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
```

---

### Post by wilee-nilee on 2012-05-29
You can rest unity.

alt-f2 then type in 
```
unity --reset
``` 
then hit enter.

---

### Post by nll on 2012-06-02
[This was a bug]("https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916"), but it has been fixed. If you don't have the precise proposed channel enabled yet and don't want to wait, you can do this: Update Manager > Settings > Updates > check precise-proposed.

---

