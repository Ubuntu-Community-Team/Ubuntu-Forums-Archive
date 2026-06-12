---
title: "HELP!!! I can't get my desktop back!!"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-08-12
Well, in my attempt to get my video card to be better supported I basically have made it not work.
Now, when it starts up, it doesn't even go to the welcome screen where you login. 

Before I can login in what looks like terminal it gives be a blue screen that says:
 Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem?
        <Yes>    <No>

after i hit enter it says:
(==) log file: "/var/log/Xorg.0.log"
(==) Using config file: "/etc/X11/xorg.conf"

then after i hit enter it says:
The X server was disabled. Restart GDM when it is configured correctly.

I know I shouldn't have messed with it but now I just want the thing to start up correctly. What do I do?

It was working before without video but at least the desktop was there.....

---

### Post by philinux on 2007-08-12
> **chaddiesel said:**
> Well, in my attempt to get my video card to be better supported I basically have made it not work.
Now, when it starts up, it doesn't even go to the welcome screen where you login. 

Before I can login in what looks like terminal it gives be a blue screen that says:
 Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem?
        <Yes>    <No>

after i hit enter it says:
(==) log file: "/var/log/Xorg.0.log"
(==) Using config file: "/etc/X11/xorg.conf"

then after i hit enter it says:
The X server was disabled. Restart GDM when it is configured correctly.

I know I shouldn't have messed with it but now I just want the thing to start up correctly. What do I do?

It was working before without video but at least the desktop was there.....

You need to type in
sudo dpkg-reconfigure xserver-xorg

Just follow the prompts mostly go with the default i.e what the system detects.
You will have it up and running as good a new!

---

### Post by creedog on 2007-08-12
its also possible that the installer that you used made a backup of the xorg.conf file. if this is the case then you need to go ahead and copy that file back over the new xorg.conf. it will look something like this.


cd /etc/X11/
ls xorg*
 there should be two or more files here. Then make a copy of your xorg.conf

cp -p xorg.conf xorg.conf_bad 
mv xorg.conf_<something> xorg.conf
startx


Assuming that there is a backup sustitute for xorg.conf_<something>

---

### Post by chaddiesel on 2007-08-12
ROCKIN!!!!!!
:guitar:

Thanks!! worked like a charm!!

---

