---
title: "unchecked login with gui"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by berk21 on 2006-10-18
need help on getting back to the gui...

read up on the problem and all i can come up with was 
sudo dpkg-reconfigure xserver-xorg...and being a comlpete n00b at this, got me no where fast.

please help](*,)

---

### Post by jordanmthomas on 2006-10-18
Since you can't get logged into a GUI, I am assuming you have a nasty blue screen.
Press Alt + F2
log in

run
```
sudo dpkg-reconfigure xserver-xorg
```
followed by
```
sudo /etc/init.d/gdm stop
gdm
```

Post back if anything goes wrong.

---

### Post by berk21 on 2006-10-18
no i did the sudo dpkg-reconfigure xserver-xorg and thats what brings me to the blue screen...went through and it gave me an error  so i alt f2 back and here i am.

---

### Post by jordanmthomas on 2006-10-18
Try stopping gdm first, and then reconfiguring.  I had the same problem once where it would switch me for no reason over to tty7.

---

### Post by berk21 on 2006-10-18
ok did that and this is what i got.

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process

---

### Post by jordanmthomas on 2006-10-18
```
ps -A | grep dpkg
```
take note of the number at the start
```
sudo kill NUMBER
```

or

```
sudo killall dpkg dpkg-reconfigure
```
Then try again.

---

### Post by berk21 on 2006-10-18
im not even sure i did anything....

i tried ps -A grep dpkg
then saw 2 numbers 
1st was 7157 tty2
2nd was 00:00:00
 
tried sudo killall dpkg dpkg-reconfigure and got dpkg: no process killed

---

### Post by jordanmthomas on 2006-10-18
Well, it seems you killed dpkg (which is what I was getting at)
Can you run the reconfigure now or is it still complaining?

---

### Post by berk21 on 2006-10-18
sudo dpkg-reconfigure xserver-xorg brings me to the blue screen promps...asking to auto detect recommmened x server and so on

---

### Post by jordanmthomas on 2006-10-18
oooohhh, that's good.  You should answer the questions as best you can.  Usually the defaults will work fine.

---

### Post by berk21 on 2006-10-18
berk21  berk21 is online now
First Cup of Ubuntu
	  	
Join Date: Oct 2006
Beans: 5
Re: unchecked login with gui
no i did the sudo dpkg-reconfigure xserver-xorg and thats what brings me to the blue screen...went through and it gave me an error so i alt f2 back and here i am.


past reply?

ill try again though.  brb

---

### Post by berk21 on 2006-10-18
back to square 1

heres what i got after the prompts

xserver-xorg postinst warning : overwriting possibly-customised configruation file; backup in/etc/X11/xorg.conf.20061018215922

---

### Post by jordanmthomas on 2006-10-18
Ok, so now X should be configured.  Do you still get errors if you try
```
sudo /etc/init.d/gdm stop
sudo gdm
```
?

---

### Post by berk21 on 2006-10-18
ok screen blinks 3 times and ERROR

Failed to start the x server. It is likley that it is not setup correctly. Would you like to view the x server output to diagnose the problem?   yes or no

---

### Post by berk21 on 2006-10-18
this all is comming up just because i unchecked the option to login gui

all i thought i was doing was loggin in w/out the ubuntu screen...and now this...im wondering if a re-install i easier

---

### Post by jordanmthomas on 2006-10-18
See if you have an old xorg.conf that might work 
```
 ls /etc/X11
```
You might get lucky and have one you can restore.

---

### Post by berk21 on 2006-10-18
ok what am i looking for...it gave me a few lines that have color to them

---

### Post by jordanmthomas on 2006-10-18
The older files would probably be best, and one like this:
```
xorg.conf~
``` would be excellent, as it would have come from when your GUI worked.
If you have one that is from a time when everything was peachy, you can use it:
```
 sudo cp /etc/X11/xorg.conf**whichever** /etc/X11/corg.conf
```

As a temporary solution, try changing your video driver to vesa instead of whatever you have there now (an option when reconfiguring)

---

### Post by berk21 on 2006-10-18
ok...your loosing me...n00b as n00b can be..lol...this is what i got 



app-defaults    gdm    xorg.conf   xsession.d


config        rgb.txt   xorg.conf 20061018210857    xsession.options


cursors        x       xorg.conf 20061218215922      Xwrapper.config


default-disply-manager     xinil   xresources


fonts       xkb  xsessions


if that makes sense at all??

---

### Post by berk21 on 2006-10-18
i tried to type them as best as possible...they seem to be in columns if that helps

---

### Post by berk21 on 2006-10-18
question...why am i not logged in as root?

---

### Post by jordanmthomas on 2006-10-18
Ok, you don't have any backups in there. Sorry

You are not logged in as root because Ubuntu thinks you should use sudo instead.

The only thing I can think of is to reconfigure (yet again) and when it asks which video driver to use, use vesa.

By the way, what kind of graphics card do you have?

---

### Post by berk21 on 2006-10-18
just got done with the versa driver thing..

Nvidia

prior to the whole catastorphy i just got my vid card settings fixed after a udate i did... i had to  sudo gedit /usr/share/applications/nvidia-setting.desktop and save that...but that wont help will it?

also want to say thanks for the attempts to achieve to fix this

---

### Post by jordanmthomas on 2006-10-18
I don't think that editing the launcher would make X fail.  Maybe someone with an Nvidia card can help...I'm not sure of what you need to do with such a card but I'm pretty sure that after a kernel update you have to recompile it.  

Sorry, but I've helped about as much as I can.  :(

---

### Post by berk21 on 2006-10-18
well...i can re format it and start over and NEVER EVER uncheck the boot without GUI ;)

---

