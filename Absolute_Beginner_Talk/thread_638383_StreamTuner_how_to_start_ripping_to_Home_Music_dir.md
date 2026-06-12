---
title: "StreamTuner how to start ripping to Home Music directory"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-12-12
**can't get it working**
Changed Record a stream in preferences
x-terminal-emulator -e streamripper %q -r -q -d /home/mozart/Music/StreamRipper

but it gives me this message (see pic)

> mozart@network:~$ streamtuner
/home/mozart/.themes/Creamy Classic/gtk-2.0/gtkrc:62: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/mozart/.themes/Creamy Classic/gtk-2.0/gtkrc:63: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/mozart/.themes/Creamy Classic/gtk-2.0/gtkrc:64: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.


---

### Post by tgalati4 on 2007-12-12
Does streamripper work in the local directory?

Go into your /Music/Streamripper directory

>streamripper 192.168.1.300:64000 -r  

(substitute your favorite internet radio station for the 192.xxx.xxx.xxx:xxx address)

>xmms localhost:8000 &

to listen to the steam.

Check the directory to see if files are being created.

The errors shown are compiz/effects errors.  They shouldn't effect the actual rip, but they may effect bringing up the terminal needed to host steamripper.  Why don't you just create a text script and put it on the desktop with a launcher and an icon?

---

### Post by MozartlovesUbun2 on 2007-12-12
> **tgalati4 said:**
> Does streamripper work in the local directory?

Go into your /Music/Streamripper directory

>streamripper 192.168.1.300:64000 -r  

(substitute your favorite internet radio station for the 192.xxx.xxx.xxx:xxx address)

>xmms localhost:8000 &

to listen to the steam.

Check the directory to see if files are being created.

The errors shown are compiz/effects errors.  They shouldn't effect the actual rip, but they may effect bringing up the terminal needed to host steamripper.  Why don't you just create a text script and put it on the desktop with a launcher and an icon?

hi ya thanks

well i never had this problem, i just installed Gutsy new, 

please see the pic i attached, thats the message it gives

(i also tried with compiz off, so that is ok)

---

### Post by MozartlovesUbun2 on 2007-12-12
> **tgalati4 said:**
> Does streamripper work in the local directory?

Go into your /Music/Streamripper directory

>streamripper 192.168.1.300:64000 -r  

(substitute your favorite internet radio station for the 192.xxx.xxx.xxx:xxx address)

>xmms localhost:8000 &

to listen to the steam.

Check the directory to see if files are being created.

The errors shown are compiz/effects errors.  They shouldn't effect the actual rip, but they may effect bringing up the terminal needed to host steamripper.  Why don't you just create a text script and put it on the desktop with a launcher and an icon?

**sorry, i didn't understand your directions properly, could you please explain again, i'm not sure what and how i have to do it, thanks in advance**

---

### Post by MozartlovesUbun2 on 2007-12-12
can someone please help me here with stream tuner ripping, thanks.

---

