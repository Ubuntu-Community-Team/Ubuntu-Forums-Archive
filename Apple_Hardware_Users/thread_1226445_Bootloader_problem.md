---
title: "Bootloader problem"
date: 2009-07-29
forum: Apple Hardware Users
---

### Post by mattgaunt on 2009-07-29
Hey everyone,

I've been trying a number of combinations to get mac os x, Ubuntu 9.04 working on my Macbook 4.1 with rEFIt.

I have never had this sort of trouble before, but basically I use bootcamp to create the spare partition, I then load ubuntu onto this spare partition (tried using the alternate and live CD), I have tried skipping installing GRUB, installing grub on hd0 (which broke Mac OS x from working and required fixing through disk utility), I tried installing it on /dev/sda3 on the live CD as suggested here ([https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)) but that broke mac os x from working again.

The closest I get to working is when I get rEFIt installed and working after a ubuntu install and when I click on the linux icon it goes to a black screen saying "Loading GRUB stage2:" and then my macbook restarts.

Now is this a problem with my Macbook, a problem with jaunty or am I doing something blindingly obvious?

Any help would be greatly appreciated - I miss my ubuntu install

---

### Post by JOHNNYG713 on 2009-07-30
Hi I'm a little confused, You use the term "grub" in reference  to your boot loader, ppc uses yaboot, any way, If  you don't care about the way your boot screen looks , just load ubuntu and let yaboot handle the rest, (no need to fuss if all you want is functionality) you will probably have install issues with 9.04 , I load 8.04 first and upgrade from there, I dual boot mac and ubuntu no problem on any mac I have loaded with ubuntu! :D

---

### Post by mattgaunt on 2009-08-10
Whats yaboot? Grub has always bn the default boot loader for Ubuntu hasnt it?

Apologies for the late reply i thought a had subscribed to this thread but apparently not.

---

### Post by mattgaunt on 2009-08-10
Ok I have just done a fresh re-install of Mac OS X on my laptop, I then installed Ubuntu Jaunty using the Live CD as the instructions in the sticky say for intel macs and when I boot into Ubuntu it shows the loading Grub 2 message and then the machine just restarts.

Has anyone else had this problem? Im going to just try loading it several times to see if this problem fixes itself as suggested somewhere on ubuntu site but no one else seems to get this problem and im not doing anything out of the ordinary.

Am I totally missing something?

*Edit: The restart happens after the message GRUB Loading Stage2 ...

---

### Post by mattgaunt on 2009-08-12
Hey everyone just to let anyone who comes across this know

I got Jaunty installed but installing an older version of Ubuntu (As johnnyg suggested, Thank you soo much your a life saver) and then upgraded from their.

I actually ended up installing intrepid (8.10) without any problems, so my guess is there is a problem with installing GRUB on the MacBook through the current Jaunty CD.

Anyone know if I should file a bug report?

---

