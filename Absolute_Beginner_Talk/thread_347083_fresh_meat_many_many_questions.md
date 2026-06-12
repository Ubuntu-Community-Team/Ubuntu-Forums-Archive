---
title: "fresh meat many many questions"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Daemion_AF on 2007-01-26
Alright let me just start off saying I am absolutely virgin to anything outside of windows, however after looking into ubuntu it interested me enough to install it on my dell e1705. After the installation I was absolutely amazed at the way it "feels" as an operating system. After checking out the packages that people have made I was flabbergasted. Anyways i just had to get that off my chest, noone i know is interested in linux and it makes me sick that something so nice is here for the taking and noone cares. Now, on to my questions. 1. I noticed under device manager that it doesnt pick up alot of my system hardware, everything works pretty well but what mainly concerns me is my dual core processor. If it doesnt "see" it in device manager or any other system utility program is it actually using it or is it not compatible? 2. My graphics card will go 1920X1240, will ubuntu support this resolution? 3. My wireless network is having alot of trouble with ubuntu, namely i dont think that it likes my wep psk protection. I know what my password is, but it seems like it is rejecting it. Other wireless networks without a password work great though. Do i need to disable the wep psk, or is there something im doing wrong? And last question. I liked ubuntu so much i decided to also install it on my girlfriends laptop, a toshiba satellite 4100xdvd. It meets the minimum system requirements but as soon as i get to the "select city time zone" screen the thing sits there and spins the disk for an hour without any changes. I ran the CD check and it comes out fine. Also i believe all hardware is good, it just took a clean install of XP but i would much rather run ubuntu on it if it will take. Any suggestions? Sorry for the long rant, thanks in advance for any help.

---

### Post by JayTee on 2007-01-26
Welcome to Ubuntu and the world of linux. I'm not a high level guru but I can try and help you out with some of your questions.
In regard to your dual core cpu, first of all if you are running Dapper you need to launch Synaptic and do a search for your current version of the kernel and select the 686-SMP kernel and apply your changes. You'll be prompted for a reboot when that finishes. If  you are running Edgy then you shouldn't need to do anything as the new 2.6.17-10 generic kernel has support for SMP and dual processors built in.
To verify both cores of your dual cpu are being recognized you can do either of the following,
GUI method: From the System | Administration menu choose System Monitor and click on the Resources tab. It should show CPU1 and CPU2 at the top of the window. 
Command line method; from a terminal type cat /proc/cpuinfo and press enter. It should show alot of info on your processors. If you've upgraded the kernel in Dapper or you are running 6.10 Edgy Eft and it still isn't recognizing your dual-core cpu then from a command line type this: SUDO UPDATE-PCIIDS and press enter then check again. 
For the wireless stuff I don't have alot of experience with working with WEP on them. Only in WIndows. You could always leave WEP disabled and just filter by MAC address on your wireless access point if that's an option.
For the Toshiba laptop I'd recommend trying to install from the Alternate CD which is available. It is more of a text based install and uses less memory overhead for the GUI. I have an older Compaq and had the same problem you're having. I was able to install Dapper although the laptop I have is constrained by having only 192MB of RAM so I chose to install Xubuntu which is great for older systems although it uses XCFE instead of Gnome and many people don't care for that desktop manager. I hang out alot in #ubuntuforums on IRC which is an informal chat. You can ask in #ubuntu which is the primary IRC chat support channel but it's usually very busy and your question may scroll off the screen before someone could read and answer it. Best of luck.

---

### Post by Daemion_AF on 2007-01-26
I apologize i did not mention i was running dapper...i guess this is 6.06 right? Anyways thanks for the help, both CPU's are there now one says cpu0 and one says cpu1. Why is it that any time that i update that it gives me another boot option for ubuntu when i get to that screen. I have like 3 of them right now, is this kind of like a backup of some sort? That is a good idea for the wireless i didnt even think of it, i will try to do that in a bit as i still need internet right now. I have one more question to throw in the fire, after researching i am finding that ubuntu does use drivers for things. Are the drivers card specific or does it just use generic drivers for stuff. I think if i can get the drivers for my graphics card working that it will display 1920x1240.

---

### Post by JayTee on 2007-01-27
Yes, whenever there is a kernel update it will save the previous kernel version to boot into in case of problems as well as the recovery mode option as well. It may save more boot options but you can remove those from grub by typing: sudo nano /boot/grub/menu.lst and editing the  options. Make a backup of menu.lst first by typing sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
If you get low on disk space make a note of the older kernel versions numbers and then by switching to root (sudo -su) you can delete the older kernel images in /boot to free up space.

---

