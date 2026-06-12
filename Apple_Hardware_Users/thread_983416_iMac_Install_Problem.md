---
title: "iMac Install Problem"
date: 2008-11-15
forum: Apple Hardware Users
---

### Post by cmmcnamara on 2008-11-15
Hi I am trying to install Kubuntu 7.10 on my girlfriend's iMac so that she can use Wine as she does not own a windows liscence. She purchased it only 5 or 6 months ago configured with an Intel Core 2 Duo at 2.8GHz, 2GB of RAM, the 8800GS video card and a 1TB hard drive on a 24" screen. The problem I am having is that I cannot get the live CD to boot into the live desktop for installation. It will boot the CD's bootloader and I can load from there but the desktop will not start and I therefore cannot install. I am able to use the text based portion and after I use the command "startx" the initialization is halted returning the error "no screens found". Can anyone direct me where to go from here? Thank you in advance.

---

### Post by Ztoph on 2008-11-17
I am having the exact same problem, if you find out how to do it, please help me.

---

### Post by cyberdork33 on 2008-11-17
Please determine and post your full Mac version as described here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by moviemaniac on 2008-11-18
when you boot from cd, select the safe video mode from the options menu. That did the trick for my on my iMac with the ATI 2600XT. After installing Ubuntu you an install the proprietary drivers for the graphics card to work properly.

---

### Post by Ztoph on 2008-11-18
How do you select the safe video mode? when i press the options menu, i only get a line of code...

---

### Post by moviemaniac on 2008-11-18
press F4 in the menu you get when you boot from cd and select "safe graphics mode". Don't let the distorted display bother you when you boot the live-cd, you an fix this after installing by activating the proprietary drivers.

---

### Post by x0as on 2008-11-18
If the only reason for installing kubuntu is for wine, why not just install wine on os x?

---

### Post by Ztoph on 2008-11-19
> **moviemaniac said:**
> press F4 in the menu you get when you boot from cd and select "safe graphics mode". Don't let the distorted display bother you when you boot the live-cd, you an fix this after installing by activating the proprietary drivers.

I tried it, but it didn't work. The cd begins spinning, but nothing happens, so after an hour, i turned off my iMac and tried again with the same result.

---

### Post by Ztoph on 2008-11-19
Today i tried with an Ubuntu live cd (7.10), and when i pressed install, it opened something called a Busy Box, and i just didn't know what to do. Can anyone help me? By the way, i determined my iMac, and it was the 8,1..

---

### Post by Ztoph on 2008-11-20
What should i do in the Busy Box?

---

### Post by hart02 on 2008-11-20
cmmcnamara,does your girlfriend want linux on her imac? if she wants it just for wine then try [Darwine]("http://www.kronenberg.org/darwine/")

---

### Post by Ztoph on 2008-11-21
I tried searching around the net, but i can't find anything about people having problems with installing ubuntu/kubuntu on their iMac. I also tried to find some informations about the BusyBox, but i can't understand it. So my problem is: When i boot from my Kubuntu 8.10 Live CD, i press the "Try kubuntu without affecting your pc", nothing happens. I have tried to change the graphic settings, but nothing helps. I have also tried with an ubuntu 7.4 Live CD, and it just openes the BusyBox after i presssed "install". What can i do to make it work?
I have the new alu iMac 8,1.

---

### Post by cyberdork33 on 2008-11-21
verify your install disc.

---

