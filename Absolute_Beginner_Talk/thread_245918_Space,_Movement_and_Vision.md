---
title: "Space, Movement and Vision????"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by John Murphy on 2006-08-28
Sounds like a 3D Discussion don't it????

Here are the issues - Aout a year ago I had SuSE 9.3 loaded for a couple of months with KDE...... couldn't configure a few things out so eventually thrashed the install altogether.

At first glance I was completely wowed by the Drake and a first venture into Gnomlandia - However I have exactly the same issues once more.

1) I installed on a 12.5 Gb Partition (Huge I would think for this distro) following on from the recommendations for SuSE initially. To date I have instlalled aMSN/Skype/Azureus a 3D App and copied over about a 2Gb Torrent folder from WindAss and am told i have low disk space???? What the F (-ree Mother Nature????)? At my reckoning 1 install CD  = 750 Mb + 2 comms Apps - maybe 80Mb, 3D prog 500Mb (including Documantation etc) and maybe some updates. Also installed are Alien and Automatix - so where have practically 10Gb vanished to???? Had similar issues with SuSE also

2) Yes, the mouse! The mouse! The same old ground - why even a year on have the linux community still not come up with a default driver for the MicroCrass Optical InteliMouse 5-button? A lot (and I mean a lot) of people have this. It should install by default and be configured properly.
My 3D apps are virtually useless at the moment and cannot be mouse mapped it seems. I spent about a month trying to fix tis issue last year with xorg,conf/IMwheel etc etc etc. scripted it to configure on boot etc......... never worked!!! I have a lot of issues with the mouse in linux - even trying to drag/scale or move native windows etc. Miss slightly and they vanish altogether

3) The Webcam - I thought that this time round - yes!!!! but wrong!!! I have a GE Type webcam that used to crash KDE if not configured - and there was no driver and could not be scripted like the mouse..... In Grnome the light comes on - the Desktop don't crash ut still there's noone home.

I came back to Linux largely for issues related to connectivity - Microsoft crippled my Internet connection an the OS in General with recent Automatic Updates. SuSe never did configure my Cable Modem Connection properly and it was time consuming and at times a nightmare trying to figure it out. YaST and Sax never could seemingly fix any of these issues. I hated the amount of messing around you needed to do in x-Server. At one stage I lost the kernel after aout 6 weeks of stability as a result of tring to confiure all these and instead of desiring to do a further 6 weeks of scripting to try ad restore the kernel in orer to re-adress and reconfigure above mentioned the fastest and better solution was a re-install.

Am grateful that the drake at least givesmy my internet connection every time- someprogress here at least. I still think Linux has a long way to go regarding peripherals among other issues.With a it of luck I will have a Mac in the next few weeks which I will elect as my no 1 to I will need to hopefully port whatever graphics packages I can. Will then have to enquire in Adoeif it's possible to download my Graphics Package CS in Mac form and transfer the licence. Same for other apps.

I think the Drake will in time become my #2

As for that other heap of Sh(elly Winters)- well I couldn't put it any better than Mr. Bill hinself 'Hasta La **Vista** baby!'

---

### Post by Crosbie on 2006-08-28
1.) What does System > Administration > Disks tell you about your partitions?  Possibly you've filled up your root partition and have space on your /home partiton, for example, if it's set up that way.  Btw, the 750-800mb CD is compressed - it'll expand much bigger than that in situ.

2 and 3.) Hassle the manufacturers to support Linux. :)  Sorry.  Maybe someone else can help with those?

EDIT:  [url=http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons]
This[/url] might be a good lead to get you going with the mouse... looks like hard work but just might do the trick.

---

### Post by John Murphy on 2006-08-28
Heya - Granted I took into account the live cd would be compressed - which makes what I'm seeing all the more scary

I installed on a classic Swap 2 / hde root system giving 750Mb to the Swap ans 12.2 Gb to the root

Right now I'm looking ar 267.77 Mb free. That would seem to suggest that Dapper installation with it's updates and package updates have accounted for 10Gb in only 2 days running. I thought Linux was supposed to be to run full version on a fraction of this space - seems like I nees to buy a few terrabytes to store a couple of Jpegs......... Nasty!!!!

Thats a monster even compared to WindAss Ex-Pee........

There is no disc clean up utility or temp file cleaner to speak of by any chance????

Thanks for the other tip about the mouse but looks like it'll be the same routine all over.... As for telling the Manufacturenrs anything. I'm clean out of words as far as they go - even curse words!!! I thought all this open source stuff was hack territory - so how come our friends in the Orphan Sauce Community haven't managed these great feats of computornic Re-engineering thus far to suit unhaopy Linux Boxes all over the place????? Sauce might be clue as to why not alright Lol!!!

---

### Post by jimrz on 2006-08-28
do not have a webcam...no help here

12.5Gb seems a bit small...but should suffice. What all have you added?

I have a 5 button MS intellimouse...not hard to set up...here is the appropriate section of my xorg.conf:

```
Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
  EndSection
```

works perfectly...you can copy and paste into yours (sudo required). be sure to make a backup of your current conf FIRST

---

### Post by John Murphy on 2006-08-29
Thanks both for the pointers but now I'm more reluctant than ever - this is exactly the same procedure that I spent months trying to crack last year and ended up destroying the kernel as my fsta file got messed up among others.

can I actually access X in Gnome???? How to????

Some things ae a lot different than in KDEon SuSE

I'm not kidding when I say I must have a book of printouts from trying to get this wretched mouse working last year.

Never got the autostart procedure to work - and it's one thing getting all 5 buttons recognized and functional but then you have to map the right behaviors to them. Maya is practically useless right now as the alt + mouse button event is non evistent. Therefore you cannot Tuble Track or Dolly - better off buying a few cases of beer and going fishing! (Well that goes without saying anyway........)

Well here's to nothing - maybe I'll do something wrong this time and actually get it to work right. Much as I hate EX-Pee and all things Micro$ucks and WindA$$ they certainly got peripheral installatios right. None of these weeks and months of sleeplessness trying to get little issues like this sorted out!

---

### Post by John Murphy on 2006-08-29
Wunderbar 

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons)

My reluctance is already becoming my impatience......

Downloaded evdev-key-btn-test.c - then discoered I had to instal G++ to try compile it (try being the operative word here)

Terminal Message:

jammer@philmore:~/Desktop/devkey$ gcc -o evdev-key-btn-test.c
gcc: no input files

.....going great so far, eh????

I scroll down to the link for The SuSe 9.3 rpm (to try convert that to a .deb) - The link don't work 

------Strike 2!!!

jack@BlackPearl:~/Desktop/devkey$ gcc -o evdev-key-btn-test.c
gcc: no input files

I got the driver okay at....

[https://bugs.freedesktop.org/attachment.cgi?id=1745](https://bugs.freedesktop.org/attachment.cgi?id=1745)

Nowhere's the amazing bit - it seems I need the x.Org SDK to compile it and guess what???

Nowhere to be seen - Not in Synaptic or anywhere else for that matter

Strike 3!!!

I'm outta here for now to get a chinese meal or something - this really doesn't look like it's ever gonna happen. 
Little pieces of the puzzle and no way to patch them all together.
This is why I doubt any Linux distro is likely to become my No.1 desktop anytime soon......


Stressful business this Lol........

---

### Post by John Murphy on 2006-08-29
Here it is - and a completely different - much shorter procedure than the geek version!


I found this link and it rocks - tailored to Ubuntu and you can install just about anything withot weeks of stress y the looks of it!

[Link](http://ubuntuguide.org/wiki/Dapper)

**_[size=3]To  Configure Ubuntu for multi-button Mouse[/size]_**

**Activate side-mouse-buttons in FireFox**

Just add two lines to xorg.conf will activate side-mouse-buttons in FireFox. This should work with most 5-button mouse. Here is a list of mice that worked with this instruction.

Logitech MX510
Logitech MX518

**Backup Gnome configuration file**

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

**Modify the Gnome configuration file**

```
gksudo gedit /etc/X11/xorg.conf
```

Find the Input Device section for your mouse and add two lines as shown below. You may also increase the number of buttons if your mouse has more than 7, just fix the rest of the section based upon the number of buttons (remember back/forward, wheel click & tilt left/right all count as buttons)

Change:

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	...
	Option "Protocol" "ExplorerPS/2"
	...
	Option "Emulate3Buttons"       "true"
EndSection

to:

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	...
	Option "Protocol" "ExplorerPS/2"
	...
	Option "Emulate3Buttons"       "true"
	Option "Buttons" "7"
 	Option "ButtonMapping" "1 2 3 6 7"
EndSection


At this point you can reboot your computer or reboot Gnome (Ctrl-Alt-BackSpace) to see if your forward/back buttons work in FireFox. They still won't work in Nautilus yet until you install the imwheel dameon.


[b/_Install & Configure IMWheel_[/b]

   ** * Install IMWheel **

```
sudo apt-get install imwheel
```

   ** * Modify IMWheel configuration file **

```
gksudo gedit /etc/X11/imwheel/imwheelrc
```

    * Insert the following at the bottom of this existing file 

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right 

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right


   ** * Create IMWheel start-up script **

```

sudo mkdir /home/login
gksudo gedit /home/login/mouse
```

    *** Insert the following into this new file **

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

    *** Grant execution for everyone to this new script **

```
sudo chmod +x /home/login/mouse
```

    * Configure this script to be executed at start-up
         1. Select 'System' > 'Preferences' > 'Sessions'
         2. Click the StartUp tab
         3. Click Add, then input: /home/login/mouse
         4. Click OK, then Close 

    * Reboot your computer or your Gnome environment and then test your back/forward mouse buttons in Nautilus

---

