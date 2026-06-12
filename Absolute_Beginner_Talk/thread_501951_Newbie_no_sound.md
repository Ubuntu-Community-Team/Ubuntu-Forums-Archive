---
title: "Newbie no sound"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Bob Bismal on 2007-07-16
Dual boot Vista, Ubuntu 7.04.  Celeron 1.73, ATI video, Realtek sound.  
I had it working, but I reloaded Ubuntu and now I can't find the guide to get it working again.   Help.

Also last time I installed something that installed a lot of popular apps.  I think it started with an A.  Any ideas?

Thanks
Bob Bismal

---

### Post by jusmurph on 2007-07-16
I had this experience were sound stopped playing in Flash, then stopped in videos all together. The issue was that it was not using the right default sound device. 

```
sudo asoundconf list
```

It will list the available sound devices, in my case:
CK804
Audigy2

I want the **Audigy2** to be default so :
```

 sudo asoundconf set-default-card **Audigy2**
```

Obviously change the Audigy part as you need.

Also you really want to be running ALSA.

GUI Areas you should check:
System > Preferences > Sound
System > Preferences > Multimedia Systems Selector
Speaker Icon in the Speaker Tray.

---

### Post by wolfen69 on 2007-07-16
check here [www.ubuntuguide.org](www.ubuntuguide.org) for your sound issue. the program that started with "A" is probably automatix.[http://getautomatix.com/](http://getautomatix.com/)

---

### Post by bodhi.zazen on 2007-07-16
> **wolfen69 said:**
> check here [www.ubuntuguide.org](www.ubuntuguide.org) for your sound issue. the program that started with "A" is probably automatix.[http://getautomatix.com/](http://getautomatix.com/)

LOL I doubt that ;)

Also see : [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

That guide discusses how to set a default sound device as well.

---

### Post by Bob Bismal on 2007-07-16
I found drivers on the Realtek site, but I've no idea what to do with them.  I download it and try to install, but nothing happens.  Is there a guide in normal english that'll walk me through the install?

---

### Post by mike102282 on 2007-07-16
> **Bob Bismal said:**
> I found drivers on the Realtek site, but I've no idea what to do with them.  I download it and try to install, but nothing happens.  Is there a guide in normal english that'll walk me through the install?

I don't think it is a driver issue because I have realtek sound and it works fine for me.

---

### Post by Bob Bismal on 2007-07-16
I get the following for : sudo asoundconf list

Names of available sound cards:
SB

No Realtek,  What the heck is SB?

Under System>Preferences>Hardware Information I can find

Vendor: Realtek Semiconductor Co., Ltd.
Device:  RTL-8139/8139C/8139C+
Status:  Status
Bus Type: PCI
Device Type: Unknown
Capabilitis:  Unknown

Doesn't seem to me that info should be Unknown.

---

### Post by Bob Bismal on 2007-07-16
anyone?

---

### Post by Bob Bismal on 2007-07-16
Looks like I might have to go back to Vista.  Been googling for hours trying to find a fix.  A PC with no sound just sucks.

---

### Post by Skidpad on 2007-07-16
Did you run through the troubleshooting guide in the link that bodhi provided above?

---

### Post by Bob Bismal on 2007-07-16
> **Skidpad said:**
> Did you run through the troubleshooting guide in the link that bodhi provided above?

Yes.  Still no sound/audio

Under System>Preferences>Hardware Information I can find

Vendor: Realtek Semiconductor Co., Ltd.
Device: RTL-8139/8139C/8139C+
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilitis: Unknown

Shouldn't the Device type and capabiltis be known for this?
What does SB mean when I do: 
sudo asoundconf list
Names of available sound cards:
SB

---

### Post by bodhi.zazen on 2007-07-16
OK, did you install the drivers from Realtek ?

Extract the zipped file.

Open a terminal, cd into the extracted directory.

Read the README.

Then :```
sudo apt-get install build-essential
./configure
make
sudo make install
```

Post any errors.

Then, 

```
./snddevices
```

---

### Post by Bob Bismal on 2007-07-16
Tried to read the Readme file.  Why not write stuff in English so everyone can understand, I mean everything is so cyrptic?  Why not write a readme file step by step so everyone can do get stuff to work.   I thought Ubuntu was supposed to be user friendly.  

I downloaded and extracted the drivers to my desktop.   clicked the install and about 5 mins of code started going.  After that it auto closed the window.  Still no sound.

---

### Post by bodhi.zazen on 2007-07-16
Not sure what you did exactly, but that does not sound like the way to install the drivers.

You can try :

1. Rebooting.

2. If that fails, you will need to follow the commands I gave you and post any error messages.

---

### Post by Bob Bismal on 2007-07-16
ME@Laptop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

ME@Laptop:~$ ./configure
bash: ./configure: No such file or directory

ME@Laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.

ME@Laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.

ME@Laptop:~$ ./snddevices

---

### Post by bodhi.zazen on 2007-07-16
LOL

That's better ;)

All you need to do now is cd (for change directory) into the extracted archive.

If you downloaded and extracted (the archive) to your desktop, start with 

cd Desktop

You and then list with 

ls

You can reduce tyypos with tab completion. Start typing a file or directory and use the <tab> key to complete ...

so ...

cd Desk<tab>


[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by anewguy on 2007-07-16
I'm a very new user to Linux and to Ubuntu, so I won't say this applies to you, but it was something I found that helped me get sound working on my laptop.  I can't find the link again that I found this on, but I do wish to thank whoever it was that posted it.:)

Double-click on the speaker or whatever you have to get to the mixer.  Change the device (if not already there) to the asla mixer, click on edit  and then preferences, then be sure that external amplifier is checked.  Now go back to the main mixer screen and click on the switches tab and uncheck external amplifier.  It sounds counter-intuitive, including it but turning it off, but that worked for me. 

Although it may not help you, perhaps it can help others reading this thread.:)

Good luck!:)

---

### Post by Bob Bismal on 2007-07-16
I GIVE UP :( . A PC with no sound just sucks.  Two days of reading, googling, reading, rebooting, freeze up, crashing, trying everything I can find and still nothing.  Ubuntu has a long way to go to being even half as user friendly as  even Windows 98.  Doesn't even include the PITA just to get my ATI video card working.  Don't know what I was thinking, I've got a perfectly good lappy running Vista with absolutly zero problems and I thought, "Hey let me bang my head off the wall for a couple days and see if I can get this new OS working, that I wont even be able to use half my apps with."    Thanks for all your help guys, I really do appreciate your help, but even for free Ubuntu just cost too much (time=$).

---

### Post by Earthwormzim on 2007-07-17
When I first installed Ubuntu, I could not get the sound to work either.  After hours and hours of searching the internet for help, I nearly gave up.  I tried just about everything, like configuring the Alsa-Mixer, etc.  But in the end, it turned out to be something far simpler...I have an Audigy card, but perhaps your card will have something simlar.  

As it turns out, all I had to do was double-click the volume bar in the panel, and the "Volume Control: Audigy 1 [SB0090] {Alsa mixer}" window popped up.  On it, there were two tabs; one labeled, "Playback" and the other, "Switches".  On the "Switches" tab there was one check-box that said, "Audigy Analog/Digital Output jack: [ ] " (the brackets represent the check-box).  For some reason, Feisty came with that setting checked by default, which silenced my computer.  So, I unchecked it, and...voila!  SOUND!

I know you don't have the same card or drivers...but who knows, maybe yours will have a similar set of options.

One thing that I think is odd, though, is the command-line version of the Alsa-Mixer did not include this option...which is one of the reasons it took me so long to figure it out!  Nowhere on any page, did I ever find anything that said that I could access a GUI version of the Alsa-Mixer simply by double-clicking the volume bar.

---

### Post by playme123 on 2007-07-17
> **jusmurph said:**
> I had this experience were sound stopped playing in Flash, then stopped in videos all together. The issue was that it was not using the right default sound device. 

```
sudo asoundconf list
```

It will list the available sound devices, in my case:
CK804
Audigy2

I want the **Audigy2** to be default so :
```

 sudo asoundconf set-default-card **Audigy2**
```

Obviously change the Audigy part as you need.

Also you really want to be running ALSA.

GUI Areas you should check:
System > Preferences > Sound
System > Preferences > Multimedia Systems Selector
Speaker Icon in the Speaker Tray.

im been having the same problem with no sound in my headphones when plugged in, followed the advice above and have now have sound in my headphone:guitar:however the mic still aint working.  Will get there eventually

---

### Post by st0nes on 2007-07-17
Hi,

Is part of this conversation going on offline?  Seems disjointed.  Please post comments so the rest of us can benefit.  I bought a cheap laptop with bog standard onboard intel sound, and I get the sound of silence.  Nothing in this thread has helped. Device VT82xx.

---

### Post by Bob Bismal on 2007-07-20
> **st0nes said:**
> Hi,

Is part of this conversation going on offline?  Seems disjointed.  Please post comments so the rest of us can benefit.  I bought a cheap laptop with bog standard onboard intel sound, and I get the sound of silence.  Nothing in this thread has helped. Device VT82xx.

Nope, it's all there.  A lot of nice people trying to help, but with about 30,000 pieces to the equation, it's realllllly hard to find answers.  One reason I never wanted to work the help desk.

---

### Post by SPQQKY on 2007-07-20
```

alsamixer
```

go to analog/digital output and turn off

---

### Post by Bob Bismal on 2007-07-21
My sound card info from Windows.

Sound Devices
-------------
Description: Speakers (Realtek High Definition Audio)
Default Sound Playback: Yes
Default Voice Playback: Yes
Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0862&SUBSYS_11790106&REV_1000
Manufacturer ID: 1
Product ID: 100
Type: WDM
Driver Name: RTKVHDA.sys
Driver Version: 6.00.0001.5413 (English)
Driver Attributes: Final Retail
WHQL Logo'd: n/a
Date and Size: 5/10/2007 18:25:12, 1775712 bytes
Other Files:
Driver Provider: Realtek Semiconductor Corp.
HW Accel Level: Basic
Cap Flags: 0x0
Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
Static/Strm HW 3D Bufs: 0, 0
HW Memory: 0
Voice Management: No
EAX(tm) 2.0 Listen/Src: No, No
I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No

---

