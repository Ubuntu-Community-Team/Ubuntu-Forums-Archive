---
title: "cant install from live CD on G4 powermac"
date: 2006-12-17
forum: Apple PPC Users
---

### Post by alexo on 2006-12-17
Hey everyone!

Im brand spakin new to Linux. Ive used Macs for years, but ive never gotten around to trying Linux. The latest Macaddict (Jan 2007 - not on stands yet i think) has a nice detailed how-to section on getting Ubunto running on a PowerPC mac and getting Airport configured.  I received the CD from Ubunto (Version 6.06) and following the magazine, i partitioned my drive into a Mac OS X partition, a large Free Space section of about 10 gigs and a free space section of 500 megs for a swap partition. 

So here is where it gets kinda messy. I put the CD, restart and press C to start up from the disc. So i get an intro screen of text that begins with "Welcome to Ubuntu 6.06" etc,  press enter, and it goes to a black screen that says with an orange Ubuntu logo with a progress bar and it starts loading this

Loading essential drivers........ok
Mounting root file system........ok
Moving mount points...........ok
Adding Live CD user

then the screen goes black and does nothing. zero. zip. the only response i can get is if i press enter then i get a blinking underscore, as if its waiting for text input or something.. you can type stuff and press enter and it just goes to the next line. 

the specs on this G4 tower are 400mhz G4, 256 mb, 25 GB, mac os X 10.3

please help! i would definitely like to use Linux.
thanks in advance.

-Alexo

---

### Post by dirkb on 2006-12-17
> **alexo said:**
> Hey everyone!

Im brand spakin new to Linux. Ive used Macs for years, but ive never gotten around to trying Linux. The latest Macaddict (Jan 2007 - not on stands yet i think) has a nice detailed how-to section on getting Ubunto running on a PowerPC mac and getting Airport configured.  I received the CD from Ubunto (Version 6.06) and following the magazine, i partitioned my drive into a Mac OS X partition, a large Free Space section of about 10 gigs and a free space section of 500 megs for a swap partition. 

So here is where it gets kinda messy. I put the CD, restart and press C to start up from the disc. So i get an intro screen of text that begins with "Welcome to Ubuntu 6.06" etc,  press enter, and it goes to a black screen that says with an orange Ubuntu logo with a progress bar and it starts loading this

Loading essential drivers........ok
Mounting root file system........ok
Moving mount points...........ok
Adding Live CD user

then the screen goes black and does nothing. zero. zip. the only response i can get is if i press enter then i get a blinking underscore, as if its waiting for text input or something.. you can type stuff and press enter and it just goes to the next line. 

the specs on this G4 tower are 400mhz G4, 256 mb, 25 GB, mac os X 10.3

please help! i would definitely like to use Linux.
thanks in advance.

-Alexo

i installed the latest version (6.10) yesterday on a G4/466 w/ 1 gb ram. i erased and installed. it functions well. it booted into the live CD, ran from the CD. erased and installed.

when it boots, it relaunches the video driver a couple times prior to reaching the sign on screen. once there, the ubuntu sign on ditty (if you will) doesnt sound, but it launched and upgraded fine, recognizing the gigabit chipset in the tower and the radeon 9000 64 mb card, and the pioneer dvr-108 straight away. i also have 6.10 running on a P4 HT 3.0. it's a bit snappier. i'm gonna do some adjustments to the G4.

---

### Post by Tait on 2006-12-17
Try typing in 'live video=ofonly'.  This will tell it to use the most basic drivers available.

---

### Post by frustrator on 2006-12-19
> **Tait said:**
> Try typing in 'live video=ofonly'.  This will tell it to use the most basic drivers available.

Hi... Linux noob here.

I have a similar problem. I know that it is not exactly the same because I am not trying to install from the Live CD.

I'm trying to install the Edgy Server version and even after the "install video=ofonly" I am still getting a white screen. Unless I select "expert video=ofonly", then it goes white for a second then completely blacks out.  ](*,) 

Does anybody have any suggestions?

Oh, the computer is a G4, Dual processor 533, 640 Megs ram. Almost everything is stock on it.

---

