---
title: "Clarifying an xorg problem"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by kristalsoldier on 2007-03-14
Hi...

I was trying to work on the 3ddesktop. Downloaded the drivers etc and then, predictably, messed up. The net result is the GUI is borked. However, while fooling around in the terminal, I had a line which basically said if anything goes wrong, the following was the backup:

cp /var/backups/xorg/xorg.conf.2007-03-14-18:20:07/ etc/x11/xorg.conf

So, I went into the recovery mode and entered it at the prompt...throws out an error message:

cp: missing destination file operand after 'var/backups...etc from the line above.

Looking at some of the advise from related posts, I found this command:

(1) sudo nano/etc/x11/xorg.conf

and

(2) dpkg-reconfigure xserver-xorg

I have two queries:

(1) Which command should I use and where to use the backup command that I got from the terminal? Also, what is an operand in the context of the error message as mentioned above?

(2) Also because I was not paying attention, I wrongly entered some stuff in the recovery mode and now I get myname-laptop tty1 - what does this mean and is there anything I should do? This is probably not related to the xorg problem, but I thought I'd mention it here.

My Laptop has Nvidia GeForce Go7400

Thanks

---

### Post by NikoC on 2007-03-14
I think you want to get rid off nvidia drivers you wrongfully installed...
in terminal:

uname -r     
--> remember this number that output gives you

sudo apt-get remove --purge nvidia-glx nvidia-kernel-common linux-restricted-modules-number   
--> this will remove all nvidia related packages

sudo nano /etc/X11/xorg.conf
--> find the Section "device" line and replace "driver" "nvidia" with "driver" "nv" and save the file


sudo shutdown -r now
--> you will reboot and should be able to start into graphic mode again

Now depending on the Ubuntu distro you are using, i.e. dapper, edgy or feisty, do a search on beryl or compiz (depending on which window manager you want to use, I myself use beryl)  howto and nvidia combined... that will give you some nice installation guides for 3ddesktop
e.g. an advanced search on "Beryl nvidia howto" and option "titles only" gives you [this]("http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+howto+edgy") nice link

---

### Post by kristalsoldier on 2007-03-14
> **NikoC said:**
> I think you want to get rid off nvidia drivers you wrongfully installed...
in terminal:

uname -r     
--> remember this number that output gives you

sudo apt-get remove --purge nvidia-glx nvidia-kernel-common linux-restricted-modules-number   
--> this will remove all nvidia related packages

sudo nano /etc/X11/xorg.conf
--> find the "device" line and replace "driver" "nvidia" with "driver" "nv" and save the file


sudo shutdown -r now
--> you will reboot and should be able to start into graphic mode again

Now depending on the Ubuntu distro you are using, i.e. dapper, edgy or feisty, do a search on berl or compiz howto and nvidia combined... that will give you some nice installation guides for 3ddesktop

OK. Just a few more clarifications. When you say 'in terminal' do you mean the screen I get (non GUI) when I get into the recovery mode? Sorry for being dense, I have always thought of the terminal as being the box that one opens up in the GUI mode. Also, that number that you say make a note of...what do I do with it?

Lastly, what of the backup line? I don't need it anymore?

Thanks and apologies for being a nosy pest!

---

### Post by NikoC on 2007-03-14
My mistake, wrong terminology:
By terminal I do mean the 'non gui' screen you enter in recovery mode.
The number is actually the version of the modules on which the nvidia driver depends and that has been installed on your system. You need to remove these modules to make a clean start. You have to add this number to the line I posted:

sudo apt-get remove --purge nvidia-glx nvidia-kernel-common linux-restricted-modules-number

so instead of the last word number you enter the output you get from 'uname -r'.

I don't really know what you mean by 'backup command'... maybe you can clear that out a bit more...

---

### Post by annda on 2007-03-14
if you had a working configuration, i think it would be a good idea to restore it. in your first post you quoted a "missing destination file operand" - it means that the command cp only noticed ONE operand (the backup file to be copied). make sure you have a space between /var/....... and /etc/X11/xorg.conf

you probably will not need to remove all the nvidia stuff at this point. see if the backup works first.

---

### Post by dannyboy79 on 2007-03-14
for one thing, your command you entered had a slash at the end which is why it failed, you made it think it was trying to copy the directory /var/backups/xorg/xorg.conf.2007-03-14-18:20:07/ into a file called etc/X11/xorg.conf and there is no such directory. not to mention also, that there is no location etc/X11/ BUT there is a location called /etc/X11/, see the difference. in linux the slash is very important. so try this

cp /var/backups/xorg/xorg.conf.2007-03-14-18:20:07 /etc/x11/xorg.conf

and see what happens, otherwise just try waht the other user is suggesting. true, a terminal is what you think it is, he meant the cli (command line interface). the guy was simply telling that during some of the instructions, you're required to know what your uname -r is, so you should either remember it or write it down.

---

### Post by kristalsoldier on 2007-03-14
OK...Cool...Thanks. I'm going to try it now! I'll get back one way or another! See u all in a bit!

---

### Post by kristalsoldier on 2007-03-14
Damn...neither worked. I tried the first option of using the backup...nothing...

Then I tried with removing of nvidia and it says: The X server is now disabled. Restart GDM when it is cnfigured correctly.

What do I do now? Thanks

---

### Post by annda on 2007-03-14
have you substituted "nvidia" with "nv" as your driver? and stil it doesn't work?

what about sudo dpkg-reconfigure xserver-xorg ? it should ask you a few questions and write the right configuration to xorg.conf

EDIT: in case you updated the kernel (maybe via update-manager along with other updates) after installing nvidia drivers, you will have to reinstall nvidia-glx

---

### Post by NikoC on 2007-03-14
Then there is always the option to reconfigure X:

dpkg-reconfigure xserver-xorg

I'm not really sure if 'sudo' needs to put in front of that line... well you can just try it...
If I recall correctly one of the first options is to select your video card, I would try "nv" in your case... 
I usually answer the other 'questions' with the suggested default values.

edit: but first check, as annda suggested, if you have replaced "nvidia" by "nv" in the Section "device" in xorg.conf

---

### Post by kristalsoldier on 2007-03-14
> **annda said:**
> have you substituted "nvidia" with "nv" as your driver? and stil it doesn't work?

what about sudo dpkg-reconfigure xserver-xorg ? it should ask you a few questions and write the right configuration to xorg.conf

I did the change from nividia to nv...I got the error msg I posted last...did not try the sudo dpkg command am doing so now....cant do it it moves straight into the X Server is now disbaled mode...

Help!!!!!

OK....I got into the reconfigure mode. I hit all the values presented by default and then come to the "Desired colour depth". the options are 15/ 16/ 24. I picked 24 and it does nothing...Well it did...and the GUI is back. But there is a strange distortion to it...everything looks stretched and somewhat blurred!

Can I fix this? How?

In addition to the display, whatever I did also killed my wireless networking! Now what do I do?

---

### Post by annda on 2007-03-14
as to blurry look: it is a result of wrong resolution/refresh rate. what is your display's default/optimum resolution and refresh rate? is it the same when you go to system > preferences > screen resolution? if not, can you change it? if not, you will need the nvidia driver (my laptop has the same issue).

back up you xorg.conf first, for example like this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

if something goes wrong, use the same command with the files in reverse order to go back:

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

search for nvidia in synaptic and install restricted modules for your kernel (i suppose they might be needed by your wireless, too, but i'm not quite sure: what is your wireless adapter?) and nvidia-glx. a good guide is here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

after restarting X you should be able to change your resolution (either via GUI or manually in xorg.conf).

good luck and post back with the results.

---

### Post by dannyboy79 on 2007-03-14
use envy, it's the easiest way to get everything going with nvidia cards. tseliot is the author and he has been using the nvidia driver from as long as I can think of.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
some1 said this link didn't work before so if for some reason it doesn't, just erase everything but [www.albertomilone.com](www.albertomilone.com) and you'll find it from his home page

---

### Post by kristalsoldier on 2007-03-14
OK folks the screen resolution etc is now back to normal. I booted and rebooted about 5 times just to make sure that this was not a flash in the pan. But the Networking thing is off...and I mean permanently. I think network-manager got corrupted somehow and got itself deleted because when I go to System>Admin>Networking I can only see a Wired Connection and the Modem connection when earlier there was a wireless connection too.

So, 2 questions:

1. Should I be changing the thread and strarting a new one - don't know the forum protocols on this and 

2. What can I do to get my machine back on the net? I have a broadband connection and the ISP sent me an ADSL modem which only works for windows. I have been using a Linksys Wireless router to connect for which the network manager is crucial...but before all this please tell me if I should make a new thread for this?

Thanks

I have one ubuntu edgy 6.10 CD that I got from Canonical. Can I use that to install network manager? If yes, how?

---

### Post by annda on 2007-03-14
definitely post a new thread, since it's no longer an X problem. link back to this thread, too, so that people can get the background.

post as much info on your hardware (exact models of the modem and router??? - i think it's a WiFi card). describe how you got it working in the first place and what you are trying to do to get it working again. i don't know much about wireless cards, so i can't help you with that.

---

### Post by kristalsoldier on 2007-03-14
OK. Will do. Thanks again for all your help...all you folks!

---

