---
title: "Absolute beginner: help setting up Creative Zen Touch.."
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by zombies!!! on 2007-02-02
Hello,

I'm looking to set up my Creative Zen Touch mp3 player to run under Edgy. To be perfectly honest, I'm a little lost as to where to start. I have installed libusb and libmtp as well as downloading but not yet compiling Gnomad.

lsusb is giving me this: 
Bus 003 Device 004: ID 041e:411b Creative Technology, Ltd Zen Touch
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

I'd appreciate someone walking me through getting this working, because I'm a little lost. What little I have done has been through reading other topics, but I'm still no nearer to having it done than I was when I started, really.

Cheers.

---

### Post by davebgimp on 2007-02-02
Did you check first to see if the gnomad2 package in the Ubuntu repos works with it? That should be all you have to do (I mean, that's all I had to do). 

sudo apt-get install gnomad2

---

### Post by zombies!!! on 2007-02-02
Which I would go about doing how?

---

### Post by davebgimp on 2007-02-02
You can launch the package manager Synaptic, search within it for 'gnomad2' and install it.

or 

open a terminal and type what I posted earlier:
sudo apt-get install gnomad2

after all the installing is done, hit ALT-F2 and type gnomad2

If you have problems getting the program to load, try running it as root.

---

### Post by zombies!!! on 2007-02-02
All appears to be working appropriately. Thank you.

---

### Post by badtlc on 2007-04-15
I am also a total noob trying to get a zen touch to work.  The device is listed when i run lsusb, but when i try gnomad2, it says no jukeboxes found on USB bus.  What am I missing?

---

### Post by JamesDownWell on 2007-10-30
Hi, this thread seems pretty similar to what I'm after. New to Ubuntu/Linux...

Have been reading around for a while and can't see anything to seemingly help!

If this helps I am:

Running Gutsy
Have checked libmtp is installed
Have checked libnjb is installed
Installed Gnomad

lsbusb shows it:

Bus 007 Device 002: ID 0644:0200 TEAC Corp. 
Bus 007 Device 003: ID 050d:705c Belkin Components 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 004: ID 041e:4131 Creative Technology, Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:2105 Dell Computer Corp. 
Bus 001 Device 005: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 001: ID 0000:0000  

and I have Gnomad telling me No Jukebox found on USB. 

Oh yeah, and the player is Creative Zen Touch with 2.11.01 firmware...

Please Help!!

---

### Post by JamesDownWell on 2007-10-30
Oh and the device does not appear to show as connecting (mounting?) anywhere in the GUI.

---

