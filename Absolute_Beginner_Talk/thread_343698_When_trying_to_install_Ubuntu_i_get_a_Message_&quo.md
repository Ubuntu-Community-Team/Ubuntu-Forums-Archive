---
title: "When trying to install Ubuntu i get a Message &quot;Failed to start the X Server&quot;"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Laxton14 on 2007-01-21
When trying to run/install Ubuntu 6.10, I hit enter when the boot screen comes up and it says a few white lines and then a white screen comes up that says 

"Failed to start the X Server(your graphical interface). It is likely that it is not set up correctly. would you like to view the X server output to diagnose the problem?  " 
I hit yes and it says...

Blah blah for a few lines then
(--)probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II)informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) log file: "/var/log/Xorg.0.log", Time: Sun Jan 21 21:14:20 2007
(==) Using config file: "/etc/X11/xorg.conf"




I am running a Dell Dimension 2400 With:
Pentium(R) 4 CPU 2.20GHz
640MB Ram
ATI Radeon 9250 Graphics Card

When Responding, please keep in mind that i am an absolute noob at linux and programming and everything, please make your responses as simple as possible

---

### Post by Bachstelze on 2007-01-21
Have you tried running the installer in the "safe graphics mode" ? You should have that option in the very first screen after your computer boots. If it stil doesn't work, try using an Alternate CD.

---

### Post by mikewhatever on 2007-01-21
You may want to study this page [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
I know it looks scary, but the instructions are very detailed, and after reading it a few times, you get the idea.:D

---

### Post by bladeless on 2007-01-21
I've actually run into the same problem quite often...  X, for some reason, when it comes to ubuntu, has a problem with ATI video cards.  This may or may not be a fix to your install problem.  Here's how to fix it.

Copy the info between the lines into a file named xorg.conf and put onto a floppy.  After that, run Ubuntu, it will probably fail again to init 3.  You will have to copy this xorg.conf and replace it with the current xorg.conf.  To do this run the following commands.

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo mkdir /mnt/floppy
sudo mount /dev/fd0 /mnt/floppy
sudo cp /mnt/floppy/xorg.conf /etc/X11/xorg.conf
startx

Here is the proper xorg.conf file
-------------------------------------------------
# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "Monitor"

 ### Comment all HorizSync and VertSync values to use DDC:
	Identifier   "Monitor0"
	ModelName    "Samsung SyncMaster 150N/152N/153N"
 ### Comment all HorizSync and VertSync values to use DDC:
	HorizSync    30.0 - 61.0
	VertRefresh  56.0 - 75.0
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "radeon"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

------------------------------------------------------------------------------------

This should work, it's how I got mine to work.

---

### Post by Laxton14 on 2007-01-22
Thanks guys, with your help i got ubuntu installed and its working great.

---

### Post by heyilikeyoursweater on 2007-01-22
Hey, I am having the same problem, but my situation is a little different. First, I don't have a floppy drive, but I do have a flash drive. Can I install the file from there? and second: I don't know where to type the commands into the unix terminal. Am I supposed to be able to do it after I exit looking at all the errors? After I exit the errors, it brings up a command type thing, which I can type into, but when I hit enter, I doesn't do anything. Sorry if this is a dumb question...

---

### Post by corvolt on 2007-01-22
I have the exact same problem (with an ATI Radeon X600 256MB graphics card) but I don't have a floppy drive - I have a flashdrive, though.

I don't know what to change "floppy" to in your code, bladeless. Please, if anyone could help me.. :/

---

### Post by rocknrolf77 on 2007-01-22
Have a look here : [www.ubuntuguide.org](www.ubuntuguide.org)

And here            : [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

This should get you started. :)

---

### Post by AndyCooll on 2007-01-22
> **corvolt said:**
> I have the exact same problem (with an ATI Radeon X600 256MB graphics card) but I don't have a floppy drive - I have a flashdrive, though.

I don't know what to change "floppy" to in your code, bladeless. Please, if anyone could help me.. :/

You don't actually need to do that bit. bladeless is being extremely cautious and telling you to back up that file to a floppy. I personally wouldn't bother doing that. This is a sufficient backup of the file IMHO:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

If his notes don't work you can always try:
```
sudo dpkg-reconfigure xserver-xorg
```
And when you get to the graphics driver bit select "vesa". It's a basic bog standard driver that will work with almost everything and at the very least get you up and running with a gui. You can always play around trying to get more specific drivers working later.

:cool:

---

### Post by heyilikeyoursweater on 2007-01-22
Yes, but *where* do I type it at?????

---

### Post by corvolt on 2007-01-22
I don't understand when to paste those commands. After the error screen comes up and I push 'esc' and get rid of it, all I have is a blank black screen - no matter what I type, absolutely nothing happens at all.

---

### Post by heyilikeyoursweater on 2007-01-22
yes, I have the same problem
c'mon someone should help us!

---

### Post by heyilikeyoursweater on 2007-01-22
Well, I guess we have been abandoned. So much for the Ubuntu Forums...

---

### Post by corvolt on 2007-01-22
I'm sure someone will help us out eventually - not everyone is at our beck and call..

---

### Post by mikewhatever on 2007-01-22
Hitting ESC (several times if needed) should present a list of options. The recovery console is the one you want.

Edit:Text Mode should be the option. Sorry, I got it confused with Windows RC.

---

### Post by corvolt on 2007-01-22
When do you hit ESC? I pushed it during the list ("Start/Install Ubuntu", "Safe Graphics Mode" etc) and when I entered that line, it said it couldn't read sudo, dpkg or reconfigure/configure.

I'm really not this stupid, but I'm absolutely stumped.

---

### Post by Happy_Man on 2007-01-22
You're all lucky: I had this same problem (I think) :p 

Try to boot Ubuntu as you always would, and get through all the error messages. DON'T PRESS ESCAPE. Eventually, you should get to a text login screen. Login, and then enter all the commands pasted above. And while you're at it, install Lynx to make your life easier. It's a text-based internet browser that helps a lot in these situations.

```
sudo apt-get install lynx
```

---

### Post by corvolt on 2007-01-22
Instead of waiting, I finished exiting the error screens and all that sh*t, and then I pushed alt+f1 out of frustration - that brought up the log for me, and let me change settings for my monitor.

Alas, it still doesn't work, ahha.

I'm just giving up.. this is way too frustrating.

---

### Post by chalex on 2007-01-22
> **heyilikeyoursweater said:**
> Yes, but *where* do I type it at?????

You can hit Ctrl-Alt-F1 to switch to the first console.  Or  Ctrl-Alt-F2 to switch to the second.  Ctrl-Alt-F7 gets you to the graphical interface.  I'm not sure how many consoles are enabled by default in the LiveCD.

---

### Post by chick penguin on 2007-01-22
Thanks for the link. Excellent guide along with many threads throughout the forum.


> **mikewhatever said:**
> You may want to study this page [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
I know it looks scary, but the instructions are very detailed, and after reading it a few times, you get the idea.:D

---

### Post by corvolt on 2007-01-23
Alright, a small update, but still problems :/

I changed my graphics driver to "vesa" via the list, but now instead of the error screen, it goes to a blank screen that says nothing but when I push keys (such as 'esc', it shows up as '^[' and jibberish for every key - except for ctrl+alt+delete, which reboots it (as if you didn't know, lol)

Sigh, okay, I read that page again and didn't realize the "startx" command was available. however, even after changing my driver to "vesa", it still goes to the same ugly black screen that doesn't let me do anything...

if I push 'esc' when the Ubuntu screen comes up, it takes me to a screen where each line begins with "root" - is there a way I can change things from there?

---

### Post by bramp on 2007-01-25
> **mikewhatever said:**
> You may want to study this page [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
I know it looks scary, but the instructions are very detailed, and after reading it a few times, you get the idea.:D


nah it's not scary I can follow instructions :guitar: 

but I am too, still having the problem, Failed to Start X server,

vesa cannot start v_bios

it says monitors were found but not with usable configurations?

I have my own thread here.

[http://www.ubuntuforums.org/showthread.php?p=2046714#post2046714](http://www.ubuntuforums.org/showthread.php?p=2046714#post2046714)

I would also like to point out that I am using 2 video cards with 4 CTR monitors 2 15inchers and 2 17inchers

---

