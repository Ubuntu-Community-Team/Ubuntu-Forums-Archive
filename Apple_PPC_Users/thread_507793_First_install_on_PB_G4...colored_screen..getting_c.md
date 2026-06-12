---
title: "First install on PB G4...colored screen..getting crazy"
date: 2007-07-23
forum: Apple PPC Users
---

### Post by markeire on 2007-07-23
Hi guys,

I'm completely new to Linux, I have tried to install Ubuntu on my PB Titanium G4, I have chosen the PPC version (it's a PPC) it would be the only OS on my PB (so one partition). I have tried both the standard and alernative version of images available.  Run the installation, looks fine, remove the cd, then I reboot the machine,I can see the black screen with the UBUNTU loading bar moving (as it should be, I think) then....that's the issue:

once the bar is loaded instead of having the login tabs/boxes (i guess) what I'm getting is a screen which is coloring form purple to green (fuzzy colors) with a small black portion on the right side of the screen and nothing is happening! I have tried in different ways but still getting this issue, what might be the problem? Is something related to the CD image?Video drivers?:confused:

I also attached a picture of the screen probably it will help

I really appreciate your help!

Thanks a mill
Mark

---

### Post by tonyr on 2007-07-24
This sounds like a video driver issue. Which G4 Ti?  Which version of Ubuntu? I think all the
video controllers in the Ti machines are ATI, but different versions as the Ti evolved.

You can try this:  When booting, watch for the text 'boot:' prompt, and type in
**linux video=ofonly**.  This is supposed to bypass the video driver and use
the basic OpenFirmware video.

The other thing you can try is this.  At the point that the screen goes all wonky, try
pressing Ctl-Alt-F1 to see if you can get a virtual console (text only).

- tony

---

### Post by markeire on 2007-07-24
Hi Tony,

thanks for your reply, I have a G4 Ti 400 Mhz (the very first one), I have installed the Ububtu v. 7.04 which I think is the latest one, yes the video card is an ATI 8MB.

Enetring the  linux video=ofonly doesn't help, but i did manage to get the console screen again by pressing ctrl+alt+f1, at this stage I have entered my username and password but now i'm in front of the sudo commands...which one do i need to use to start the graphical interface or to run the os successfully??

Thanks a mill
Mark

---

