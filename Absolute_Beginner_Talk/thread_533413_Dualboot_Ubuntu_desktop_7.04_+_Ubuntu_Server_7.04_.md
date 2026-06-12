---
title: "Dualboot Ubuntu desktop 7.04 + Ubuntu Server 7.04 (and windows XP)"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Thorun on 2007-08-23
As for now, i have a dualboot with WinXP and Ubuntu FF v7.04. Trying to know Linux bit by bit.
First installed XP, then Ubuntu FF with GRUB as boot-manager. 

Now i have bought a old laptop (dell c600) that I want to use as a server on my local network. 
I have installed the Server with WinXP pro and managed to get the filesharing-ting to work with passwords and rights. It works wery well! As it is now, I cannot just unplug the server to play with the Linux-server-installation. My server has to be online 95-100% of time. 

Therefore I would like to use my secondary laptop (dell latitude x1), wich contains the dualboot with XP and Ubuntu FF as mentioned above, to play with the Ubuntu Server-installation. When I can manage to install the server, make it work, remote-controll it via SSF (of sst?) and do the FTP-sever-stuff, file-managing and so on, it is way more easy for me to do the same thing in much less time with my Server. And by doing it fast (because i have learned it on my secondary laptop) I can avoid long server-down-time. 

And now to the main question :D

Is it possible to do a tripple-boot with Windows XP, Ubuntu FF 7.04 and Ubuntu Server 7.04 ??
If yes; can it be done with an existing dual-booting system with XP and Ubuntu FF 7.04 ?


(Don't hope you got too confused by my description...:confused:)

---

### Post by m_atif on 2007-08-24
yes, it is possible to tripple boot (quadruple boot etc etc), with no problem. Just create another partition to install Server (or whatever) and install the same way as you did but this time on the new partition. Grub will takecare of everything.

Once you are good with linux, only then may i suggest to use Xen virtualization or VMware.

---

### Post by steve.horsley on 2007-08-24
Multi-booting is not a problem (I quad-boot at home). You will need to make a new partition for the new OS though, so you may have to re-size your existing partitions. The Linuxes can all share the same swap partition, and can share a common /home partition if you want.

Remember that GRUB uses files from /boot/grub, including menu.lst from one of the Linux partitions. If you install a second Ubuntu, that will probalby take over the main GRUB, so this will be the one with the active menu.lst. One problem with this arrangement is that any kernel updates to the original Ubuntu will make corresponding updates to its own (now unused) menu.lst, so you may have to keep the active menu.lst up to date on behald of the other Ubuntus. 

In order to avoid this confusion, I always install GRUB on the root partition of all my Ubuntu installations. Frinstance, If I have a system installed on /dev/sda6, I boot that system and run the command **sudo grub-install /dev/sda6**. Now this partition can be booted by chainloading in the same way a windoze partition can be chainloaded, and it always uses the local menu.lst to get the right name of the kernel file to boot. I then just configure my master bootloader to chainload the other partitions instead of direcctly loading a particular kernel. 

In fact my setup at home contains a Hoary system that contains the master menu.lst, and that I never actually boot except to use as a rescue system (it's faster than a rescue CD). My other Ubuntu systems (currently Edgy and Feisty) both have their own GRUB installed on their respective system partitions and get chainloaded by the Hoary GRUB.

---

### Post by Thorun on 2007-08-24
Wow. Thankyou for the great newz. 

As for the GRUB-problems - i think i stick with the default installation that Linux create itself (with GRUB on the root-partition). And just keep the new GRUB up to date with copying when a new kernel updates. 

I just want to play with the server-installation as it is for now. I'm kind of dependant, that the secondary computer (with the comming triple-boot) is somewhat stable and able to boot every time i press the power -button, and I'm pretty sure, that I will mess around and making my systems out of function if I'm trying the method you (steve.horsley) mention in section 3. 

But i like new challenges, and will definitely try the other boot-GRUB-method at a later time. :)
Thank you once again.

---

