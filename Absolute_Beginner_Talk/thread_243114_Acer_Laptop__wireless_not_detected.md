---
title: "Acer Laptop / wireless not detected"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Stegga on 2006-08-24
Hi there,
I have just purchased an Acer Laptop (4245 I think) and I have decided that I am going to ONLY install Ubuntu on it - it came with XP, and I used it for a week, but then converted, or so I hoped.

I have installed 6.06 and it booted up fine, but I have bought a Linux Bible and been trying to learnn the Linux Way of Life and I do not have any wireless anything detected. (I am going to do as much of this from memory as I can as my Ubuntu Laptop is at the office!)

There is a command which allows me to see the 'hardware on board' or something, and there is a 'network' class that I entered into the command, to show the netowrking componants, and it shows the Eth0 (which in my understanding is the onboard Ethernet connector, but nothing about wireless. I guess in window speak, I need to 'install the drivers' for Acer's computer and Ubuntu, but as a newbie, I wouldn't know where to get the Ubuntu driver (or is it a Linux driver) and then how to go about installingit, and in the first place how to find out what driver I need as the Laptop has no idea about the onboard wireless.

Please can someone steer me in the correct direction for which website to go to, or something.

Cheers,
Andrew

---

### Post by jordilin on 2006-08-24
There is some documentation in the wiki regarding laptops. For Acer take a look here:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer)
and see if your model is documented there. Hope you find the answer

---

### Post by benfindlay on 2006-08-24
Hi there, Linux and Wifi have always been a problem. First you're best off installing a program called NDISWRAPPER. If you're not familiar with ubuntu, I'd suggest you use the SYnaptic Package Manager to install all your desired programs.

Click on the System menu at the top of the screen and choose Administration. About 2 thirds of the way down there is an option called "Synaptic Package Manager"

Choose this and scroll down the right hand list of programs till you get to N. Right click on NDISWRAPPER and choose "Mark for Installation". Click OK on any boxes that then come up (as it may well have dependencies, which need to be installed along with the program itself).

Then at the top click on the "Apply" button (big Tick) It will give you a box up where it informs you about the amount of data to be downloaded, installed etc. Just OK this box. Once this is done you can click close, then shut Synaptic and NDISWRAPPER is installed.

NDISWRAPPER itself is a Linux program that lets you use Windows drivers with a wifi card under Linux. Now, I've only used it in SuSE Linux, where it automatically configured my card for me. It may well detect and install your card ok, then again, it may do nothing, and need configuring!

Once it's on I'd first suggest you reboot, in case it has teh fortune of just working out right.

I'm sure someone who knows much more about wifi will be posting soon enough anyways telling me I'm completely wrong, but never mind! ;) 

Hope this helps!

---

### Post by annda on 2006-08-24
i would hold off installing ndiswrapper because you might not need it after all. it's possible that your problem is configuration, not lack of linux support.

please post the exact model of your notebook. and preferably, do that while sitting in front of it if possible. that way the helpful folk here will be able to guide you step-by-step while you try out suggested solutions.

i did have some issues with my acer laptop with hoary, but managed to solve them thanks to this great forum. well, i have intel centrino that takes care of the wireless communication, so it was pretty standard procedure...

anyway, good luck and post back - some problems are tiresome to solve, but in my experience most of them are not as scary as they seem.

---

