---
title: "Resolution - Out of range signal. Cannot display this video mode, change computer dis"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-03-09
I really read and search the site for an answer but I guess I need help since i am a new person to ubuntu

so i have a dual boot. win xp and linux. on my start up screen i ran:
Ubuntu, kernel 2.6.12-9-386
so right now it is loading modules, etc, etc... and then suddenly I get this thing on my screen. It says:

Out of range signal. Cannot display this video mode, change computer display input to 1920x1200 @ 60 hz

I dont know what to do. I have no problem running XP. I don't get why this is happening on ubuntu. My graphics card can go up to 1920x1200 on xp.
I have a radeon 9600 series 

please help

---

### Post by Kateikyoushi on 2007-03-09
Try this to load the right driver for the video adapter, and see if it works. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by gotquestions on 2007-03-11
that link you gave me didn't do the job. so soon as a i see the bootloader screen i clicked c for cmd line. i typed in

chroot /root nano /etc/X11/xorg.conf
* I got this error:  Error 27: Unrecognized format

so i typed out:
cat /etc/X11/xorg.conf ...and i see whole bunch of stuff.
I see Driver: "kbd" for "Input Device"
I see Driver: "ati" for "Device"

On the "Screen" section where Display is I do not see 1920x1200 registered

I do not know what to do now. and how come I cant copy?
error on both:
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ??

---

### Post by Pikestaff on 2007-03-11
try

```
dpkg-reconfigure xserver-xorg
```

Choose mostly the default stuff, but be sure you set the drivers that you want when it asks... and then when it asks what kind of screen resolutions you want, select the ones you want with the spacebar.

---

### Post by sad_iq on 2007-03-11
Do you have ubuntu allready installed or is it the Live-Cd?
 If it's installed you could press ALT+F1 to get to a command prompt to login then you could type "sudo dpkg-reconfigure xserver-xorg"...follow the instructions...BUT choose a lower resolution...that should help. Then you can install the driver for your video card from here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) (if you're running Edgy).
 If it's the Live-Cd...use it with the resolution it has until you install it and follow the link to install the video driver...but skip the  sudo dpkg-reconfigure xserver-xorg part.

---

### Post by gotquestions on 2007-03-11
thanks for your speedy response. so on cmd line i did type:
grub> [COLOR="Red"]dpkg-reconfigure xserver-xorg[/COLOR]

and i still got error 27: unrecognized command

:( i really got no clue why ubuntu is so mean to me.
i have GNU Grub version 0.95 if that makes any difference

---

### Post by gotquestions on 2007-03-11
i also typed:
sudo dpkg-reconfigure xserver-xorg  and i am still getting that funky error.

sad_iq- you've mentioned i need to install driveR? but theCD i have boots up for windows xp..not sure for linux (sorry i am such a newbie)

---

### Post by sad_iq on 2007-03-11
You're typing it too early...wait for ubuntu to boot and when you get the Out of range stuff press ALT+F1 login and type sudo dpkg-reconfigure xserver-xorg

---

### Post by gotquestions on 2007-03-11
i tried several ways here are my steps and still getting the Out of range problem on my screen


Attempt 1
wait for ubuntu to boot settings press ALT+F1 --> Out of range problem

Attempt 2
wait for ubuntu to boot and when you get the Out of range stuff press ALT+F1 --> Out of range problem

---

### Post by sad_iq on 2007-03-11
Ok...then try this...when the computer starts it shows something about "Press ESC in"3..2...1 ...well press ESC when that happends and choose Recovery Mode (or similar...haven't done that in a long time :) ). That should log you in as root and you can type **dpkg-reconfigure xserver-xorg** withought sudo...folow the steps..and when done type **shutdown -r now**

---

### Post by Chuckanut on 2007-03-11
> **gotquestions said:**
> i tried several ways here are my steps and still getting the Out of range problem on my screen


Attempt 1
wait for ubuntu to boot settings press ALT+F1 --> Out of range problem

Attempt 2
wait for ubuntu to boot and when you get the Out of range stuff press ALT+F1 --> Out of range problem

I'm in the same situation as you and am here trying to find a solution to my problem.  Try pressing CRT+ALT+F1 - that gets me to a command line.  Now if I can figure out what to do then.....

---

### Post by gotquestions on 2007-03-11
thank you! you saved my day! :)
going thru the xconf screeen was quite intimidating heh.

---

### Post by gotquestions on 2007-03-11
> **Chuckanut said:**
> I'm in the same situation as you and am here trying to find a solution to my problem.  Try pressing CRT+ALT+F1 - that gets me to a command line.  Now if I can figure out what to do then.....

read what Sad_IQ told me (last post of his) it definitely helped me out.

---

### Post by sad_iq on 2007-03-11
Darn.. .:oops:  I forgot about CRT in the ALT+F1 step...sorry!!!
 Well..press it(ALT+CRT+F1)...type your user_name...hit Enter...Type your password...Hit Enter
 that should get you logged in...then type **sudo dpkg-reconfigure xserver-xorg**...follow the steps...choose **medium** when it asks about **monitor** stuff...follow instructions...and when it's over type sudo **shutdown -r now** . When the computer starts you should be able to use the GUI. then go to [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) and install the graphical driver to get 3d acceleration and a chance to change the resolution again...or save the instructions on that page (on paper :lolflag: ) and skip the **sudo dpkg-reconfigure xserver-xorg** step

---

