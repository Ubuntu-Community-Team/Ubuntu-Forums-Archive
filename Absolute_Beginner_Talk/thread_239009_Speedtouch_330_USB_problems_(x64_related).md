---
title: "Speedtouch 330 USB problems (x64 related?)"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by petedee on 2006-08-18
Hey all, I'm a little new to this whole linux first but I thought i would give ubuntu a try to see if i would be safer than windows is these days.

So I've got a silver speedtouch 330 usb modem that I got from my ISP and I'm trying to get it running on the AMD64 distro of ubuntu drapper drake. I've followed a couple of guides (namely [this one]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch") and [this one]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html#pppoe")) and neither of them worked, checking my messages file in /var/log I have the line 

```
ATM dev 0: ADSL line is up (3648 kb/s down | 448 kb/s up 
``` so i think its connected however when i start firefox to load a page I get the "Firefox can't find the server" line. I've tried pinging google as well but that doesn't seem to work.

Have I done something wrong? Is the process any different for AMD 64 systems? Would it be a load easier to get a router instead?

If I can't get ubuntu online then I think I'll have to go back to windows :(

---

### Post by ice60 on 2006-08-18
hi, i have got the silver Speedtouch 330 working in the past, i'll have alook to see how i did it in abit, i'm abit busy atm. i'll definately post back within 24 hours if no one else does.

do post if you get it working though so i don't waste my time.

---

### Post by petedee on 2006-08-18
Hi, I don't really know where to start with it tbh. I've followed the instructions to the letter and it still doesn't work  :(

---

### Post by ice60 on 2006-08-19
hi, these are the instructions [here](http://steve-parker.org/speedtouchconf/)

you need to download these two files

[http://kent.dl.sourceforge.net/sourceforge/speedtouchconf/speedtouchconf-27-Jun-2006.tar.gz](http://kent.dl.sourceforge.net/sourceforge/speedtouchconf/speedtouchconf-27-Jun-2006.tar.gz)

[http://steve-parker.org/speedtouchconf/firmware/rev4fw.zip](http://steve-parker.org/speedtouchconf/firmware/rev4fw.zip)

put them in your home directory, that's the same as My Documents in win32. you should be able to click, from the Desktop menu, Places>Home Folder.

then decompress the speedtouchconf-27-Jun-2006.tar.gz archive - open Terminal
```
alt-F2 then run this gnome-terminal
```
then copy and paste this into terminal and hit enter
```
tar xzvf speedtouchconf-27-Jun-2006.tar.gz
```
a new directory should appear called speedtouchconf-27-Jun-2006.

now drag rev4fw.zip into the new directory, you don't need to do anything more with it

go back to the terminal and type this to move into the new directory
```
cd speedtouchconf-27-Jun-2006/
```
and press enter (NOTE. instead of typing in all these long names you can type just the first 2 or 3 letters then press the tab key, the one with 2 arrows, to auto-complete what you're typing in)

now, do this in terminal to run the modem setup
```
sudo ./speedtouchconf.sh
```
it should then show you something like this -
[http://steve-parker.org/speedtouchconf/script.shtml](http://steve-parker.org/speedtouchconf/script.shtml)
you need your ISP username and password and the VPI VCI numbers. if you live in a country which the script shows the correct VPI VCI numbers then just copy them there, if not you can find the numbers on google.

that should be it, everytime you bootup the script should startup too. however, if it doesn't, which happened to me with some installations, you'll need to run the undo script before you can run speedtouchconf.sh again.
```
sudo ./undo.sh
```
before you run the script you have to be in the speedtouchconf-27-Jun-2006 directory
```
cd /home/***username***/speedtouchconf-27-Jun-2006/
```

 if you forget to run it you'll have to run it then reboot :rolleyes: the best thing to do, if you don't automatically connect, is to run undo.sh right after you have run the speedtouch script so you don't forget. lol

let me know how it goes. :)

---

