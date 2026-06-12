---
title: "Kubuntu won't start right"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by otterstrom on 2007-06-18
Hi

I recently installed Ubuntu Fiesty Fawn. Last week I installed Kubuntu using the Synaptic Package manager and selecting "Kubuntu-Desktop". During the installation I selected kdm as my default manager. Everything went smooth the first time I booted up, and I definitely prefer KDE. 

Later that day I came home from school and booted up again and I got a Kubuntu splash page that was on screen for quite a while and then I got a black screen with a flashing cursor but no command prompt. After trying a couple of things I pushed the power button which then led to the Kubuntu flash screen and the computer shut down.

I tried starting up again a few times with the same result. 
Then I tried starting up with a different kernel. On my Grub loader page I have two kernel options, 2.6.20-16-generic and
2.6.20-15-generic. When I select "15" then I get an Ubuntu splash page (instead of the Kubuntu splash) and the and the kdm loads just fine and I am able to select a gnome or kde session and log in just fine. However the system seems to spend a long time on the Ubuntu splash page.

can someone help me solve this problem when I select the default "16" linux kernel and I would also appreciate any advice about whether I should install a kernel more tailored to my hardware. (I have a Vaio laptop with a Centrino processor 1.73 Ghz)

Thanks
Jared

---

### Post by Clay_Banger on 2007-06-18
if you only recently installed ubuntu, and havent modded it to much, i would suggest a reinstall rather then picking through things and fixing it all up.

---

### Post by Austin_KW on 2007-06-18
One of my PC has developed KDE problems on shutdown (not the same as you) but disabling splash fixes it for me. Try removing splash by editing in the grub menu (enter "e")

You could try reconfiguring KDM again, 
sudo dpkg-reconfigure kdm

Also try switching to a terminal when KDE does not start (ctrl-alt-f1) and check the output of dmesg and the log files in /var/log

---

### Post by otterstrom on 2007-06-19
I have no problem re-installing, I only worry about how it works since I have a partition with Windows XP on it. If I put the installation disc in, will I be able to reinstall over the existing Ubuntu partition without affecting the windows partition?

Thanks for your responses

---

### Post by Clay_Banger on 2007-06-19
i think that the auto option during setup will just wipe the entire drive, so you may need to use the manual partitioner to achieve what you are after.

---

### Post by guitodd on 2007-06-19
I had various issues loading both K and Gnome together.  Splash screen weirdness.. There are some posted fixes for some of these issues somewhere in the boards here.

If you Like KDE.. I would recommend doing a fresh install with Kubuntu..  not Ubuntu.

---

### Post by otterstrom on 2007-06-19
I will try a fresh install of  Kubuntu when I get some time to backup my files already on Ubuntu.
Thanks
jared

---

