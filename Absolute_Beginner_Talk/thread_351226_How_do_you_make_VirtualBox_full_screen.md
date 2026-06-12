---
title: "How do you make VirtualBox full screen"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-02-01
I've only installed Dapper a week ago, so I'm still a newbie.

I have installed VirtualBox which I'm quite satisfied with at the moment.  However, after installing Windows XP on it it only gives me a maximum resolution of 1024 x 768

My laptop is capable of 1440x900 nVidea

Does anyone know how I can get full screen for XP on Virtual Box please.

Many thanks,
David

---

### Post by miseljt on 2007-02-01
Right Ctrl + F

---

### Post by domino on 2007-02-02
You need to use the "Install guest addition.." option under the device menu to install the proper drivers on the guest and reboot the guest. Then do a Host+F and resize your guest using the "Display properties" to the res you like.

---

### Post by David Floyd on 2007-02-02
> **miseljt said:**
> Right Ctrl + F

Sorry, I didn't explain well.  I already have VirtualBox at Full Screen, but it's Windows XP within VirtualBox that is not.

I will have a look at 'domino' suggestion later today.  Seems a logical answer.

David

---

### Post by David Floyd on 2007-02-02
> **domino said:**
> You need to use the "Install guest addition.." option under the device menu to install the proper drivers on the guest and reboot the guest. Then do a Host+F and resize your guest using the "Display properties" to the res you like.

Thanks,

That worked to some extent, but only uses VirtualBox drivers and not the nVidia ones.  All standard screen size options are available but not wide screen, which is what I've got on my laptop :( 

David

---

### Post by Jussi01 on 2007-02-02
You need to host + G - it auto resizes the display so you can get widescreen. I had the same problem. Hope this helps.


Cheers

Jussi

---

### Post by David Floyd on 2007-02-02
> **Jussi01 said:**
> You need to host + G - it auto resizes the display so you can get widescreen. I had the same problem. Hope this helps.


Cheers

Jussi

That worked - thanks.

A new problem now - I seem to have lost sound :( 

Also, where can I find all these host+ codes?

David

---

### Post by Jussi01 on 2007-02-02
The sound source can be configured in the intial virtualox screen, before you start the virtual pc - there is a settings icon at the top of the screen. The host commands can be found in the menus once you have started the virtual machine in a window - not in fullscreen. (ie. where the guest editions entry was, but the other menu.)

Any other questions/problems just ask - we will help if we can

Cheers


Jussi

---

### Post by Karl S. on 2007-02-02
All seems to be good advice, but what if you did what I did....

In my initial efforts to make VirtualBox full screen, I tried changing the screen resolution from within Windows. This screwed everything up: the screen stretches off the edge of the monitor, the colors and text are all stretched out, and WIndows doesn't respond to any commands. That said, I can still use my virtual machine *if* I start Windows in VGA mode. Once in VGA mode, I can resize the screen just fine, and everything works. However, having to wait and press F8 every time I start my virtual windows machine is pretty annoying.

Anyone know a fix short of reinstalling?

--

Update: asked at the Virtual Box forum and followed the suggestion of starting my Virtual Machine in safe mode and then restoring it to an earlier point (i..e, click 'no' when the first dialogue comes up in safe mode). Worked like a charm.

---

### Post by David Floyd on 2007-02-02
> **Jussi01 said:**
> The sound source can be configured in the intial virtualox screen, before you start the virtual pc - there is a settings icon at the top of the screen. The host commands can be found in the menus once you have started the virtual machine in a window - not in fullscreen. (ie. where the guest editions entry was, but the other menu.)

Any other questions/problems just ask - we will help if we can

Cheers


Jussi

Thanks very much for your help - all's well now.

David

---

### Post by volkerbradley on 2007-02-09
> **domino said:**
> You need to use the "Install guest addition.." option under the device menu to install the proper drivers on the guest and reboot the guest. Then do a Host+F and resize your guest using the "Display properties" to the res you like.
I have Edgy as Host and MSVista as guest. When MSVista is displayed and I then click on Install Guest Additions ..., nothing happens.  Any suggestions?

---

### Post by skenagle on 2007-02-14
> **domino said:**
> You need to use the "Install guest addition.." option under the device menu to install the proper drivers on the guest and reboot the guest. Then do a Host+F and resize your guest using the "Display properties" to the res you like.

Ok here is waht i did... (running Edgy Host/XP Guest)

After gettting everything installed perfectly... (this is third time installing windows in the VBOX because of this issue)
1. I installed Guest Addition
2. Rebooted
3. I host+F (it goes to 1280x1024 full screen Black Frame with a 640x480 windows in the center)
4. Then in my guest PC... i right click on desktop,properties,choose settings tab, and slid the resolution to 1280x1024, then hit ok..
5. BOOM... screen goez nutz, now i have a huge blue frame around my 640x480 windows... but i cant do anything, it locks up... icons get all squiggly and i lose my xp install.

Can you please tell me what i am doing wrong?
Ive tried so many different ways... all im trying to do is run XP in VBOX in 1280x1024 mode.. and it seems possible.. somewhere though i am getting really mixed up or my computer hates me.

):P HELP ):P

---

### Post by Jussi01 on 2007-02-14
before you host+f for full screen, try host+g - its an auto resize - should help.

---

### Post by skenagle on 2007-02-14
> **Jussi01 said:**
> before you host+f for full screen, try host+g - its an auto resize - should help.

Yes i tried that , i did all the host commands before and after i went to full screen attempt.
I ran every combination of command i could thing of but my screen never resized until i switched the internal guest resolution to a higher one... thats when it all fell apart.

I feel like i am missing something, since so many people are running this software so well on their ubuntus.

thanx for tryin though...
i appreciate this community.

---

### Post by Karl S. on 2007-02-14
Sounds like maybe you did the same thing I did?

Restart your guest (the Win XP) in safe mode (f8: **function** 8, not smiley face 8!). Click 'no' (which should give you the option of restarting from a restore point). Chose a date before you screwed everything up. That should fix it.

At the least, you can try what I did for a few days, which is start in VGA mode every time (again, f8, and then choose VGA). It's not optimal, but it certainly worked.

---

### Post by skenagle on 2007-02-14
> **Karl S. said:**
> Sounds like maybe you did the same thing I did?

Restart your guest (the Win XP) in safe mode (f8: **function** 8, not smiley face 8!). Click 'no' (which should give you the option of restarting from a restore point). Chose a date before you screwed everything up. That should fix it.

At the least, you can try what I did for a few days, which is start in VGA mode every time (again, f8, and then choose VGA). It's not optimal, but it certainly worked.

Ah yes thank you for that... i have been doing it since i read it in one of your other posts... 
everytime i try to resize my windows install it totally F's things up... 

i know there are people here who are running Vbox in a higher resolution than 800x600.

I just cannot figure it out.. its infuriating.

I even upgraded to service pack2 in my xp install and got every update thinking it could be a driver conflict locally... but nope..

I hit Host+A and Host+g and Host+F ... and it stays 640x480...


ahhhh .... i will pay Virtualbox to fix this but their IRC cahnnel is never responsive and their forums have at least over half unanswered... support seems almost non existant.

See i know its open source, but if this works for me, i will pay for the full version for my customers and move them to ubuntu...


much to gain here.


in the meantime... 640x480 and doing host+( :( )

---

### Post by Karl S. on 2007-02-17
Skenagle, if it's any comfort, I'm having the same problem. I've no idea how to work out a solution to it, though.

---

### Post by skenagle on 2007-02-17
> **Karl S. said:**
> Skenagle, if it's any comfort, I'm having the same problem. I've no idea how to work out a solution to it, though.

WOW Karl..i wonder if we can get help.

Do you use an ATI Card?
Mine is a X600 .. i wonder if this is the link between our issues.

Im on a Dell 9150 PC.

does anyone know if they offer support outside of IRC and their Crap forums?

i would really like to use this software.

other than this ONE issue... its stable and fast.

---

### Post by Karl S. on 2007-02-18
Aargh. This is how little I know: I can't figure out how to list out what hardware I have (at least, not in Xubuntu, which is what I have to run if I want VirtualBox to run at a decent speed). I have an HP Pavilion ze2315us laptop, which I'm *guessing* uses an Ati Radeon Xpress 200M IGP. So, yeah, ATI card. Probably.

EDIT: figured it out. I looked at my xorg.conf file. Here's the relevant information. And I just looked for ATI graphics cards on the forum here, and, yes, they're a POS when it comes to Ubuntu.

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes

---

### Post by skenagle on 2007-02-18
ok interesting, it seems we are both running ATI then.

Have you tried running the Envy Script to update your drivers?

---

### Post by Karl S. on 2007-02-18
Did I know about the Envy script until just now? Nope. I know pretty much nothing about computers.

Okay. Ran it. Thanks for suggesting it.

Also followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+radeon+xpress+200M")

But t[his thread]("http://www.ubuntuforums.org/showthread.php?t=255929&highlight=ati+200m") contains a lot of complaining from people running the ATI 200M card. There's also [this.]("http://www.ubuntuforums.org/showthread.php?t=231529&highlight=ze2315us")

I don't know if this info is useful, but here goes. After all that updating:
karl@karl-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

This might also help??
karl@karl-laptop:~$ glxinfo | grep direct
direct rendering: Yes



And all the updating didn't effect my VirtualBox install either way. If the problem with VirtualBox is a graphics card thing, we might be SOL. Or, uh, should we update the graphics card from within the Virtual Machine? Would that help?

---

### Post by james957 on 2007-02-27
I'm having volkerbradley's problem:  In the Devices menu, I click on Install Guest Additions... and nothing happens.  

Anyone else having the same problem?

James

---

### Post by michwill on 2007-03-07
I'm using Windows XP as the host and Ubuntu as the guest.  I can't get Ubuntu to use 1280x1024 despite the host running at 1280x1024.  And installing the "Guest Additions" with an Ubuntu guest appears to cause serious issues.  Any suggestions?

---

### Post by Karl S. on 2007-03-07
> And installing the "Guest Additions" with an Ubuntu guest appears to cause serious issues.

What happens?

BTW, I still can't get my guest (Win XP; host: Edgy Xubuntu) to run full screen. I have Guest Additions installed, so that's not the problem. Whenever I change the screen resolution to match my host resolution (according to whatever's listed in xorg.conf: 1024 X 768), the guest machine becomes inoperable. The graphics 'stretch out' and become unclickable, and the only way to reset the VM to something useable is to start it in safe mode and then go back to a restore point. Going to 'auto-resize' the guest doesn't work. The Virtual Machine window stays the same size.

Irritating!

(if this is at all useful, here is some current data that may or may not be useful:


karl@karl-laptop:/etc$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
karl@karl-laptop:/etc$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

(this is leftover from my failed efforts to get either Beryl or Compiz running with my pathetic graphics card, an ATI Radeon Xpress 200M (RS480))

---

### Post by mangoti on 2007-03-07
> **james957 said:**
> I'm having volkerbradley's problem:  In the Devices menu, I click on Install Guest Additions... and nothing happens.  

Anyone else having the same problem?

James

Open terminal, cd to cdrom folder and issue: ```
sh VboxAdditionsLinux.run
```
Please check the filename, I'm not sure of the exact name.

---

### Post by kevmartin on 2007-03-07
Similar problems here - it was all going so well lol - I had it running nicely at 1024 resolution, but right after getting the guest extensions running, I told it to go to 1600x1200 resolution that my system normally runs at, and everything went haywire. None of the host+ keys or menu items does any good.  I can load it OK using either safe mode or VGA mode, buyttaht's no fun because changes I make there don't help once I reboot again. Bugger.

As it's a fresh install - no apps installed yet - I think I will reinstall and avoid further frustration.  Then take a snapshot and system restore point - then I'll read more before I jump in and try to raise resolution higher than 1024.  Maybe increase the video memory available too? (just a thought).

---

### Post by kevmartin on 2007-03-08
> **james957 said:**
> I'm having volkerbradley's problem:  In the Devices menu, I click on Install Guest Additions... and nothing happens.  

Anyone else having the same problem?

James

I had this happen too - until I unmounted the cdrom, then when I clicked on Install Guest Additiosn again, the installation program started right up :)-)

---

### Post by kevmartin on 2007-03-08
Update on my experiences: I did my reinstall, and now have everythign running well, including access to otherdrives from the virtualbox - except the best screen res I can get is 1024.

I took care to take snapshots every step of the way, and system restorepoints too.  Then I tried the suggestions here on the screen resolution and got the same result again.  Using the suggested host keys, followed byusing windows properties to change the screen resolution up to 1240 (thereare numerous others listed including wide screen ones - none of which are listed as options without using the host keys first).  Result, screen goesbonkers again, and can't be fixed.

Thankfully, rebooting to VGA mode allows me to then use the system restore point to get back to normality :-)

So it's annoying only having a 1024 screen to work with when you are used to 1600, but workable.  I'd still love to hear any other input.

Thanks

---

### Post by Karl S. on 2007-03-18
FIXED.

I just updated to the new version (1.3.8)--that's one point three point eight--and now full screen works perfectly.

---

### Post by kevmartin on 2007-03-21
sounds hopeful :-)

But I have a question - how do I update to 1.3.8?

Synaptic says I have 1.3.6 and that 1.3.6 is the latest version?

Thanks

---

### Post by Karl S. on 2007-03-30
Download the latest from the VirtualBox website

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by kevmartin on 2007-03-30
Thanks a lot - worked a treat for me too ::grin:

---

### Post by 5thgendriver on 2007-04-01
yeah so im trying to get vista fullscreen but when i hit install guest additions - nothing happens - is there something im missing or is there a way to perform this install through console - thanks

---

### Post by dacool25 on 2007-04-01
All it does when you hit install guest additions is mount the cd image, so go to my computer and then double click the cd.

I'm having a problem myself with this, and i was wondering if someone could help.  When i go full screen, i still have the ubuntu taskbar (top and bottom)  I try to set it so that the virtual machine is on top, but nothing.  Anyone have any ideas or suggestions?

EDIT - I tried this in metacity, and it works fine.  So, if that makes any difference can anyone help me?

---

### Post by jimbosheep101 on 2008-06-01
hi i am having the same problem, i had vista running for a bit in virtual box (but didnt work with my wifi) so i installed xp and it works with my wifi but when i click "install guest addition" nothing happens, by the way i did install guest additions when i had vista running (if thats any help)

---

