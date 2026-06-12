---
title: "Dowloaded Java runtime envir 5 but can't  unpack and install it"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2006-12-19
The tar -xv etc command does nothing, and I can't seem to install this jre which I appreciated a lot in Windoze. O what to do?

---

### Post by taurus on 2006-12-19
What exactly is the name of the file?  I believe it would be something like jre-blah-blah-blah.bin which you run it directly to install it!!!

---

### Post by konungursvia on 2006-12-19
I'm dumb, and can't figure out the command to run. In Sun Solaris it was "run" and in DOS it was "run" but it doesn't seem to be here. It it bash?

---

### Post by konungursvia on 2006-12-19
Well I tried running it with the command sudo bash but it gave the errors:

Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_10-linux-i586.rpm
error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by jre-1.5.0_10-fcs.i586
        sh-utils >= 2.0-1 is needed by jre-1.5.0_10-fcs.i586
        fileutils >= 4.0-8 is needed by jre-1.5.0_10-fcs.i586
        gawk >= 3.0.4-1 is needed by jre-1.5.0_10-fcs.i586
        textutils >= 2.0-2 is needed by jre-1.5.0_10-fcs.i586
        /bin/sh is needed by jre-1.5.0_10-fcs.i586

?

---

### Post by taurus on 2006-12-19
If you download the .rpm, then you need to use alien to convert it to .deb before you can install it...

```
sudo aptitude update
sudo aptitude install alien
alien jre-1_5_0_10-linux-i586.rpm
sudo dpkg -i jre-1_5_0_10-linux-i586.deb
```
Why not download the .bin which is much easier to install than the .rpm stuff!!!

p.s.  Here is something for you to read...

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Add-On_Applications](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Add-On_Applications)

---

### Post by konungursvia on 2006-12-19
Thanks it went almost like that but it created *-i386.deb which seems to have installed without error but the web page I was hoping to use still says it needs a plugin. Do I need to reboot firefox or x?

---

### Post by taurus on 2006-12-19
You need to restart firefox only.

---

### Post by konungursvia on 2006-12-19
Wow! That Easyubuntu looks VERY useful, thanks a lot. I was able to extract it in /tmp/ but cant seem to install it now. :( The ./configure and make and install don't do anything, and I can't make out an executable.

---

### Post by taurus on 2006-12-19
You extracted it to /tmp!  What's the output of this command then?

```
ls -la /tmp
```

---

### Post by konungursvia on 2006-12-19
Oh, ok, used python to do it and now I have installed EasyUbuntu. Thanks very much, that sh*t is so good it should be in the distro!

---

