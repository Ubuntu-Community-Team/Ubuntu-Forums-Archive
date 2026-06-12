---
title: "[SOLVED] Wine not installing on gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by glantela on 2007-10-22
I followed the instructions on winehq, and this is what i got from the terminal:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
E: Broken packages

Can anybody help me out?

Thanks!

---

### Post by heinig on 2007-10-22
Did you try to install it using Add/Remove softwares under the Applications menu?
I did yesterday and it worked.

---

### Post by glantela on 2007-10-22
This is what i get in the add/remove section...

"This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

I dont know what to do in synaptic to resolve it...

---

### Post by heinig on 2007-10-22
Did you completely uninstall the other version? (I'm assuming that you have installed something following the website instructions)

---

### Post by TadH on 2007-10-22
I would try uninstalling whatever you have for wine on there now and in the terminal type
sudo apt-get install wine


that worked for me my first time.

---

### Post by aljatrad on 2007-10-22
I am a new user and know little but did/still have 7.04 working great.

My spare machine for there type of experiment is:
Intel 2.4Ghz processor on Intel Motherboard
512 DDR RAM
GeForce4 MX 440 graphics
40 Gb HDD
DVD burner

I Installed 7.10 as new install, all seemed to go well and on completion had what seems a full and working system. Now we come to the sorry bit.
There in no add and remove item at the bottom of the applications list, there is no synaptic item in System/administration. I have tried adding packages via the terminal and it accepts the command and prompts for the password but will not let me type the P/W in to the terminal.
I see there is a lot of talk about Nvidia not loading in many systems, my card installed fine. It is a Nvigia GeForce4 MX 440 and I am running 1280 X 1024 resolution, not a great card but it works.
Can anyone make some suggestions to a newby, should I continue trying to get 7.10 going or revert to 7.04 Why are the bits missing, how can I install programs without the missing bits and get passed the password prompt in apt terminal.

---

### Post by glantela on 2007-10-23
yea, i guess i had another wine installed on one of my hard drives... because of the way i installed gutsy... i'd rather not get into too many details... its a little embarrassing.... :)

Thanks a lot guys

---

### Post by Maestro23 on 2007-10-23
> **glantela said:**
> yea, i guess i had another wine installed on one of my hard drives... because of the way i installed gutsy... i'd rather not get into too many details... its a little embarrassing.... :)

Thanks a lot guys

Good deal.  Please mark this thread SOLVED using the Thread Tools.

Thanks.:)

---

