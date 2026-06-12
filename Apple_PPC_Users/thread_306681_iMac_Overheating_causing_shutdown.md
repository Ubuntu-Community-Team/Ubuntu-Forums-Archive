---
title: "iMac Overheating causing shutdown"
date: 2006-11-25
forum: Apple PPC Users
---

### Post by Radiolad on 2006-11-25
Hi, My iMac G3 400Mhz 'Graphite' PPC works just great on Ubuntu Dapper and with Forum members' assistance I can also access the Web on it.       **One small problem** ! After approx 90 minutes it just shuts down regardless of the fact that I am actually working on it i.e the power/sleep mode has not timed in.  I am wondering if it is to do with overheating?  I am running the ADSL modem from a powered external USB hub to avoid using the iMac internal power supply.  I have even raised the iMac approx 4cms from the desk on 'feet' in order to improve air circulation underneath it.

Has anyone experienced this problem? Is it more that a heat problem?    Any advice would be welcome.
  Regards  Radiolad  (UK)    :-k

---

### Post by stream303 on 2006-11-25
I'd run **top** in a terminal to see if it finds any processes hogging the cpu.

Perhaps right click on the top bar and add the cpu frequency-scaling applet to see if your iMac is always running at full speed all the time.

Now that Ubuntu is installed, I'd be tempted to install the XFCE4 desktop and see if that makes a difference in the meantime..

---

### Post by Torrance on 2006-11-25
Frequency scaling would be your best bet to test if it is indeed a heat problem.

I have heard of reports of G5s (I think Quad Core) also shutting down unexpectedly - and this turned out to be due to overheating. Though in that case, they had to do a CPU-intensive task for a couple of minutes.

---

### Post by Radiolad on 2006-11-25
Hiya, Thankyou both for your replies. What is a '**CPU-intensive task**'?    Cheers Radiolad.

---

### Post by Radiolad on 2006-11-25
Hiya, I've been Googling around and found this link to a whole bunch of people having overheating probs on various computers:
[https://launchpad.net/distros/ubuntu/+bug/22336](https://launchpad.net/distros/ubuntu/+bug/22336)
Seems the problem has been going on for months. Is it not possible for the folks in development for Dapper to get this prioritised before our 'chips' are fried!!  Radiolad

---

### Post by stmiller on 2006-11-25
Do you have powernowd installed? And what kernel? (What is the output of uname -a )

---

### Post by Radiolad on 2006-11-26
> **stmiller said:**
> Do you have powernowd installed? And what kernel? (What is the output of uname -a )

Hi, As a newbie all I can tell you is Ubuntu was installed as the sole OS on the iMac. I used the free LiveCD for MAC and is version 6.06.1  Nothing else has been added or removed. I would be grateful if you would give me an 'idiot guide' in order for me to check what you have asked.
The iMac being convection cooled is very clean inside, at least from what I can see through the clear case from the top. Would a removal of the base for a *delicate *spring clean be advisable?
   Thanks, Radiolad (UK)

---

### Post by RHTopics on 2006-11-29
Radiolad,

I also have a problem with an iMac that I believe is heat related.

It is an iMac G3 350MHz with Dapper 6.06.1 installed on it.  I have not experienced a complete shutdown.  Instead I have experienced losing access to the hard drive followed by a lockup.  Pressing the reset button on the side of the iMac was required to get it to shutdown inorder to get it restarted.

My problem occurred after several hours of use during hot weather when the temperature in the house was in the low 80s ( Fahrenheit ).  It seems to run longer when the temperature is lower.  Also, positioning a small fan to blow air across the top of the iMac seems to delay the length of time before it will lockup.

I suspect my problem is with the hard drive itself or loose connections from it to the motherboard.

You may have a similar problem with loose connections that are aggravated by heat.  If you do open up your iMac, you might want to check and make sure all cable connections are secure.

Does your iMac exhibit the same behavior when using the Live CD as a Live CD?  In my case, lockup problem did not occur when using the Live CD.  When using the Live CD, the hard drive should generate less heat allowing the iMac to run cooler.

---

### Post by Radiolad on 2006-11-29
Hiya, Thanks for your reply. I booted the iMac this evening at 1800hrs and let it just sit with its desktop on and nothing else. I went and had my evening meal and returned to iMac at 1930hrs to have a little 'play'!(I was supprised to see it still on with its screen-saver)  I opened up the 'word' processor and made a few 'test' documents.  Whilst I was playing about, iMac decided 'he'd' had enough and switch himself OFF! at approx 2000hrs (just like that...not like that...like that) So I went down to my radio shack and played with my (50 year old) radios! (ther're slightly more stable!)
I think I will take a look inside iMac and give his 'multi-connectors' a push/pull to shift any oxidation from the connections. I had a connection problem on a VDU last year. It just kept flicking from ON to STANDBY mode every split second. It was just luck to find a multi-connector that needed an unplug/replug to clean the pins!
I have pondered about fitting a fan to the TOP of the iMac and housing it in a 'tupperware style' round container in order to cover the ring of vent holes and thus maximizing the 'suck' (or should that be 'draw') Of couse I shall have to find a 'graphite' colour plastic to match the case (wouldn't want it to look 'tacky now would I!)
I'm going to give Ubuntu a chance to prove that it's not the OS system, by trying a dual-boot on my PowerMac G4 (with fans !!!!)
Talking of LiveCD: I'm not quite sure how long the iMac was switch on for in this mode. I think I liked the look and feel of Ubuntu so much I decided to kick out OS9.22 almost immediately. Only AFTERWARDS did I realize I had lost the ability to adjust 'brightness/contrast/geometry' from the software (Arrgh!)
...How are you dealing with that problem ?? 
   I look forward to your reply,  Cheers  Radiolad

---

### Post by RHTopics on 2006-11-29
> Only AFTERWARDS did I realize I had lost the ability to adjust 'brightness/contrast/geometry' from the software (Arrgh!)
...How are you dealing with that problem ??

For adjusting brightness and contrast, I do not know of any software that will make those adjustments for an iMac.

For the geometry, if that means changing the resolution, then from the menu bar, click System -> Preferences -> Screen Resolution.  Depending on how your configuration file (/etc/X11/xorg.conf) for the X server is setup, you may have the option to change your resolution from its current setting.

Your iMac was the top of line, while mine is the bottom of the line for that model of iMac.  Yet, I am fairly certain they both have the same monitor specifications.  If you have only the current monitor resolution available to you, then you will need to edit the file "xorg.conf" found in the /etc/X11 subdirectory.  In the 'Section "Monitor"' part of this file if you have 'HorizSync       60-60' then change it to 'HorizSync       58-62'.  This change should allow you to have the resolutions of 1024x768, 800x600, 640x480, and possibly others as well.  I have added "ModeLine" statements in my 'Section "Monitor"' which limits my resolution choices to 1024x768, 800x600, and 640x480.

If on the other hand you mean geometry to be the placement(left, right, up, down) and size (wider, narrower, shorter, taller) of the screen image, then you will need to run "xvidtune" from a Terminal window.  xvidtune is a video mode tuner for Xorg.  It will allow you to make changes to your display.  And then it can generate a ModeLine statement which can then be placed in your /etc/X11/xorg.conf file to make the change permanent.

I have included a copy of my xorg.conf file so you can see how it fits together.  So, making changes to the display is definitely possible, but it  involves more manual editing than the Mac OS 9 environment.  

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
	Driver		"ati"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	58-62
	VertRefresh	75-117
        ModeLine        "1024x768" 78.5 1024 1045 1141 1312 768 769 772 796 +hsync +vsync
        ModeLine        "800x600" 62.4 800 813 893 1040 600 601 604 632 +hsync +vsync
        ModeLine        "640x480" 49.9 640 653 717 832 480 481 484 514 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
	Monitor		"iMac"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
 

```

---

### Post by EuroCity on 2006-11-30
So, **xvidtune** really works as a screen geometry preference panel for CRT iMacs? Good to know: very interesting information.

BTW, it would be really cool if there could be a graphical frontend to this program, sooner or later: but, in general, of course there should first of all be a general graphical display/screen preference also in Ubuntu, as for example in Fedora and other distros; Kubuntu, anyway, already has this in KDE (except the geometry tuning).

---

### Post by stream303 on 2006-11-30
> **RHTopics said:**
> I suspect my problem is with the hard drive itself or loose connections from it to the motherboard.

Sounds like the hd might be on it's way out if it works while cold, but seems to fail as it gets hot.  It may also be stressing the power supply as it is failing causing those shutdowns later?

Aside from mechanical failure, maybe run Apple's disk utility on it and see if it can detect bad blocks, etc.  Of course you'd probably have to reinstall Ubuntu after a thorough check.

Just some thoughts...

---

### Post by RHTopics on 2006-11-30
I concur with your thoughts about the hard drive being faulty.  A few months ago, I searched the Internet for others having overheating problems with the slot loading iMac G3s. Most of the posting I found were several years old, but they did indicate this model iMac can suffer from overheating and that the Maxtor hard drive being used had problems as well.

With the cost of hard drives these days being relatively cheap and they run cooler than older drives, I am thinking about replacing the hard drive with a larger one.  It is my understanding this iMac can support something as large as 120GB.

My greatest concern is breaking off something (i.e. tabs) when trying to replace the hard drive.

Maybe Radiolad will report back on his experience after he opens up his iMac.

---

### Post by Radiolad on 2006-11-30
Hi, Radiolad here. Well I've read up on how to dismantle the iMac and will hopefully be performing this task tomorrow (Fri 1st Dec)
I'll let you know how I get on. I do have a spare 20Gig HDD which is is good condition so in a worst case senario I could always change out the old one.   Thanks for all the other info. I really do wish there was a GUI for the 'screen adjust' task. In my own humble opinion (for what it's worth) the majority of 'home' users of computers want plug&play and GUI for all aspects of PC work which is why 'windows' will continue to dominate for a good time yet. It feels like a throw back to the 70's in the hay-day of HI-FI; it was more a case of listerning for the 'wow and flutter' of the turntable rather than the music ON the record (if you get my drift!!!)   Cheers,  Radiolad

---

### Post by Radiolad on 2006-12-02
Hi, Well I have removed the bottom section of casing and the metal screening. I have removed/replugged multi-connectors to/from HDD and CD drive. Everything looks as clean as when it left the factory, not a bit of dust or 'heat' grime. I did NOT remove the top casing as I could not figure this out! (I did remove the 4 screws to see if it became more obvious but did not persue it for fear of cracking the plastic!
I also removed/replaced to two RAM cards.
It is now back in one piece and being used to write this email..... so I guess It might not be long until it switches itself OFF !!!
  I'll let you know the ON-time prior to shut-off.    
Cheers, Radiolad

---

### Post by RHTopics on 2006-12-02
Radiolad,

Good to read that you were able open up your iMac and then put it back together again with no problems.

I found this web site on replacing the hard drive in a slot loading iMac;

[http://www.nelsonbc.ca/mactech_supprt_html/imac_hard_drive_replace/imac_replace_hard_drive.html](http://www.nelsonbc.ca/mactech_supprt_html/imac_hard_drive_replace/imac_replace_hard_drive.html)

Is that the one you used?

If your iMac does continue to switch itself off, then you may want to eliminate the possibility that it is caused by a process that is being run in Ubuntu.  If you still have a Mac OS 9 CD that you can boot up with it and then let it run to see if it shuts down after while.

If it does, that would definitely point to a hardware problem.

If it doesn't, then you would need to simplify Ubuntu to have it run with the absolute minimum number of processes.  That is, running just a terminal screen with no GUI software running (i.e. X server, Gnome).

Under these conditions, see how long it will run before shutting down.  If it keeps running, then you know it is a software problem.  Then you have to determine which process is causing the problem by adding them back one at a time until it shuts down on you.  That would be a lot of work, but it would definitely point out the culprit process.

---

### Post by Radiolad on 2006-12-02
Hi, YES! The link you gave is the one I used for removal of the bottom section. 4 of the 6 screws holding on the metal screening are a bit tricky i.e. NOT to let them drop into the upper casing! I put some *REALLY *sticky 'gum' on the end of the screwdriver tip in order to remove them without dropping. Thanks for the advice regarding running OS9; Unfortunately I do not have a CD ! but I'll ask around. I like the idea of running on minimum programs and working up (This has a ring of STAR TREK when Scotty  
replies to Captain Kirk about the engines not being able to cope on maximum warp drive !!!!!!!!!!!!!)
    Cheers for now from my side of the 'pond'.    Radiolad

---

### Post by Radiolad on 2006-12-03
Failed again...Yep! Everything looked rosey for approx 1hr, then 'plip'... iMac had had enough and switched off; right in the middle of me *TRYING *to work out how to get 'Firestarter'.  So it looks like trying to run with less progs. I was only on Firefox at the time!  (What is the eqivalent for Computer years with regard to human years!!??)     Cheers for now,  Radiolad

---

### Post by stream303 on 2006-12-03
It may not be heat related!  How about a dodgy power-switch?  There's mention of this to G3's:

[http://discussions.apple.com/thread.jspa?threadID=753622&tstart=0](http://discussions.apple.com/thread.jspa?threadID=753622&tstart=0)

I had also long forgotten my old 601 G3 had this same issue.  I had to jiggle the power switch to back it out just a bit after powering on so that it wouldn't inadvertently power down.

After my "jiggle fix", I only used the keyboard to turn the unit on.  I wish I would have remembered this sooner!

---

### Post by Radiolad on 2006-12-03
Hi, Thanks for the jiggle advice, I'll give it a try; and using the Keyboard switch?   Cheers.     Radiolad

---

### Post by RHTopics on 2006-12-03
Radiolad,

I have come up with an easy way to run a simplified system to check if the problem is with your hardware.

When the iMac boots up, it (yaboot) goes through two stages. At the second stage, you will see the following message on your screen;

```
    Welcome to yaboot version 1.3.13
    Enter "help" to get some basic usage information
    boot:

```
Press the "tab" key at this point to stop the automatic boot process.

yaboot will then display the available kernel images names on your system.  In my case, they are "Linux" and "old".

At this point all you are running is just "vmlinux", the boot image.

See how long it runs in this mode.  If it shuts down, then you definitely have a hardware problem.

To continue the boot process, enter "Linux" and press the return key.

Also, thanks for the heads up on easy it can be to lose screws when opening up the iMac.

---

### Post by Radiolad on 2006-12-03
> **RHTopics said:**
> Radiolad,

I have come up with an easy way to run a simplified system to check if the problem is with your hardware.

When the iMac boots up, it (yaboot) goes through two stages. At the second stage, you will see the following message on your screen;

```
    Welcome to yaboot version 1.3.13
    Enter "help" to get some basic usage information
    boot:

```
Press the "tab" key at this point to stop the automatic boot process.

yaboot will then display the available kernel images names on your system.  In my case, they are "Linux" and "old".

At this point all you are running is just "vmlinux", the boot image.

See how long it runs in this mode.  If it shuts down, then you definitely have a hardware problem.

To continue the boot process, enter "Linux" and press the return key.

Also, thanks for the heads up on easy it can be to lose screws when opening up the iMac.

Hi, Thanks for the info: I have just done what you advised at 21.40 GMT so I'm now going to wait and see!! It's just as well my faithful Compaq SFF is capable of 'all-day-running'.
I have also swapped keyboards and used the **keyboard on/off switch** following STREAM303's advice on possible faulty switch.
   Thanks to both of you.   Heres hoping!   Radiolad  :-k :-k

---

### Post by Radiolad on 2006-12-04
Hi, Well the bad news is...iMac managed to run in the minimal operating mode: '**vmlinux**' for approx 5 hours and then switched itself OFF ](*,) ....Arrgh!   So what next?  :-k 
It was obviously *warm *but not: 'whats-that-funny-smell' warm :rolleyes:. No smell of melting plastic or liquid wax (like before a Capacitor is about to go **pop**!

   Any ideas?     Regards  Radiolad

---

### Post by RHTopics on 2006-12-04
Radiolad,

A few thoughts on other things to look at and consider.

On my iMac, I remember having a problem with the power cord that plugs into the iMac not being fully plugged in and the computer would lose its power connection on occassion.  You may wanted to make sure it is properly plugged in and that nothing is pulling on it.

I am not that knowledgeable about iMac firmware, but could that be another area of possibility?

Could the power supply being going out on you?  Is there a way to test it?

On the bright side, since it does not appear to be software problem, once your hardware/firmware problem is solved, it should be smooth sailing with Ubuntu.

Best of luck,

RHTopics

---

### Post by dpny on 2006-12-04
Can you get your hands on an appropriate iMac Hardware Test CD? Apple makes them, but sometimes makes them hard to get. I got one for my Pismo from someone on the macnn.com forums.

If it is a hardware problem that CD would be the best way to diagnose it short of taking it into an Apple dealer/reseller.

---

### Post by stream303 on 2006-12-04
> **Radiolad said:**
> 
It was obviously *warm *but not: 'whats-that-funny-smell' warm :rolleyes:. No smell of melting plastic or liquid wax (like before a Capacitor is about to go **pop**!

   Any ideas?     Regards  Radiolad

On my old G3, the power switch was actually just a little button on the motherboard which lay at the end of a plastic on/off button on the case.  It was the little *motherboard* pushbutton that was stuck on.  (mine would constantly cycle the boot process.)  Is your switch actually located on a motherboard?

Almost sounds like that motherboard power button is *so* close to being constantly closed, that when the system heats up it closes the contact.  I just pulled it back with my fingernail and used the keyboard from then on...

---

### Post by Radiolad on 2006-12-05
Hi everyone. Thanks to you all: RHTopics,dpny,STREAM303  for your help, I'll give all your advice a try.   Apparently another 'in' thing to do with a mis-behaving iMacG3 is to convert it into a fishtank!!
My 'parallel' project is to install Ubuntu Dapper onto my G4 PPC which has two separate HDDs. I'd like to keep OS9.22 on the 'main' HDD and install Dapper on the 'slave' HDD. I haven't booted the G4 up for approx 6 months so it's anyones guess if all will go smoothly!
                 All good wishes  RADIOLAD

---

### Post by Appleby on 2006-12-18
I bought my iMac 5 10 mths ago in Taiwan and it was great using it.  Fairly recently I moved from Taipei to Shanghai and when my personal effects shipment arrived Shanghai yesterday and I could not wait to connect my iMac.

I plugged on the machine (Shanghai is 220V and Taiwan is 110V), the machine ran normally as it was before.  When I tried to connect my wireless keyboard and mouse with the PC, I switched off the machine in the normal fashion.  When I switched it on again, I could hear the noise of the fan (it was never lthat noisy before) but nothing on the screen.  I waited for about 2 to 3 mins still nothing.  I then took my machine to the bathroom, which is fitted with a 110V socket.  I switched it on again and I could only heard the fan but no screen.   

I was panic as I thought I might have done the wrong thing (110V to 220V with no transformer!).  Later, I found that the PC is universal and is functional in both environments. 

When  returned from work today, I switch it on again and it worked perfectly normal again.  I went for my dinner as Radiolad did and when I returned 1.5 hour later, the PC prompted me to force shut down.  I did and when I switched it on again, guess what the fan ran noisy again and no screen.  I repeated the force shut down twice but I could not switch it on again.  What is my iMac PC so bad in temper.  ](*,) 

Help please, anyone.  

Appleby

---

