---
title: "can i bypass get-edid somehow?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by rubbersoul.josh on 2008-01-08
I have an old compaq laptop (presario 2140us) that i am trying to install ubuntu 7.10 on.  i was having some issues with the live cd, so i gave the alternative cd a shot and completed the installation.  after install and reboot, i get an error that says:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

i choose yes and it says:

/etc/gdm/failsafexserver: line 47: [: too many arguments
Warning: Could not retrieve EDID because get-edid is not installed (1)

i click ok and then:

The X server is now disabled. Restart GDM when it is configured correctly.


after reading through the forums, i thought that it may be a problem with my graphics card driver. (ATI Radeon IGP 320M (ATI Radeon Mobility U1 )  i tried "sudo dpkg-reconfigure xserver-xorg" and "sudo dpkg-reconfigure -phigh xserver-xorg" in recovery mode; neither worked.

i then tried installing edid with:

sudo apt-get install read-edid

and it could not install.


i saw someone post that amd's (i have AMD Mobile Athlon XP 2200+ 1788MHz 256KB Cache) do not have edid.  is this true?  what does that mean for me? and what can i do get ubuntu running?  thanks a lot for your help!

---

### Post by chuckyp on 2008-01-08
run sudo dpkg-reconfigure xserver-xorg and try the vesa driver.  You should be able to get in the GUI then.  Or you can just install the proper video drivers right from console then sudo /etc/init.d/gdm restart after you are done.

---

### Post by dcstar on 2008-01-08
> **rubbersoul.josh said:**
> 
........
after reading through the forums, i thought that it may be a problem with my graphics card driver. (ATI Radeon IGP 320M (ATI Radeon Mobility U1 )  i tried "sudo dpkg-reconfigure xserver-xorg" and "sudo dpkg-reconfigure -phigh xserver-xorg" in recovery mode; neither worked.
.........

You will probably need to install the correct ATI driver for your hardware, I suggest you have a look at this:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by rubbersoul.josh on 2008-01-10
changing to the vesa driver worked!!

how is the vesa driver different, and does it allow the full functionality of my graphics card?  do you think i should still go ahead and still do the envy thing that dcstar posted a link about?  

thanks for your help so far.  i'm really happy to get this computer back on its feet.  (next i need to get the wireless card working, but that is another story)

---

