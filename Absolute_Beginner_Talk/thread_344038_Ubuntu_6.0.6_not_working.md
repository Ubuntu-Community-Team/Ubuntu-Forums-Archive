---
title: "Ubuntu 6.0.6 not working"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by T4tav on 2007-01-22
About 5 mins ago , i went to go onto linux but i get an error message saying something like "The x (GUI) something can not load". Then i go into ascii mode and i dont know what to do. HELP :lolflag:

---

### Post by Pobega on 2007-01-22
Have you tried running> startx

---

### Post by T4tav on 2007-01-22
I get a big nasty error , Sorry if somethings are wrong in this , but its alot to type : 
```
/usr/bin/startx: line132: cannot create temp file for here document: Read only file system

xauth: error in locking authority file /home/tavis/.xauthrourity
```

same for line 144 too.

```

Fatel server error:
Could not create lock file in /tmp/.tx0-lock

Giving up


```

---

### Post by scrooge_74 on 2007-01-22
You have to read the error messages to know what is wrong.  Did you made any changes lately?

you have a command line so log in using your normal user and pass

then do

sudo dpkg-reconfigure xserver-xorg

and read carefull the questions so you can have your GUI back

---

### Post by T4tav on 2007-01-22
I get the error 

```
x-server-xorg is not installed
```

and I have modified my fstab file latley

---

### Post by scrooge_74 on 2007-01-22
> **T4tav said:**
> I get the error 

```
x-server-xorg is not installed
```

and I have modified my fstab file latley

try again but this time do xserver-xorg  not x-server-xorg  you have a typo error there

---

### Post by T4tav on 2007-01-22
```
creating symbolic link `etc/X11/X.dpkg-new` to `/usr/bin.Xorg` : Read only file system
```

No good :( , I am serioulsy thinking of switching to SUSE

---

### Post by scrooge_74 on 2007-01-22
sudo dpkg-reconfigure xserver-xorg   does not works?  

then if everything fails go to /etc/X11/  and sudo nano xorg.conf and edit the file by hand

but first rad through the error log when you boot so you can have an idea why the Xserver is not working

---

### Post by T4tav on 2007-01-22
All the files are read only :mad: I cant edit anything

---

### Post by scrooge_74 on 2007-01-22
that is why you use "sudo" infront of the commands

---

### Post by T4tav on 2007-01-22
How do i modify the file ? 
 Well , What do i modify ?

---

### Post by scrooge_74 on 2007-01-22
ok, lets go slow

the easiest way is to just do   sudo dpkg-reconfigure xserver-xorg

with that utility it will be easier yo reconfigure X and get the GUI back

if it is not working (which seems odd), you can go the /etc/X11/ folder , there is a file call xorg.conf

you can edit it typing   sudo nano xorg.conf

depending on the error message you got when you boot you may have to edit either the video driver section or maybe is your mouse.

What kind of specs you have for your equipment?  Brand of video card, type of mouse, etc

dpkg-reconfigure should do the trick if you dont have that much experience

---

### Post by T4tav on 2007-01-22
I modified the file and tried to save it , it now says Error Writing File : Read only file system , at the bottem of nano :(

---

### Post by scrooge_74 on 2007-01-22
did you type sudo in front of nano xorg.conf ?

---

### Post by konst88 on 2007-01-22
I think you have a problem with the file system, cuz it is mounted read only.

---

### Post by T4tav on 2007-01-22
What can i do to fix it ?

---

### Post by oilchangeguy on 2007-01-22
ok, so maybe you've done something wrong to the system, maybe not. and since there is no system restore, or last known good configuration (that i'm aware of). instead of all this try this and try that, why not simply insert the live cd and re-install ubuntu. instead of switching to another version, because it's probably not 6.06's fault, maybe you did something that you're not aware you did. just wipe it and start fresh.

---

### Post by scrooge_74 on 2007-01-22
> **T4tav said:**
> I get the error 

```
x-server-xorg is not installed
```

and I have modified my fstab file latley

What changes you did to your fstab, can you post it?

---

### Post by T4tav on 2007-01-22
I modified something with the filesystem , but i cant save over that file now , but i have got a back up , but i think ill just do a clean install

---

### Post by T4tav on 2007-01-22
I modified something with the filesystem , but i cant save over that file now , but i have got a back up , but i think ill just do a clean install

---

