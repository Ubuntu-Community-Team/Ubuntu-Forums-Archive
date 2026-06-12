---
title: "Running Ubuntu 11.1 without a graphics card"
date: 2012-02-01
forum: Any Other OS
---

### Post by stanek on 2012-02-01
Why?
I have enough hardware to make two computers except only one video card.  

-----

I am running Ubuntu 11.10 which is configured to auto log-in and x11vnc which is configured to auto start.  My bios is set to not halt on errors.

When I have the video card in, this setup works without any input needed on the Ubuntu machine.

----

When I remove the video card the computer gets to the stage where I hear the hard drive doing work and I also get a ping back response from the Ubuntu machine.  The numlock on the keyboard is also responsive.

However VNCViewer (win7) returns an error 10061 connection refused and the Default Remote Desktop in linux mint returns 'cannot connect'.

----

The fact that the computer responds to the ping request is quite promising.

I imagine there might be an error / dialog box appearing.

I am looking for ideas.  

Most google results turn up saying a computer wont even POST without a graphics card so I am having a hard time finding answers throuh the misinformation.

Thanks

---

### Post by stanek on 2012-02-01
I left the computer alone for a while and then pressed ctrl+alt+del and then enter.  To presumably logout, and there was quite a bit of hard drive activity for 20 or so seconds.  If this helps anyone.

---

### Post by Perfect Storm on 2012-02-01
Moved to Other OS/Distro Talk.

---

### Post by Double.J on 2012-02-01
Hi there are you able to see the grub bootloader and boot into recovery mode? It's hard to say what display you can run without knowing the onboard graphics capabilities, but most recent desktop mobo's should be able to run ubuntu in 2D mode (which would be the default start up)

If you can't see the Grub prompt, then there's probably something wrong in the BIOS, and if you can't get into the BIOS, then with the onbord graphivcs/connection/display/mobo!

All the best :)

---

### Post by stanek on 2012-02-01
The computer works fine with the video card installed.  
I am trying to vnc into the computer when I remove the graphics card.  

There is no onboard graphics chip.  To be clear when I remove the graphics card, there is no monitor cable connected to the computer. 

There is hard drive activity and a short while after powering on, I am able to ping the computer.  It is reaching some part of the OS but the x11vnc script that is in the startup directory is not being run.

Perhaps ubuntu is detecting the missing card and entering a 'safe' mode?

---

### Post by mips on 2012-02-02
telnet/ssh into the for starters, you could also access it via serial console so you can work on it so long.

---

### Post by jay123035 on 2012-09-18
i know this is after that fact but maybe it will help the next person. 

your system is booting and working fine. the problem your having and that i have is that with out the video card the x server doesn't start. with out that no x11. no x11vnc.

if your still working on this than we both need to find a way to run the x sever from memory (xvfb) or run a x sever on your client machine. but how you get any of that to work i don't know.

---

### Post by QIII on 2012-09-18
This is a bit old, but in case someone stumbles across it...

Try installing the xserver-xorg-video-dummy package.

Your available resolutions will be limited.

---

