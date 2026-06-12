---
title: "Can't boot! xserver failed to start"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by tommason on 2007-08-14
Hey,

After a little rough and tumble last night i eventually installed ubuntu feisty onto my old pc. Had a little tinkering to do with the nvidia drivers to get it to except my lg l194wt flatron widescreen monitor and it's 1440*900 resolution, but got that sorted by installing envy. Rebooted, all started fine, set up my new desktop with some nice wallpaper and went to bed dreaming of bill gates free living. 

Woke this morning with a humming coming from somewhere in the house, turned out it was my old pc which was still running. Hmmm, turned it off at the power and went to work. Got home tried to start it up and got  a:
 'failed to start the xserver....'

 dialogue - searched that out on these forums and found my way to the advice:

1.   find out your graphics card (lspci in command line=geforce2 mx400)2.  Type in "sudo dpkg-reconfigure xserver-xorg" which i did and picked nv as my driver and followed the 'line of least resistance' through all the preceding stuff.

Attempted to 'start her up' and got exactly the same answer..... 'failed to start the xserver....'
apparently it is unable to find a valid framebuffer device.

Any ideas? (bearing in mind I'm very new to ubuntu)

Cheers!

Tom

---

### Post by Alterax on 2007-08-14
Try setting it to the VESA driver.  That should get you into X in the meantime.

---

### Post by tommason on 2007-08-14
ok - will do....how do i restart after I've done this?, I've tried typing 'shutdown' without much luck, so i just hit the reset button..... :)

---

### Post by yellowband on 2007-08-14
did you happen to back up your xor.conf file before you changed your graphics settings and drivers?

if so replace with the original xorg-conf file.

cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by tommason on 2007-08-14
> **yellowband said:**
> did you happen to back up your xor.conf file before you changed your graphics settings and drivers?

if so replace with the original xorg-conf file.

cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

no i didn't :oops:

---

### Post by tommason on 2007-08-14
> **Alterax said:**
> Try setting it to the VESA driver.  That should get you into X in the meantime.

yeah, has done, cheers...any ideas for the nvidia driver?
Also it doesn't seem to turn itself off when i go to 'shutdown' just hangs on the ubuntu unloading screen, progress bar moves to the right, ends up black and hangs.....

---

### Post by captainwitherspoon on 2007-08-25
Hi, I'm having this exact problem and would really appreciate some help!
Did you fix yours? I tried running dpkg-reconfigure xserver-xorg and setting it to the vesa driver without results.

---

### Post by ritterrav on 2007-08-25
Where you messin with compiz fusion by any chance?

---

### Post by captainwitherspoon on 2007-08-25
Well, I was about to, I ran envy and it seems to have screwed my system. Is there anyway to just undo what it did?

---

### Post by nonewmsgs on 2007-08-25
well what i would do is go one step at a time to get back to where you were remembering how to get back if you fall.
do the restricted drivers 
then try to manually adjust your xorg.conf with 
sudo gedit /etc/X11/xorg.conf
and add your main resolution in front of all the resolutions listed on the bottom

---

### Post by Bout to Snap on 2007-08-26
> **captainwitherspoon said:**
> Hi, I'm having this exact problem and would really appreciate some help!
Did you fix yours? I tried running dpkg-reconfigure xserver-xorg and setting it to the vesa driver without results.

I installed an Old Gforce2 Mx200 today in this pc..was using and ATI Radeon 9250...that blew this 32 mb card's making it look bad...anyhow this is how i got past the x server problem

when ubuntu's booted with NO GUI just type _envy -t _Uninstall Nvidia's drivers after uninstalling them reinstall, seem to work fine for me and after ubuntu's back in GUI run envy to set up the rest of the stuff you want.

---

### Post by captainwitherspoon on 2007-08-26
I fixed it! I just ran dpkg -reconfigure xserver-xorg to get my GUI back then reran envy and all seems well, thanks for the help.

---

### Post by smo0th on 2007-08-27
I run an old AMD K6-2 450 with a generic PCI trashy video card, my problem was that the card was not able to display the default 24-bit graphic mode LOL.... so here's a recreation of what I did... 

first get into command shell mode and do the "sudo dpkg-reconfigure xserver-xorg" thing...

now type "sudo nano /etc/X11/xorg.conf"

scroll way down to the line where says DefaultDepth      24

I changed it for 16... you may play along with the values there but always keep a backup file before modifying anything.... just in case ;)

c-ya.

---

### Post by vpjr on 2007-08-27
hi tommason,

i'm interested in figuring out the original problem. if you don't mind, please post the xorg.conf that failed and your BIOS settings. thanks.

regards,

ven

---

### Post by vincentvee on 2007-08-27
type this:
sudo reboot


> **tommason said:**
> ok - will do....how do i restart after I've done this?, I've tried typing 'shutdown' without much luck, so i just hit the reset button..... :)

---

