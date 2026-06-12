---
title: "broken xserver-xorg"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by chick penguin on 2007-01-16
About four months ago as an experiment, I installed Dapper on an old computer to see if I would be able to migrate to a linux system. From a magazine I had purchased I followed the excellent, clear and simple step by step instructions and successfully installed Dapper.

I found this forum and thanks to many of the posters here I was able to get the system up and working to my satisfaction. I installed the scanner and printer and the internet worked flawlessly. I have been enjoying the system.

I had to install Dapper in safe mode as it would not install directly from the live CD. 

The only problem I was having was trying to change the monitor resolution. It is a flat screen and I only had 800 x 600 and I wanted to change it to 1280 x 1024  60Hz. 

I found the command in this forum:
sudo dpkg-reconfigure -phigh xserver-xorg.

This command worked on another old box on which I have installed Dapper and it too has the same flat screen. But did not work on this machine that I am having problems with.

Then newbie that I am I tried:
dpkg-reconfigure xserver-xorg and that did not work either, but then I did not understand all of the options and took all the defaults as I had read in one of the postings that I had found a while back. That did not work. Then I tried selecting vesa. No luck.

Now the inevitable has happened to the newbie who tries to work with the comand line and hasn't got a clue what they are doing. I have no graphical interface at all from which to work. The message on the screen reads:
Analogue out of range 35.5 / 87 HZ. 

Will I have to reinstall Dapper?

Thanks to the many people here who have helped me learn about linux and Dapper. I appreciate all posters who take the time to share your knowledge and experience. Through those messages I have been able to overcome my fear of the command line only to find the fear realized, that is, that I would ruin what I am trying to adjust. 

In all fairness I would have to have a better machine than this old box to be able to evaluate whether I would be able to work successfully in linux. It will take lots more work from me to get to be productive. 

I have gone through all the treads on monitor resolution and have check other sites as well but I have not been able to find an answer to my question and so here I am with my first post and my first question.

Thanks for any help you may be able to provide. I am a beginner and any info will have to be simple, clear and step by step because I really am unfamiliar with the system.

---

### Post by bodhi.zazen on 2007-01-16
1. Is there not a back up in /etc/X11 you can restore ?

2. If not, fall back to ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

3. Post your xorg.conf when you are up and running. Most likely you need to add hroizontal and vertical refresh rates for your monitor.

Oh I almost forgot, 

Video card ?

Do you know your monitor's specifications ?

---

### Post by floke on 2007-01-16
Have you tried your first CLI again - i.e. sudo dpkg-reconfigure -phigh xserver.xorg  ?

You could also try sudo startx (to see if this gets anything going)

And you could also try : sudo nano /etc/X11/xorg.conf

This will open up the xorg.conf file for you to edit manually

If these don;t work then I would then try them by booting up in a failsafe mode.

Not sure how useful any of this will be, but at least it will narrow down the list of possible solutions ;) 

Good luck

---

### Post by ljpm on 2007-01-16
Sounds like you buggered your xorg.conf file. Did you make a backup? if you did then copy the back up into the xorg.conf file from the command promp. I learned this one the hard way. ](*,) 

```
sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```

If you didn't make a back up then run 

```
sudo dpkg-reconfigure xserver-xorg
```

But this time make sure you enter the hscan and vscan ranges for your monitor. Hopefully this will solve both problems by resetting your xorg.conf giving you your GUI back and the hscan and vscan ranges should allow you a higher res on your monitor.


Oops, bodhi.zazen posed while I was typing.

---

### Post by chick penguin on 2007-01-16
1. Is there not a back up in /etc/X11 you can restore ?

>>I don't know, is there a way that I could look at that file folder without having any access to the program. I do not get past that analogue message. I do not know how to get into the program with a graphical interface. 

2. If not, fall back to 
Code:

sudo dpkg-reconfigure -phigh xserver-xorg
3. Post your xorg.conf when you are up and running. Most likely you need to add hroizontal and vertical refresh rates for your monitor.

>>I will try it again if I ever find a terminal or consol again!

Oh I almost forgot, 

Video card ?

>> hmm, good question. Not sure. Old system and can't remember.

Do you know your monitor's specifications ?

>> it is a 19inch LG Flatron L1920P purchased last year. Its default resolution is suppose to be 1280 x 1024 60 Hz.  
When I tried to go through the dialogue boxes in the reconfigure sequence. I did not know how to eliminate the resolutions that I did not want Dapper to select. I think what has happened is that the highest setting has been taken by Dapper and that is what has konked out my interface. Not Dappers fault I just don't know how to not select.

---

### Post by chick penguin on 2007-01-16
Did you make a backup? if you did then copy the back up into the xorg.conf file from the command promp. I learned this one the hard way.  

>>I tried to but I am not sure. Lets guess that I did it incorrectly and that it is not there. If I did have it I would not know how to copy it using the command line. We are talking real newbie here.


Code:

sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf
If you didn't make a back up then run 

>>I would try this if I know how to get a consol but I don't know. And I do not know how to get to safe mode either. 


Code:

sudo dpkg-reconfigure xserver-xorg
But this time make sure you enter the hscan and vscan ranges for your monitor. Hopefully this will solve both problems by resetting your xorg.conf giving you your GUI back and the hscan and vscan ranges should allow you a higher res on your monitor.


>>I will try to find that info in my specs and put that in if I ever find that I can get to the reconfgure dialogue again.
thanks

---

### Post by bodhi.zazen on 2007-01-16
Well, re-install will be faster for you, but you will not learn as much :p

When you boot, once X crashes you are at tty1, or the CLI (command line interface)

If not, Ctrl-Alt-F1 (Ctrl-Alt-F7 will return you to your GUI if we get X restarted).

OK, 

```
cd /etc/X11
ls -l | grep xorg
```

The last command will list all your potential back up candidates.

To use one:

```
sudo cp xorg.conf.xyz xorg.conf
```

Re-start X:```
sudo /etc/init.d/gdm restart
```

If that fails, try another :p

If that fails,```
sudo dpkg-reconfigure -phigh xserver-xorg
```

for sepcs on your monitor , google search :p

---

### Post by chick penguin on 2007-01-16
@bodhi-zazen
thank you
Well, re-install will be faster for you, but you will not learn as much 

>>I would really like to be able to fix this if possible withou reinstalling, that is the fast and easy way, as yes, I would like to learn to do this if possible. 

When you boot, once X crashes you are at tty1, or the CLI (command line interface)

The Ubuntu splash screen show what is loading and instead of the dialogue box for the username and password, the program puts up a dialogue box  saying
analogue out of range
35.5 / 87 Hz.

that is as far as I can get. 

thanks

---

### Post by bodhi.zazen on 2007-01-16
> **chick penguin said:**
> @bodhi-zazen
thank you
Well, re-install will be faster for you, but you will not learn as much 

>>I would really like to be able to fix this if possible withou reinstalling, that is the fast and easy way, as yes, I would like to learn to do this if possible. 

When you boot, once X crashes you are at tty1, or the CLI (command line interface)

The Ubuntu splash screen show what is loading and instead of the dialogue box for the username and password, the program puts up a dialogue box  saying
analogue out of range
35.5 / 87 Hz.

that is as far as I can get. 

thanks

LOL, well hat's off to you then. Fixing X is a very handy skill set indeed :)

Hit Ctrl-alt-F1 to get to tty1

You may need to log in, use your user name and PW

You should probably kill X before your configre:

```
sudo /etc/init.d/gdm stop
```

---

### Post by chick penguin on 2007-01-16
@bodhi-zazen

Hit Ctrl-alt-F1 to get to tty1

You may need to log in, use your user name and PW

>>I cannot log in the gui is not there to log in to, that is when the program puts up the analogue dialogue box. "not in range".

How do I get to a console if I cannot log in?

when I hit Contrl-alt-F1 nothing happens because I am not in a place in the computer program where that command would work.

---

### Post by bodhi.zazen on 2007-01-16
Ouch. Ctrl-Alt-F1 (that is the "F1" or function key) should bring up a black screen with a command prompt.

Will sometimes tty1 does not work so try tty2, tty3, etc up to tty6

tty2 = Ctrl-Alt-F2
ty3 = ctrl-Alt-F3

... Ctrl-alt-F6

It that fails, you can try to boot to the Oh, what is it called, the restore mode ? rexcue mode ? sorry cat has my tongue ...

That system restore option in on the grub menu will log you in as root :) The try to reconfigure X

As root you may enter commands without sudo :)

---

### Post by chick penguin on 2007-01-16
[QUOTE=bodhi.zazen;2023480]Ouch. Ctrl-Alt-F1 (that is the "F1" or function key) should bring up a black screen with a command prompt.

Will sometimes tty1 does not work so try tty2, tty3, etc up to tty6

>>>Somehow I managed to get to the tty2 but I got there and I used the 
sudo dpkg-reconfiguire xserver-xorg and did my best to answer the questions. I come to the same place where it asks for the bit depth I choose 24 and then at the bottom of the dialogue box is the following message and I do not know what to type.

it says:
xserver-xorg posting warning:
overwriting possibly-customized configuration file;
backup in /etc/X11org.conf.20070116192659
then under that is
[login name] @ [computername]:~$

I do not know what to type in the command line.

I had gone through this before and this is where anything that I have done just goes down the drain.

Your help is greatly appreciated. Thankyou.

---

### Post by bodhi.zazen on 2007-01-16
Oh, don't worry about that "error message"

It is not a problem, it is telling you it made a back up is all ....

Well, lets start X and see what we have :;

```
sudo /etc/init.d/gdm restart
```

If that fails, try again with the -phigh flag:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That will select the default values for you with everything except screen resolution.

Select screen resolution with the keyboard up & down arrows, use the space bar to select.

It can sometimes help if you reduce your depth to 16 :D

Well, lets see what ya got !

---

### Post by chick penguin on 2007-01-16
[QUOTE=bodhi.zazen;

```
sudo /etc/init.d/gdm restart
```

>>When I tried this I get the message:
Failed to start the xserver. It is likely that it is not set up correctly. Would you like to view the xserver to diagnose the problem?

I selected  yes,

then to next screen which now says:

Do you want to view detailed exserver output as well?

I selected yes

Now I am back to the screen with:
Stopping Gnome Display Manager
Starting Gonome Display Manager
and then

[login name] @ [computername]:~$

....don't know what to type now.


Select screen resolution with the keyboard up & down arrows, use the space bar to select.

>>Thank you I did not know how to select with the space bar. merci

>>selected screen resolution  1280 x 1024

It can sometimes help if you reduce your depth to 16 :D

>>I did change the depth to 16

thank you for you patience

---

### Post by bodhi.zazen on 2007-01-17
So sorry you are still having trouble.

Looks like your last attempt to configure X

Try the -phigh flag,

---

### Post by floke on 2007-01-17
Hi

I have nothing useful to add except my support. 

Your persistence is much admired, and I am storing a copy of this thread in my gmail account in case I ever have a similar problem. It seems like there's lots of useful advice packed in here!

Good luck, and don't give up!

---

### Post by chick penguin on 2007-01-17
> **bodhi.zazen said:**
> So sorry you are still having trouble.

Looks like your last attempt to configure X

Try the -phigh flag,

and @SteveK

>>>I have not given up yet, I want to try to find out how to get into safe mode and try the commands and all the suggestions that have been given from there. I had to install Dapper on that machine in safe mode and maybe if I did the reconfigure from safe mode that might do the magic fix.

I have a bit of trouble with the keyboard as the Ctl+Alt+F1 keys etc do not take me to the tty1,2,3,etc. not sure why. but I get there by tapping around. 
 I also cannot see the command line at the bottom of the screen as half of it is cut off and I do not know if I have typed the command in without spelling errors. Anyway...
I am going to try to do some more searching on learning how to get to safe mode and entering grub. It is easy to wipe the disk and reinstall as a last resort. 
I have overcome my fear of the command line. And I have confidence in reinstalling which is the main thing and for me that is easy and not too time consuming. 
I have seen in the forum there is a manual for green beginners on using the command line. I will need to understand the logic of it and then maybe I will be able to use it with some basic skill. Right now it is just stumble stumble. I did read a good primer on it and will have to go back to it and buckle down. I sat for hundreds of hours to learn Windows and Photoshop and I am an intermediate user in that system and I expect it will take the same number of hundreds of hours for me to be productive in linux whatever distribution I finally end up in.
Thank you all for your kind help and encouragement. I appreciate it.

---

### Post by bodhi.zazen on 2007-01-17
Well, it could also be a hardware compatibility problem as well ...

Try a different computer and/or different version of Linux ...

---

### Post by chick penguin on 2007-01-17
[QUOTE=Steve.K;2022994]

And you could also try : sudo nano /etc/X11/xorg.conf

This will open up the xorg.conf file for you to edit manually

>>>Well I have tried the other commands recommended many times, and now I am in the /etc/X11/xorg.conf file. It is quite a list and I am not sure what to do exactly...edit manually. yikes

---

### Post by bodhi.zazen on 2007-01-17
LOL

Post it, lets take a look ...

---

### Post by chick penguin on 2007-01-17
> **bodhi.zazen said:**
> LOL

Post it, lets take a look ...

>>>post it? hmmm. I have no idea how to get that into a browser and into this forum. Its just a black screen with all the white writing. I am no where near a browser. It looks like a DOS window.

I exited it a second ago and then booted into safe mode via grub and selected recover mode from the list. Now, I am logged in as root. Even more dangerous. I do know how to type reboot and get out though. 

I could go back to the nano command I am sure.

---

### Post by bodhi.zazen on 2007-01-17
You can attach the file (look down when you post) ...

---

### Post by chick penguin on 2007-01-17
> **bodhi.zazen said:**
> You can attach the file (look down when you post) ...

>>>sorry for the misunderstanding, my fault,
I am typing this on the laptop, in ah, in Windows while I am working on the other machine. 
It now goes to tty2 and I am working from there with the commands.

My apologies for any misunderstanding. The fault is mine.
Thanks for your kind and patient help.

---

### Post by bodhi.zazen on 2007-01-17
Do you know how to copy /etc/X11/xorg.conf onto a flash drive and post from windows ?

```
mount /dev/sda1 /mnt
cp /etc/X11/xorg.conf /mnt
umount /mnt
```

Transfer to windows, pulg & post :p

---

### Post by chick penguin on 2007-01-17
[I]> **bodhi.zazen said:**
> Do you know how to copy /etc/X11/xorg.conf onto a flash drive and post from windows ?

```
mount /dev/sda1 /mnt
cp /etc/X11/xorg.conf /mnt
umount /mnt
```

Transfer to windows, pulg & post :p[/I]

>>>I will try, 
 I will plug in my pen drive to the USB and follow the commands you have posted

I will try this right after supper.
Thank you so much

---

### Post by chick penguin on 2007-01-17
[QUOTE=bodhi.zazen;2028067]

```
mount /dev/sda1 /mnt
cp /etc/X11/xorg.conf /mnt
umount /mnt
```

>>>I hope I copied it correctly. I see I did not type umount /mnt
I typed _un_mount   ah...so I took out the usb stick and hoped for the best...ah. I can always try again if it is corrupted.

---

### Post by chick penguin on 2007-01-17
[QUOTE=chick penguin;

>>>I hope I copied it correctly. I see I did not type umount /mnt
I typed _un_mount   ah...so I took out the usb stick and hoped for the best...ah. I can always try again if it is corrupted.[/QUOTE]

>>>I cannot see the attached file that I uploaded. 

I will try the copy paste: oh finally ....!

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"pc101"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. 210888GX [Mach64 GX]"
	Driver		"ati"
	BusID		"PCI:0:10:0"
EndSection

Section "Monitor"
	Identifier	"LG L1920P"
	Option		"DPMS"
	HorizSync	30-83,
	VertRefresh	56-75,
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 210888GX [Mach64 GX]"
	Monitor		"LG L1920P"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by bodhi.zazen on 2007-01-17
You did it :p

See, that was not so hard, and you learned a little about mount ;)

I don't know why, but there is only 1 "n" in umount :D

At any rate, try editing the file ....

You can do it on windows (with ?notepad or winpad), save the file as a text file not a .doc

put usb in your laptop and re-mount

Then cp /mnt/xorg.conf /etc/X11/xorg.conf

OK, now do you have a mouse with a scroll button ? A button to press down and get a click ?

If so,   > Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" **"false"**
EndSectionThat is no big deal however so if you are not sure you can leave it ....

Next, it appears you have an ati card. I am not as familiar with these so I trust you installed the ati driver ?

If not, see this thread:[http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320)

OK, now for the good stuff.

Make the bold changes:

> Section "Monitor"
Identifier "LG L1920P"
**# Specifications: [http://www.dealtime.com/xPF-LG-LGE-MONITOR-19-TFT-BLACK-SILVER~r-1~CLT-INTR~RFR-www.google.com](http://www.dealtime.com/xPF-LG-LGE-MONITOR-19-TFT-BLACK-SILVER~r-1~CLT-INTR~RFR-www.google.com)**
Option "DPMS"
HorizSync **30-83**
VertRefresh **56-75**
**Option         "UseEdidFreqs" "1"**
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. 210888GX [Mach64 GX]"
Monitor "LG L1920P"
DefaultDepth **24**
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280 x 1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280 x 1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

The # is a comment
# Sepcifications is a site I used to confirm your monitor settings and may be helpful to track in xorgconf, up to you ...

In the monitor section I removed a "." at the end of the HorizSync and VertRefresh lines (small edit)

You can reduce the color depth back to 16 later if needed ....

That should be it for editing

Put that in you linux box and re-start X

sudo /etc/init.d/gdm restart

If it works, back up xorg.conf and re-boot

If you get error messages, post them :(

---

### Post by chick penguin on 2007-01-17
[QUOTE=bodhi.zazen;2028772]

OK, now do you have a mouse with a scroll button ? A button to press down and get a click ?

>>>Yes a scroll mouse, Logitech optical 

Next, it appears you have an ati card. I am not as familiar with these so I trust you installed the ati driver ?

If not, see this thread:[http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320)

>>>No I have not installed the drivers as you might have guessed,  I took the defaults when I installed Dapper and it worked that way so I left it. But I will try to install the drivers if they have them available. It is a very old card and an old machine. Thank you for the thread I will follow it.
I think that is probably a bit part of the problem. 


Make the bold changes:

>>OK I will.


In the monitor section I removed a "." at the end of the HorizSync and VertRefresh lines (small edit)

>>>In the instructions when putting in the HorizSync VertRefresh numbers it says to put a comma at the end of the last number. If I don't then it in then  a dialogue box comes up and instructs that that comma be put in. It will not accept the numbers without the comma.

You can reduce the color depth back to 16 later if needed ....

>>>OK.

That should be it for editing

Put that in you linux box and re-start X

>>>Thank you so much. I will try this first thing in the morning. 
I appreciate your help.

---

### Post by chick penguin on 2007-01-18
[QUOTE=bodhi.zazen;2028772]

Then cp /mnt/xorg.conf /etc/X11/xorg.conf

>>>When I tried this command it said it did not have a destination.

Next, it appears you have an ati card. I am not as familiar with these so I trust you installed the ati driver ?

>>>yes I found instructions how to do that and it was successful install
but it failed to give me any results.


I even tried editing the config file directly. Managed that in sudo with nano in tty2. 
I tried a number of things but no luck.

Will reinstall Dapper on that machine.
Thank you for all your help.
Much appreciated.
And I learned a great deal by doing.

---

### Post by bodhi.zazen on 2007-01-18
Ack ....

It seems you are a short edit (of xorg.conf) away :p

Good luck and I am glad you at least learned a little.

---

### Post by chick penguin on 2007-01-18
Is there a difference in doing the changes from sudo or root?
In other words, when I edit the config file in sudo is that the same
file I would be editing if I were logged in as root?

I am also curious as to why there is a comma required after the Horizontial and Vertical numbers when it is done via sudo and the graphical interface and there would not be any comma if it were just the config file itself?

Lots of mystery as to why these commands don't work.

I sure enjoyed going out on sudo apt-get for the ati drivers. Was that fast. Very nice. I think that aptitiude is suppose to be better according to my reading.

I might try again tomorrow with a few more hints. A short edit eh?hmmm



[QUOTE=bodhi.zazen;2032672]Ack ....

It seems you are a short edit (of xorg.conf) away :p

---

### Post by bodhi.zazen on 2007-01-19
> **chick penguin said:**
> Is there a difference in doing the changes from sudo or root?
In other words, when I edit the config file in sudo is that the same
file I would be editing if I were logged in as root?

Yes, sudo = root

You can also sudo su or sudo -i to change to root :p

> I am also curious as to why there is a comma required after the Horizontial and Vertical numbers when it is done via sudo and the graphical interface and there would not be any comma if it were just the config file itself?

Yea, that was a new one on me too :)

> Lots of mystery as to why these commands don't work.

I sure enjoyed going out on sudo apt-get for the ati drivers. Was that fast. Very nice. I think that aptitiude is suppose to be better according to my reading.

I might try again tomorrow with a few more hints. A short edit eh?hmmm

Oi

Yes the things in post after reviewing your xorg.conf, the things in bold, 

well they might work.

And it was only a few things ...

And you have those ATI drivers :p

You have come so far :D

Well good luck ...

---

### Post by chick penguin on 2007-01-19
>>>Interesting way to change user to root, thanks. 

[QUOTE=bodhi.zazen;2033947]Yes, sudo = root

You can also sudo su or sudo -i to change to root :p

Yes the things in post after reviewing your xorg.conf, the things in bold, 

well they might work.

>>>I did try it but it didn't work. But then I took out the commas as per.
I could try putting them back in.

Does the command
sudo /etc/init.d/gdm restart
do the same type of job as
sudo shutdown -r now?
or CTR+ALT+Backspace, this is the command I used when
I change the resolution on the other linux ubuntu machine. Worked like a snap.

I didn't get it right in copying the file from the stick drive to the file
so I found out how to use nano to edit it directly using the changes in bold that you suggested.

I am getting so I could do this almost without looking at my notes. Its all very good and well but I sure wish I could get the thing working.
I reinstalled the xserver with sudo apt-get install --reinstall xserver-xorg.
Somehow it seemed like it wasn't there. 
At first it couldn't find the package but after I installed the atidrivers it went in.
hummm...

---

### Post by bodhi.zazen on 2007-01-19
sudo /etc/init.d/gdm restart = Ctrl-Alt-Backspace

Logs you out and re-starts X (at gdm, the graphical log in screen).

sudo shutdown -r now = Power Button :p

shutdown -h now is much more graceful and kind to you HD though :p

Sure, try the commas, can't hurt ....

What happens if you type:

```
startx
```

If that works you should get a gray screen with a black X that moves with the mouse.

Ctrl-Alt-Backspace to exit ;)

Error message ??

Might point us in the right direction ...

---

### Post by chick penguin on 2007-01-19
Going to try this tomorrow,
thank you for sharing your knowledge and expertise.
I am enjoying learning this. I am beginning to see the terminal window as a powerful tool that it is. Very flexible compared to a standard gui.




> **bodhi.zazen said:**
> sudo /etc/init.d/gdm restart = Ctrl-Alt-Backspace

Logs you out and re-starts X (at gdm, the graphical log in screen).

sudo shutdown -r now = Power Button :p

shutdown -h now is much more graceful and kind to you HD though :p

Sure, try the commas, can't hurt ....

What happens if you type:

```
startx
```

If that works you should get a gray screen with a black X that moves with the mouse.

Ctrl-Alt-Backspace to exit ;)

Error message ??

Might point us in the right direction ...

---

### Post by chick penguin on 2007-01-20
some time today to retry a few of these commands.

have tried to reconfigure and now I have and error message:
Ati drivers can't support depth 24
Screens found but none have useable configurations

Fatal Server Error
No screens found
XI0 Fatal IO error 104

=====
I also tried depth 16 and that didn't work.

---

### Post by chick penguin on 2007-01-20
[QUOTE=chick penguin

have tried to reconfigure and now I have and error message:
Ati drivers can't support depth 24

>>>So I tried vesa from the list and voila. Back in to graphical interface.
Ubuntu is up and running.
Still only have 800 x 600

sometime  I will have to try
 
sudo dpkg-reconfigure -phigh xserver-xorg
which worked on my other machine.

but not right now. had enough fun for one week end.

thanks for all the help
greatly appreciated
..A reincarnated penguinhttp://ubuntuforums.org/images/smilies/icon_smile.gif

---

### Post by rocknrolf77 on 2007-01-20
Have you visited [www.albertomilone.com](www.albertomilone.com)  (one of the forum staff, who has made a super script to install graphics driver?) :guitar:  ON

---

### Post by chick penguin on 2007-01-21
> **rocknrolf77 said:**
> Have you visited [www.albertomilone.com](www.albertomilone.com)  (one of the forum staff, who has made a super script to install graphics driver?) :guitar:  ON

>>>>well, I guess I did via find this in another post on installing the ati drivers

I found this and followed the instructions:

To install the ATI driver - type these commands:

sudo aptitude install  xorg-driver-fglrx 

sudo aticonfig --initial 

sudo aticonfig --overlay-type=Xv 

>>>>>What I did not do is to do this part in the conf file. Maybe that is why the ati drivers did not work as per the message I got.

Then open your /etc/X11/xorg.conf

sudo nano -w /etc/X11/xorg.conf

and add the following lines to the end of the file:

Section "Extensions"
   Option "Composite" "Disable"
EndSection

>>>>Thank you for the link. I will have to try this whole exercise over again next week.

---

### Post by chick penguin on 2007-01-21
Also my card is very old
Device "ATI Technologies, Inc. 210888GX [Mach64 GX]"

and so is the whole machine.

---

