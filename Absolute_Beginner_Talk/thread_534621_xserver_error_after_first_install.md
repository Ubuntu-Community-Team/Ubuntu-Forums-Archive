---
title: "xserver error after first install"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by kittyloaf on 2007-08-25
Just bought a new laptop, installed Debian but it was impossible to get ANYTHING to work at all...so i installed the newest Ubuntu (7.04)

These are my specs

```

15.1" WXGA monitor 1280x800
1.50 GHz Intel® Core™2 Duo T5250 667MHz 2MB
Intel® GMA X3000
1GB DDR2 800MHz/PC6400 Ram
80GB 5400rpm. SATA hårddisk
Intel Pro/Wireless 4965AGN
SAMSUNG COMBO 6xx4w/6xx5WD/3xx5W

```


Installation went well.. but after install when it was supposed to start for the first time, it gave me an error saying that a monitor was found but none of the configurations could be used for it...

i tried this....

sudo apt-get install xserver-xorg-video-intel  (think that was the name)

then

sudo dpkg-reconfigure xserver-xorg

and then i configured everything as it should be (i think)

This time it didn't give me an error though, when i wrote startx it just went blank and nothing happend.


Please help, i am longing to play with my new laptop ='(

---

### Post by vpjr on 2007-08-25
hi kittyloaf,

did the computer boot and run with live CD?

regards,

ven

---

### Post by kittyloaf on 2007-08-25
No, i used the alternate disc since i got an error saying "can't access tty" , the thing was that it was a clean install, there was nothing on the HDD since it's a brand new laptop.

---

### Post by vpjr on 2007-08-25
can you post the result of "more /etc/X11/xorg.conf" ?

regards,

ven

---

### Post by kittyloaf on 2007-08-25
Well....how? =P    since i can't enter xserver at all, it will be hard to show it to you.... i could try to upload it to an FTP server i guess...will try that =/

will make a new post to bump this when i have fixed the xorg.conf ^^

---

### Post by kittyloaf on 2007-08-25
kk so i uploaded it to an FTP server ^^

check the xorg.conf here

[http://documentcat.com/xorg.conf](http://documentcat.com/xorg.conf)

---

### Post by Majorix on 2007-08-25
Comment out the lines that start with HorizSync and VertRefresh then try again.

---

### Post by kittyloaf on 2007-08-25
tried to comment them out, no change.

---

### Post by kittyloaf on 2007-08-26
I filmed my problem here...

[http://documentcat.com/doc/test.3gp](http://documentcat.com/doc/test.3gp)

on the video i am first trying a live distro, and then rebooting and trying the "real" distro on the HDD, as you can see the screen goes blank when using the Intel driver...when i use the Vesa one it just gives me an error.....the live distro uses the Vesa one though :/

i already tried to swap the xorg.conf files...

---

### Post by vpjr on 2007-09-12
hi,

my apologies for the delay.  My boss sent me out of town for a while. anyway. how was the problem?  solved?

if not:

swapping the xorg.conf file might not have worked because the intel-video driver was still installed.  Remove it first and then try swapping again.

best regards,

ven

---

