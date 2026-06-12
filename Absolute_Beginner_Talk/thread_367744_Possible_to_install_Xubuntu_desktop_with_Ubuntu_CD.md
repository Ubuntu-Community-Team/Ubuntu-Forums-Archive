---
title: "Possible to install Xubuntu desktop with Ubuntu CD?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by ScooterDMan on 2007-02-22
I have mastered the art of installing Ubuntu 5.10 on my G3 Powerbook Wallstreet. Alas, it runs unbearably slow, given the mere 128MB of RAM and the 233mhz processor. 

Installing Xubuntu 6.10 (alternate) has proven problematic. It doesn't recognize my ethernet card and a slew of other things. 

So my question is, is it possible to run the Ubuntu 5.10 install, but somehow ask it to install the Xubuntu XCTE (sp?) desktop environment?

---

### Post by mahy on 2007-02-22
The easiest way is to install it is to boot your current ubuntu and run

sudo apt-get install xubuntu-desktop

Then you can choose between Gnome and Xfce at the graphical login (look for 'session'). Have fun!

---

### Post by ScooterDMan on 2007-02-22
OK, cool. That sounds doable. I am trying to run Xubuntu on a series of PB G3 Wallstreets.
So my approach for these should be:

1. Fully install Ubuntu 5.10
2. Boot into Ubuntu GUI.
3. Launch Terminal and run 
sudo apt-get install xubuntu-desktop

Would that do it?


And an additional question: Will the Xubuntu desktop environment also be limited to the 640X480 resolution I had with Ubuntu? Is there a fix for this?

---

### Post by mahy on 2007-02-22
> **ScooterDMan said:**
> OK, cool. That sounds doable. I am trying to run Xubuntu on a series of PB G3 Wallstreets.
So my approach for these should be:

1. Fully install Ubuntu 5.10
2. Boot into Ubuntu GUI.
3. Launch Terminal and run 
sudo apt-get install xubuntu-desktop

Would that do it?



It would. But i thought you've already completed the steps 1 & 2...

> 
And an additional question: Will the Xubuntu desktop environment also be limited to the 640X480 resolution I had with Ubuntu? Is there a fix for this?

That's a separate problem. You have to set it up in the file /etc/X11/xorg.conf There's plenty of info around regarding X server configuration.

---

### Post by ScooterDMan on 2007-02-22
I have completed steps one and two on my first machine. I have two more that I am trying to get working again for the high school where I work.

---

### Post by ScooterDMan on 2007-02-22
I followed these steps, but nothing has changed. It still looks like Ubuntu after reboot. I thought by downloading that package and rebooting it would put me in the Xubuntu environment?

---

