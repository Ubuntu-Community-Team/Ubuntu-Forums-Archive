---
title: "screen reolution"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by jacklindsay on 2006-09-06
hello to all,

im sorry if this topic has been brought up already but i have just installed linux ubuntu 6.06 after first playing with the "live CD version" and noticed something not quite right.  the Live version was in my normal 1280x1048 (i think thats what it is) but after the proper installation the screen is now 640x480 and i cant stand it but when i go to change it, nothing happens.  i click the arrows it just does nothing.  have i missed something in the installation?  

all help appreciated 

jack Lindsay

---

### Post by moore.bryan on 2006-09-06
*edit the /etc/X11/xorg.conf file to include your resolution in the monitor section.*

---

### Post by braheem on 2006-09-07
> **moore.bryan said:**
> *edit the /etc/xorg.conf *

:arrow: /etc/X11/xorg.conf

---

### Post by moore.bryan on 2006-09-07
> **braheem said:**
> :arrow: /etc/X11/xorg.conf

*corrected... thanx braheem.*

---

### Post by jacklindsay on 2006-09-07
hello and thanks for the reply as i am very new to this is there any chance u can tell me how to find this file?

thanks 

jack Lindsay

---

### Post by moore.bryan on 2006-09-07
[I]open a terminal (if you're running gnome, it's in the applications menu).
type ```
sudo gedit /etc/X11/xorg.conf
``` and browse to the "monitor" section.  make sure you have the resolution you want in each of the sub-sections.
[/I]

---

### Post by jacklindsay on 2006-09-07
hello again right i have just really messed up my computer  now under all the different subdirectories were different resolutions ranging from 1024x1048 down to 640 x480 so i scholled to the top where it said default and 24 and i changed it to 4 (which was default sub directory) and now it wont let me get into ubuntu.  it gives me all these different error messages to view reports.  i fear that i will have to blitz my hard drive at the moment im running on a XP partition (the only one left that works) 

PLEASE HELP ME

i do get a screen come up ( like a DOS screen) after i click all the ok's and it says 
USERNAME: so i type that in then it says PASSWORD so i type that in and then i type in the bit of code in the hopes that it will show up that window again but it just says code does not exist (or something like that) and that i should type in a help code

---

### Post by moore.bryan on 2006-09-07
*you shouldn't have changed the 24.  after entering your password, have you typed ```
sudo gedit /etc/X11/xorg.conf
``` again?  if that doesn't work, try ```
sudo dpkg-reconfigure xserver-xorg
```.*

---

### Post by moore.bryan on 2006-09-07
*another way to go is covered in another thread ([http://ubuntuforums.org/showthread.php?t=27029);]("http://ubuntuforums.org/showthread.php?t=27029%29;") that worked for my issues.*

---

### Post by bodhi.zazen on 2006-09-07
> **jacklindsay said:**
> hello again right i have just really messed up my computer  now under all the different subdirectories were different resolutions ranging from 1024x1048 down to 640 x480 so i scholled to the top where it said default and 24 and i changed it to 4 (which was default sub directory) and now it wont let me get into ubuntu.  it gives me all these different error messages to view reports.  i fear that i will have to blitz my hard drive at the moment im running on a XP partition (the only one left that works) 

PLEASE HELP ME

i do get a screen come up ( like a DOS screen) after i click all the ok's and it says 
USERNAME: so i type that in then it says PASSWORD so i type that in and then i type in the bit of code in the hopes that it will show up that window again but it just says code does not exist (or something like that) and that i should type in a help code

Now you've done it.

Try this:
```
sudo nano /etc/X11/xorg.conf
```
Change you default color depth to 16

Ctrl-X to exit nano, "Y" to save edit

then
```
sudo gdm
```
to re-start gdm

---

### Post by ske1fr on 2006-09-07
Don't panic, Jack.

That "DOS" screen is the best you can get when your machine can't start the X server that provides you with the nice Windows-like front end you're accustomed to.

If your machine is still logged in as you described then there is a way to set up the X server again.  I've had to do it recently myself.

At that "command line" type in the command

**sudo dpkg-reconfigure xserver-xorg**

It will start asking you lots of questions about your keyboard (just agree to the defaults it should show selected, and press Return) and eventually it will get to the screen resolution stuff.  I'm not at my Kubuntu machine right now so I can't run through this with you, but there's one screen where you choose what resolutions you want to have available.  You need to make sure all the ones that you know for sure your monitor (or screen if a laptop) can handle, and make sure they are marked with an asterisk (you move the cursor down the list with the tab key and press the spacebar to select each one).   Make sure too that the X server is the correct one for your graphics card (or the built-in graphics system if appropriate).  You can choose your colour depth too.  When you get to the end, save the file, then restart the computer.  That's

**sudo shutdown -r now**

that you type at the command line.

Have a look at this page [ click me!](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28dpkg-reconfigure%29%7C%28xserver-xorg%29) for some explanation and advice that's relevant.

---

### Post by jd65pl on 2006-09-07
This thread may help you [http://www.ubuntuforums.org/showthread.php?t=252065]("http://www.ubuntuforums.org/showthread.php?t=252065")

---

### Post by jacklindsay on 2006-09-07
fixed WOOHOO cheers ske1fr and everyone else thank god i didn't have to blitz the hard drive your all legends

---

