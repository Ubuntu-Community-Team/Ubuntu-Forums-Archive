---
title: "Replaced ATI with Nvidia video, problems."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-20
After replacing ATI and booting up I lost the dexktop.  I managed to get it back with a generic driver.  Then I clicked system > administration and activated the restricted driver.  In the middle of down loading and installing.  The process aborted and told me that install could not be completed.  
So I downloaded envy .  I selected install Nvidia.  It seemed to work but when I tried to run nvidia-settings I received a not found message.  So I used envy to uninstall nvidia.  Now I  install Nvidia again with envy still can't run twinview and in looking thru xorg.conf only see generic.  Also, if I try t adjust the screen resolution the best I can get is 1074x768.  I have a 19" viewsonic lcd.  I think that I need some help here.

---

### Post by Golyadkin on 2007-06-20
Uhm, to begin with: what brand of graphics card do you have in that computer? ATi or nVidia? If you have a ATi card, you cannot install nVidia, and vice versa.

---

### Post by Happy_Man on 2007-06-20
Tried ```
sudo dpkg-reconfigure xserver-xorg
``` yet? That should at least get you a functional, generic desktop back. Then try downloading the drivers again.

---

### Post by ICUR2Ys on 2007-06-20
I replaced the ATI with an Nvidia graphics card.

---

### Post by ICUR2Ys on 2007-06-20
I entered sudo dpkg-reconfigure xserver-xorg
again,  and when clicking system > administration > restricted drivers I get the message that my system does not need restricted drivers.  I wonder if a fresh install is required?

---

### Post by Happy_Man on 2007-06-20
Just for kicks, go to Synaptic and search for "nvidia-glx". See if any of those packages are already installed. If so, no need to install them again.

---

### Post by ICUR2Ys on 2007-06-20
Synaptic showed that they were not installed so I tried to install it.  Got this message.

Well I had copied the message and cleared the screen  when I tried to paste the message I couldn't.  The message was 2 and 1/2 lines long.  that last part said error 2 or level 2.  Sorry I can't remember.  Thought I had it copied.

---

### Post by ICUR2Ys on 2007-06-20
OK I ran synaptic again and here is the message.

E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.28_i386.deb: subprocess pre-installation script returned error exit status 2

Something is wrong with my system.  I don't know if we can straighten it out or if I need to do a fresh install.  What do you guys think?

---

### Post by Happy_Man on 2007-06-20
Try sudo apt-get update..... if that doesn't work, *then* we have a problem.

---

### Post by ICUR2Ys on 2007-06-20
That didn't work.  I have done a fresh install, and am rebuilding.

---

