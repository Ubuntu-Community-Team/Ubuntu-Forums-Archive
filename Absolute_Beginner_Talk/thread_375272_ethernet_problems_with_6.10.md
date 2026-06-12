---
title: "ethernet problems with 6.10"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by jimini on 2007-03-03
Hello Guys and Gals,
 I have installed Ubuntu 6.10 recently on a machine that Ii bought for the purpose of installing linux onto. It came with windows XP pro. installed and i wiped that out with the install of Ubuntu. everything seems to worh except for the fact that my ethernet card was not detected. (it worked fine with XP). I have searched the forums for advice and have tried everything that was offered to no avail. (ismod, ifconfig, and a few that i do not remember). I reinstalled overwriting the old partition. I would really like to use linux instead of windows ( I have to keep windows on one machine for AutoCad and Photoshop but i would like linux to be my os of choice. However if i can't access the internet with it it would be useless to me. i know it can be done because you folks are doing it. It seems that i need some help. I need it to be step by step in simple language if possible as i am new to linux please do not assume that i know what the next step is. I know that this post will probably garner some distain (from some of the rude replies that i have seen) but i trust that one of you human becomings will fill me in and help me out. thank you for your patience and for sharing your knowledge with me. Now if someone will read this and help me find my ethernet card the next post from me will be on my Ubuntu Linux machine. 
Jim

---

### Post by Stemp on 2007-03-03
Hi Jim,

What version of Ubuntu are you using ? 
Do you know the name of your ethernet card ? 
Open a terminal in Linux and type this command :
```
 lspci | grep Ethernet
```

---

### Post by jimini on 2007-03-03
Thank you for your prompt reply. I am using edgy 6.10 and i have no idea what card is in the box. I typed the code into the terminal but nothing visualy happened the terminal just went to the next line.

---

### Post by Stemp on 2007-03-03
Is there a way in Windows to know the name of the ethernet card (or even the driver) ? 
Maybe you know the name and model of the computer and/or motherboard ?

---

### Post by sailor2001 on 2007-03-03
in windows, download belarc to audit your system that will give you all the data of your hardware

---

### Post by jimini on 2007-03-03
the only operating system on the machine is edgy UBUNTU 6.10, so windows anything is not an option. the motherboard is an "ELITEGROUP- P4M800PRO-M" Intel Pentium D Processor. I have the install disc for the motherboard if that helps.
Jim

---

### Post by Stemp on 2007-03-03
Well after a little research it seem to be a  VIA VT6103L 10/100 Mbps Fast Ethernet. 
And it should work out of box :(
So maybe you just find out a bug in Ubuntu 6.10, if you have time try with the new testing version of Ubuntu Feisty.

---

### Post by jimini on 2007-03-03
It would be my luck to find such a bug. I will try fiesty and if that doesn't  work i'll go to mandriva or fedora i guess. Thank you very much for your time and trouble.
Jim

---

### Post by t3chb0y on 2007-03-04
I'm planning to buy a motherboard by Jetway for a VIA C7 Processor and it has the same LAN chipset...

Is there any patches for this ethernet problem or any quick workarounds?

---

