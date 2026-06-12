---
title: "ATI vid card sticky instructions not working help!"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by McGatsby on 2007-07-09
i have an ATI x series vid card and have gotten through the instructions that are listed in the sticky up until after the reboot. it tells me that "I cannot start X server (your GUI) Its likely thats its not set correctly. Would you like to view the X server output to diagnose the problem".

so i look at it (as a linux newb they don't mean too much.. although the more i read the move i kinda understand..) then click ok. it asks me to look at something else related to the x server then tells me to try again when the problem is fixed (sorry that's me paraphrasing). so i log in and see (myname)@ubuntu:~$.

so i try to put in the codes listed in the sticky instructions and get "E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable) E: Unable to lock the list directory" even tho the first part didn't work i did fiddle around withthe other code lines.. but they didn't work either. i've come a long with with this install since not getting the live cd to work to using the alternate to not being connected to the internet (something about my network not using DHCP(?) to figuring out for the first time ever how to figure out my ip address... (in the spirit of full disclosure, I did have issues in the "configuring the network for DHCP" step and did a manual config... so maybe it didn't work??) i feel like i'm ALMOST there!! i've figured alot of this out on my own, but i can't seem to get past here. i've read other peoples posts.. and there are so many suggestions, i don't know where to start! please help me...

i really hate vista and was looking forward to using ubuntu on my laptop. oh in case it helps here are the stats for my laptop..

Toshiba Satellite Notebook
Processor Brand 	AMD Turion(TM) 64 X2
System Memory (RAM) 	2GB
Hard Drive Type 	Serial ATA (4200 rpm)
Hard Drive Size 	250GB
Graphics 	ATI RADEON X1200
Video Memory 	128MB - 319MB dynamically allocated shared
Networking 	Built-in 10/100 Mbps Ethernet (RJ-45 connector)
Wireless Networking 	Built-in Atheros high-speed wireless network connection (802.11b/g)

---

### Post by FNDII on 2007-07-09
I am having a problem with my ATI x800 display as well. I cant install it or even use the live aspect. I have to use the "safe grafics mode" and answer all of the questions. When is asks the question about color depth, every option boots me to the command prompt.

---

### Post by McGatsby on 2007-07-26
if someone could please help me still that would be great. i got no responses except for that guy who just said he had the same problem.... but i'm still at a loss. is it just my computer that's not compatible? am i not doing a step that i should be? please help me.

---

### Post by Ek0nomik on 2007-07-26
> **McGatsby said:**
> i have an ATI x series vid card and have gotten through the instructions that are listed in the sticky up until after the reboot. it tells me that "I cannot start X server (your GUI) Its likely thats its not set correctly. Would you like to view the X server output to diagnose the problem".

so i look at it (as a linux newb they don't mean too much.. although the more i read the move i kinda understand..) then click ok. it asks me to look at something else related to the x server then tells me to try again when the problem is fixed (sorry that's me paraphrasing). so i log in and see (myname)@ubuntu:~$.

so i try to put in the codes listed in the sticky instructions and get "E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable) E: Unable to lock the list directory" even tho the first part didn't work i did fiddle around withthe other code lines.. but they didn't work either. i've come a long with with this install since not getting the live cd to work to using the alternate to not being connected to the internet (something about my network not using DHCP(?) to figuring out for the first time ever how to figure out my ip address... (in the spirit of full disclosure, I did have issues in the "configuring the network for DHCP" step and did a manual config... so maybe it didn't work??) i feel like i'm ALMOST there!! i've figured alot of this out on my own, but i can't seem to get past here. i've read other peoples posts.. and there are so many suggestions, i don't know where to start! please help me...

i really hate vista and was looking forward to using ubuntu on my laptop. oh in case it helps here are the stats for my laptop..

Toshiba Satellite Notebook
Processor Brand 	AMD Turion(TM) 64 X2
System Memory (RAM) 	2GB
Hard Drive Type 	Serial ATA (4200 rpm)
Hard Drive Size 	250GB
Graphics 	ATI RADEON X1200
Video Memory 	128MB - 319MB dynamically allocated shared
Networking 	Built-in 10/100 Mbps Ethernet (RJ-45 connector)
Wireless Networking 	Built-in Atheros high-speed wireless network connection (802.11b/g)

The "E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable) E: Unable to lock the list directory" error should be fixed by a simple reboot.  This usually means that a package manager such as apt was improperly killed (closed).

How far in the instructions with the sticky did you get? I presume the...

```
sudo apt-get update
sudo apt-get dist-upgrade
```

commands are what brought you to a hault given your error messages.

Try restarting to get rid of the lock, than continue with the instructions.

---

### Post by Ek0nomik on 2007-07-26
If you don't wish to restart, you can also issue this command:

```
sudo killall dpkg
```

and then try to run the commands from the top again in the instructions.

---

### Post by RangerDanger on 2007-07-26
In order for the instructions in the sticky to work, you MUST be connected to the internet.  Easiest way for the sticky to work is to plug directly into a network with an Ethernet cable.

---

