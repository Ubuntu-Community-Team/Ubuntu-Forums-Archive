---
title: "graphics problem!!!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by ubuntokun on 2007-11-21
I adjusted my resolution to one higher than the normal 1024 and now when I boot ubunto I hear sounds but i'm not seeing anything but a black screen. How can I fix this problem. Can it be done from a command line? Please I really miss my Ubunto.

---

### Post by MaximusTG on 2007-11-21
Yes, you can fix this, start ubuntu, until you hear those sounds (the login sound I assume?) then press

ctrl+alt+f2 to switch to terminal 2

Login with your user name and password

run the following commands:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak  #backup existing xorg.conf
sudo dpkg-reconfigure -phigh xserver-xorg #this will reconfigure your xorg.conf

```

then switch back to your running x-session, 

ctrl-alt-f7

and press
crtl-alt-backspace to restart your x-session

---

### Post by ubuntokun on 2007-11-21
I adjusted my resolution to one higher than the normal 1024 and now when I boot ubunto I hear sounds but i'm not seeing anything but a black screen. How can I fix this problem. Can it be done from a command line? Please I really miss my Ubunto. I am still having the problem after using the codes:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak  #backup existing xorg.conf
sudo dpkg-reconfigure -phigh xserver-xorg #this will reconfigure your xorg.conf
 it now says 

x server -xorg postinst warning: something about overwriting configuration and need to back up 
/etc/X11/xorg.conf.20071121094717.:(

---

### Post by ubuntokun on 2007-11-21
graphics problem!!!
I adjusted my resolution to one higher than the normal 1024 and now when I boot ubunto I hear sounds but i'm not seeing anything but a black screen. How can I fix this problem. Can it be done from a command line? Please I really miss my Ubunto. I am still having the problem after using the codes:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak #backup existing xorg.conf
sudo dpkg-reconfigure -phigh xserver-xorg #this will reconfigure your xorg.conf
it now says

x server -xorg postinst warning: something about overwriting configuration and need to back up
/etc/X11/xorg.conf.20071121094717.
__________________

---

### Post by taurus on 2007-11-21
You can edit your /etc/X11/xorg.conf by hand, removing the high resolution that doesn't work.

```
sudo nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.  Then, reboot and see if it works again.

```
sudo shutdown -r now
```

---

### Post by oneadvent on 2007-11-21
> **ubuntokun said:**
> I adjusted my resolution to one higher than the normal 1024 and now when I boot ubunto I hear sounds but i'm not seeing anything but a black screen. How can I fix this problem. Can it be done from a command line? Please I really miss my Ubunto. I am still having the problem after using the codes:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak  #backup existing xorg.conf
sudo dpkg-reconfigure -phigh xserver-xorg #this will reconfigure your xorg.conf
 it now says 

x server -xorg postinst warning: something about overwriting configuration and need to back up 
/etc/X11/xorg.conf.20071121094717.:(

When did you change your resolution?

go to your /etc/X11/ folder by:

```
cd /etc/X11 
```

and type:
```
 ls xor* 
```

and post the output here

---

### Post by ubuntokun on 2007-11-21
WHAT are restricted drivers???

Im about to do a command which might affect the restricted drivers so could someone please explain what are these?

---

### Post by Inxsible on 2007-11-21
> **ubuntokun said:**
> WHAT are restricted drivers???

Im about to do a command which might affect the restricted drivers so could someone please explain what are these?
Restricted drivers are proprietary drivers and therefor Ubuntu doesnt supply them unless you agree to the terms and conditions of the driver manufacturer.

Most likely they are for your video card and you are possibly doing a ```
dpkg-reconfigure -phigh xserver-xorg
```, correct?

You can re-enable them by going to System>>Administration>>Restricted Driver Manager and selecting them to be enabled.

---

### Post by ubuntokun on 2007-11-21
I am trying to login on my system but everytimr it reaches the login page the screen is totally black even though i haer the boot up sound . what could be the problem why I see nothing not even to type in mty user name and password? Please help it is what I use to do Everything!!!!!! :(

Its not spamming but i am just geting pretty worried because all that you guys have posted are'nt working ang Im getting pretty concerned about countless valuable files on my pc

---

### Post by Inxsible on 2007-11-21
ubuntokun, why are you spamming the message boards?

This is the 5th thread I have seen from you for the very same problem. Here are your other 4 threads, and your question has been answered in at least 3 of them

[http://ubuntuforums.org/showthread.php?t=619342](http://ubuntuforums.org/showthread.php?t=619342)

[http://ubuntuforums.org/showthread.php?t=619279](http://ubuntuforums.org/showthread.php?t=619279)

[http://ubuntuforums.org/showthread.php?t=619261](http://ubuntuforums.org/showthread.php?t=619261)

[http://ubuntuforums.org/showthread.php?t=619210](http://ubuntuforums.org/showthread.php?t=619210)

---

### Post by ubuntokun on 2007-11-21
I still have the problem guys please dont give up on me i know Ive been  annoying you all day but after i tried 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
and then
sudo dpkg-reconfigure -phigh x server-xorg

and then Ctrl-alt-f7 and Ctrl-alt-backspace it said
x server -xorg postinst warning : overwriting possibly customised configuration file; back up in 
/etc/X11/xorg.conf.20071121122530

Please help me out. Iwant back my ubunto:confused::(

---

### Post by Inxsible on 2007-11-21
Are you friggin' kidding me?

[http://ubuntuforums.org/showthread.php?t=619359](http://ubuntuforums.org/showthread.php?t=619359)

---

### Post by PriceChild on 2007-11-21
Left one open thread: [http://ubuntuforums.org/showthread.php?t=619279](http://ubuntuforums.org/showthread.php?t=619279)

---

