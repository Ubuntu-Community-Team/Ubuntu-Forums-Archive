---
title: "Xorg.conf Problems with Nvidia video card Ubuntu"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by kickerkeeper on 2007-03-15
Hi all. I'm very new to Linux and I am currently in the process of getting my video card and wireless card up and running. My wireless card worked fine out of the box. After that I tried to install my video card. These are the steps I took:

1-Followed the steps on the following site: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29") 

2-Rebooted my computer without the video card and right before it loaded the login screen I got a blue background with a box saying the following: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? <YES> <NO>"
I turned off the computer.

3-I then put the GeForce FX 5500 graphics card in the PCI slot and rebooted. Everything booted up fine it gave me the correct login screen and Ubuntu worked normally. Except I no longer was able to connect to the Internet. I am using a Belkin Wireless G Desktop Card with the Atheros chipset. I then opened a terminal and typed iwconfig it gave me the following:

lo       No wirless extensions
eth0    No wirless extensions
sit0    No wirless extensions

That was it, nothing showing the wireless card.


4-I then rebooted again without the video card and arrived at the same box in part 2 above. I selected NO and was brought to a black and white screen that asked for my login and password at the command prompt. I entered it and it gave me the usual terminal prompt on a black and white screen (as though I had just opened a new terminal) I then typed iwconfig and it said (the first letter in each line is missing bc for some reason my monitor doesn't adjust right):

O       No wireless extensions
ifi0    No wirless extensions
th0     IEE 802.11g  ESSID:<Correct Network name here>
        <followed by 7 more lines indicating it sees   the card>
th0    No wirless extensions
it0    No wirless extensions


It seems as though only one PCI card is being seen. Can anyone help? If you need more or better information I'll do my best to explain.

---

### Post by ZERO_SHIFT on 2007-03-16
I strongly reccomend using Automatix for both the nVIDIA driver as well as the wireless driver using NDISWrapper

---

