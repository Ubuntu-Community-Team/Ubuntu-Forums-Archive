---
title: "[SOLVED] download and install problems"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Phil420 on 2008-01-01
so I did install the program with the requested cd and all that stuff
and while on the new software, I can't download anything or install 
a thing all it says is that there's an error blablabla.. check the pic 

[IMG]http://i263.photobucket.com/albums/ii146/420phil/errorinstall.png[/IMG]

please help bacause I can't do anything but go on the internet, and I can't 
even download flash... when I try to open the install icon, it says there's 
no such automatic download or whatever...

thanks

---

### Post by taurus on 2008-01-01
Close down all windows especially the Add/Remove.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by richardjennings on 2008-01-01
hello

please could you open up a terminal and type:

```
sudo apt-get update
```



& post details of any error messages it gives you.

cheers

---

### Post by blithen on 2008-01-01
well fire up the terminal and type in
sudo dpkg --configure -a
then
sudo apt-get install ubuntu-restricted-extras
which will install flash, java,audio/video codecs.
This is assuming you have gutsy.
If you don't then I don't know about the restricted extras, but you should at least run the dpkg one.
If that doesn't fix your problem then run
sudo apt-get install -f

---

### Post by Phil420 on 2008-01-01
> **richardjennings said:**
> hello

please could you open up a terminal and type:

```
sudo apt-get update
```



& post details of any error messages it gives you.

cheers

okay it says E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem... which i did..

---

### Post by Phil420 on 2008-01-01
okay i think I got it. just figuring how to make a cube desktop.
thanks

---

