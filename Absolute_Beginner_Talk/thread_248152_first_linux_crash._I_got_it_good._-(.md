---
title: "first linux crash. I got it good. :-("
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by ehonda on 2006-08-31
I was trying to install Xgl and had everything right so I thought. When I went to log in the desktop didn't work at all. I rebooted and thought I'd try to update the drivers as said here: [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html) in the ATI 3d section. When I rebooted after the driver install I got a screen that said 'failed to start the x server...likely not setup right..'

Is there anyway to install the correct drivers from the command line I recieve after I enter through all the flim flam that tells me how bad I screwed up?

---

### Post by Toxicity999 on 2006-08-31
First did you use the Permanent XGL session or the temporary XGL session install? If you need clarification the permanent pops you into a session on startup, where as the Temp method allows you to run it by Selecting the XGL session from the GDM login screen.

that will help me pull over your XGL issues. Now second for the record of Linux sake you didn't experience a 'linux' crash but rather Xorg which is just what gives you a nice GUI. Anyway Do you have a nvidia or an ATI? are you *sure* you edited xorg.conf correctly?

If you want know how to easily undo XGL starting automatically (if you did it that way that is.) Do it for simplicities sake and edit /etc/X11/xorg.conf and replace fglrx with ati or nvidia with nv this will let you use the Open source drivers until you get things squared away and let you use a more confortable GUI environment. Open source drivers are perfectly fine for normal use I might add. At this point you'll need to consult someone more experienced with Driver trouble shooting I can only get you to this point really.

---

### Post by ehonda on 2006-08-31
Thanks for the response. 

I selected this session only on login for Xgl. Then when I was logged back in w/o running Xgl I d/l'ed the new drivers and installed them. When I rebooted the third time is when it crashed. After the driver update. It wouldn't even go as far as letting me choose the session I wanted. Even though on the second boot I clicked 'default' again. I'm going to try this:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)

In the manual install portion. I'm assuming that will get me back to the UI with the open source drivers?


O yeah, it's a Radeon Mobility 7500.

---

### Post by Toxicity999 on 2006-08-31
MEHP! This first paragraph is an Edit Fglrx does NOT NOT NOT work with the 7500 mobility from personal experience! So only take to heart what I say about swithcing to the open source drivers! I recommend reversing any fglrx packages you install after you get with the Open source drivers, you may then get Direct Rendering from them :D

well you can do just what I said without uninstalling fglrx (though if the opensource drivers would normally give you 3d acceleration the won't now!) just for the short term type:

sudo nano /etc/X11/xorg.conf

look for the block with fglrx which will look like this:

> Section "Device"
       Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 900$        Driver      "fglrx"
       Option      "VideoOverlay" "on"
       Option      "OpenGLOverlay" "off"
       BusID       "PCI:1:0:0"
EndSection 
You'll want it to look something liiiiiiiike

> Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 900$        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection 

Of course don't take that word for word the identifier and busid may be differen't just giving you the basic transition. See how I removed all the extra stuff about the overlays? yea.

of course you can always run:

sudo dpkg-reconfigure xserver-xorg

which is the graphical way to fix things up by selecting 'ati' when prompted for driver info. But with this you need to push through a tonnnnnnn of unrelated questions. So try the first way if you break it no biggie run through the secondary command.

Oh... By the way 
If you don't want to restart evertime you play with xorg config. When it tosses you to terminal type:

sudo killall gdm
sudo gdm

this kills the gdm session still ghosting in the back an restarts parsing the new xorg configuration.

Feel free to play around trying to get the fglrx drivers working again later just refer to this if you happen to kill things again! Xorg config issues are always reverable... I say that lightly you can of course mess things up badly but that doesn't much apply to this.

If you type glxinfo and see Direct Rendering: Yes after removign all the fglrx packages you know you CAN still run XGL and compiz using compiz-vanilla sets! In most cases, just a tip :o

---

### Post by ehonda on 2006-08-31
Awesome response. The reconfigure worked just fine. When I run glxinfo direct rendering is no now. So I need to figure out how to fix that. That was kinda scary for me. Up until this week I never even really knew how to use the command line. Live and learn. Now I'm not so afraid of the terminal and I'm gonna be a little bit more careful about what I do and don't install. lol

Thanks again! - Marshall

---

### Post by Toxicity999 on 2006-08-31
No problem! but never be scared of the terminal! As fancy as all the GUIs in Dapper and soon edgy are the real powers always in the command line. And I'm not sure on getting direct rendering post failed fglrx install with the ati drivers... out of the box it might give you rendering... pop in a live cd and see if glxinfo returns something different. If it says no there then atleast you know it doesnt work out of the box for your card and there's no time wasted in trying.

also sorry for the slight distortion in my quote blocks earlier obviously the driver line should be broken to the next.

---

### Post by ehonda on 2006-08-31
Ok, before I go jacking with it too much again. Here's what I have in the terminal.
> Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]ATI Radeon Mobility 7500"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection


Thats what it gave me after running the xorg command and walking through all the goofy steps. I do know for a fact though that the directrender command returned a yes before I started fooling with it. The reason I updated the drivers was b/c after I logged in with xgl the desktop was all messed up. There were just a bunch of wierd colors and no text or icons.

---

### Post by Toxicity999 on 2006-08-31
Well that looks fine. What I was hinting at is see if Direct Rendering works out of hte box for you with the open source drivers. To do that instead of retarding fire up a live CD and use the glxinfo command and look for direct rendering which should be accurate to a default install. If that says no I wont say all hope is lost but getting direct rendering through the open source drivers probably wouldn't be easy! Seeing as your a newer user diving right into that might be a little like jumping into the deep end without waterwings you know lol. Xorg.conf you can always reconfigure messing with library links and stuff ehhh most advanced users don't like that stuff. I propose you live without until you get out of the box rendering with any hopes with a fresh edgy isntall (October I think that is right?) Or hope fglrx pushes back the models they support... which they should! Inspiron lines that are still made an popular arent even supported which is a pain. Laptop users like us can't just buy a new card in most cases... though for my inspiron 5100 I did! not technically supported but the Mobility 9000 from the inspiron 5150 works aces! 64mbversion not so much but 32 works fine. I say that on the off chance You have one. If you do I can hook you up with a 9000, I found some random site selling them... easier than dealing with spare parts from dell...

---

### Post by ehonda on 2006-08-31
I can actually install that thing in here? I've been told by others to leave everything but the ram and HDD alone. Although all the ppl telling me that also think i'm crazy for jumping in the shark end of this program like I have. What can I say? This is fun to me. 

Is there no unsupported drivers somewhere for the 7500 that are beta or only slight chance to work? I can do without if necessary, but would rather try just to see if I can make it to the end of this nice little puzzle. I'm going to try to install BF2 and see if that works. If that doesn't work then I'll be totally unsatisfied with my hardware and be forced to start looking deeper into this issue. I thought this was a decent laptop when i got it. Maybe I should sell it and buy something a little nicer?

---

### Post by ehonda on 2006-09-01
Ok, Wine tries to set up BF2 but kicks the install when it asks for the second cd. I think I might give it a rest for a little while before I fry my brains and poo on my keyboard.

---

### Post by Toxicity999 on 2006-09-01
If you can't find a detailed workaround just try copying all the install media to one folder (asuming it doesn't overwrite.) little trick for WoW install. try appdb.winehq.org search for what your installing look through all the listed versions might even be a dapper test mahine amongst them If there is click show. But usually all the guides and problems apply cross distro.

---

### Post by justin whitaker on 2006-09-01
> **ehonda said:**
> Ok, Wine tries to set up BF2 but kicks the install when it asks for the second cd. I think I might give it a rest for a little while before I fry my brains and poo on my keyboard.

You have to manually unmount and remount the drive under WINE. 

Tox is right, try the WoW/HL2 hack, where you copy the CDs to HD, unpack them, and install from there.

---

### Post by ehonda on 2006-09-01
Allrighty then. I'll spend the better part of my afternoon figuring that one out. Man these forums really curve the learning curve. haha.

---

### Post by Toxicity999 on 2006-09-01
also you never answered aboput your laptop do you have an Inspiron 5100? If so what I'm saying is verified all over the Inspiron boards (The official ones.) Users always report the 32mb M9 from the 5150 to work like a dream. I can verify that too. And that's right bottom of the line for hte official drivers. and To answer your questions I'm not an expert on the open source drivers but I know if you don't get direct rendering out of the box (check with the Live Cd like I mentioned) then you have to go throug hehll to do it. And there aren't a ton of different packed drivers like htere are with Windows like Omega and other customized sets. It's basically ati, radeon, or fglrx for us. That is drivers specifically for us vesa works for damned near everything but only basic calls. (That's what things like uspasl and splashy use that users see when they first boot up before anything really is parsed xorg wise!) As user friendly as we try to make ubuntu the best way to learn is your first breakage which is 90% of the time user inflicted these days but hey what can you do but learn when it happens!

---

### Post by ehonda on 2006-09-01
> **Toxicity999 said:**
> also you never answered aboput your laptop do you have an Inspiron 5100? If so what I'm saying is verified all over the Inspiron boards (The official ones.) Users always report the 32mb M9 from the 5150 to work like a dream. I can verify that too. And that's right bottom of the line for hte official drivers. and To answer your questions I'm not an expert on the open source drivers but I know if you don't get direct rendering out of the box (check with the Live Cd like I mentioned) then you have to go throug hehll to do it. And there aren't a ton of different packed drivers like htere are with Windows like Omega and other customized sets. It's basically ati, radeon, or fglrx for us. That is drivers specifically for us vesa works for damned near everything but only basic calls. (That's what things like uspasl and splashy use that users see when they first boot up before anything really is parsed xorg wise!) As user friendly as we try to make ubuntu the best way to learn is your first breakage which is 90% of the time user inflicted these days but hey what can you do but learn when it happens!
Its a Compaq 610c. Unfortunately, nothing top of the line. I checked with the cd and out of the box it does show yes for the rendering. I wish I'd of never screwed with it. BUT!!!!...That is how we learn right?

---

### Post by Toxicity999 on 2006-09-01
Try removing the fglrx packages by reversing the howto you followed and make sure your Driver inxorg.conf is ati and not vesa. Might get lucky and have it restored! Otherwise anyone want to step in on how to get the out of the box rendering back? I won't lie to you the Open source drivers 3d rendering isn't great at all right now but better than nothing or a blue xorg error screen! If you can't reverse things to a point of getting rendering enabled again just hang in there till edgy hits the scene and manually reinstall... or do it now with dapper, your choice.

---

### Post by ehonda on 2006-09-01
> **Toxicity999 said:**
> Try removing the fglrx packages by reversing the howto you followed and make sure your Driver inxorg.conf is ati and not vesa. Might get lucky and have it restored! Otherwise anyone want to step in on how to get the out of the box rendering back? I won't lie to you the Open source drivers 3d rendering isn't great at all right now but better than nothing or a blue xorg error screen! If you can't reverse things to a point of getting rendering enabled again just hang in there till edgy hits the scene and manually reinstall... or do it now with dapper, your choice.

I'm seriously contemplating reinstalling with Ubuntu Server instead of the install thats here. I don't need a lot of the fluff thats here. This machine is a duty machine anyway.

---

### Post by Toxicity999 on 2006-09-01
Well if you want a light machine you can always install server than install xubuntu-core then you get xfce mega lightweight. But whatever works. Glad I could atleast help you figure out some things :D

---

### Post by ehonda on 2006-09-01
> **Toxicity999 said:**
> Well if you want a light machine you can always install server than install xubuntu-core then you get xfce mega lightweight. But whatever works. Glad I could atleast help you figure out some things :D

Yeah for sure. I really appreciate it.

---

