---
title: "3 annoying bugs"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by ducttapemasterJ on 2006-08-14
#1 Ok so I have my screen resolution set to 1280 by 1024, but very often whenever I shut down or reboot the resolution comes back stuck on some very low resolution and doesn't let me change it.  I end up having to reboot several times until it randomly comes back up in the 1280 by 1024 setting.  

#2 Seems like whenever I leave my computer alone for several hours, it up and decides to reboot itself which is very annoying

#3 Whenever my computer goes into screensaver it locks up and has to be manually restarted. 

Any ideas? 
Thanks

---

### Post by jincast90 on 2006-08-14
> **ducttapemasterJ said:**
>  
#2 Seems like whenever I leave my computer alone for several hours, it up and decides to reboot itself which is very annoying
Thanks

Turn it off then. Its just wasting power.

---

### Post by ducttapemasterJ on 2006-08-14
Well, I have several good reasons for wanting to keep my computer on all the time.  If anyone knows a way to fix the problem of it shutting itself off I'd really appreciate the help. 
thanks

---

### Post by griff01 on 2006-08-14
Hey ducttapemaster

No answers but I'm struggling with exactly the same problem.

As a mid-level user this is the biggest barrier to me using linux - guys this screen res thing must be resolvable.

I need 1280 x 768 and have been struggling for 10 days to get it to stick.

Still using Windose because of it.

Griff

---

### Post by geokok1981 on 2006-08-14
Specify your harware components and say if u have messed with any files in the system. Maybe then someone will be able to figure something out.

---

### Post by ducttapemasterJ on 2006-08-14
Well, Im pretty much a newbie, so Im not really sure what hardware components are relevent.  I've done very little messing around with system files since I really don't know what Im doing.  
I have a GeForce 4 video card if that helps anything..

---

### Post by kaamos on 2006-08-14
1) Have you tried installing different drivers for your video card? See [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

2) No idea, sound like overheating to me..

3) Might be related to 1 (for example an OpenGL screensaver tries to start and causes trouble because of the drivers are bad for your card).

Hope this helps.

---

### Post by geokok1981 on 2006-08-14
in a terminal type:
lspci
and post here the output.It should include your devices. Have installed vga drivers?To check if they are working properly in a terminal type again:
glxinfo
and see if it says "3D--->yes" or "no".

Also, (just to be on the safe side) clean the pc from dust with a blower:rolleyes:

---

### Post by steve.horsley on 2006-08-14
If X cannot figure out your monitor frequencies as it starts, it defaults to a safe 640x480, which is a PITA. It finds those frequencies in one of 2 ways:

1) Ask the monitor. Most monitors these days can be queried for their refresh rates. Starting X with the monitor disconnected (perhaps by a KVM switch) defeats this of course.

2) Consult the /etc/X11/xorg.conf configuration file. It is possible to put the frequencies (HorizSync and VertRefresh) in the **monitor** section although the default install doesn't do so.

So I guess adding the correct frequencies to your config file should sort that out. Here is mine as an example:
> Section "Monitor"
        Identifier      "E-171"
        Option          "DPMS"
        HorizSync       24-80
        VertRefresh     49-75
EndSection
but you really should make sure you have the right frequencies, and back up the file first, just in case.

Are you sure 2 and 3 aren't actually the same problem - screensaver causing crashes? I had this on an pld PC.

Along with the intermittent reading of screen frequencies, I wonder if your video hardware is a bit flakey.

---

