---
title: "Probably a very simple question, but..."
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by dswatuga on 2005-11-21
I am basically a newborn trying this stuff so please forgive me.

I am trying to set up my MN-520 Wireless Notebook Adapter and have installed the ndiswrapper from the Synaptic Package Manager. (To my knowledge the package manager seems to be working fine.) 

The problem arises when I try to enter my driver. My driver's file name is MN520.inf and it is in my Home.

In the terminal I have been entering "ndiswrapper -i MN520.inf" or "ndiswrapper -i /home/sarah/MN520.inf." and I keep getting the message "Unable to create directory /etc/ndiswrapper.mn520. Make sure you are running as root"

Probably an easy answer to this for someone but I just decided to dive into Linux and am struggling a bit to say the least.

---

### Post by MrCheese on 2005-11-21
[QUOTE=dswatuga]I am basically a newborn trying this stuff so please forgive me.

I am trying to set up my MN-520 Wireless Notebook Adapter and have installed the ndiswrapper from the Synaptic Package Manager. (To my knowledge the package manager seems to be working fine.) 

The problem arises when I try to enter my driver. My driver's file name is MN520.inf and it is in my Home.

In the terminal I have been entering "ndiswrapper -i MN520.inf" or "ndiswrapper -i /home/sarah/MN520.inf." and I keep getting the message "Unable to create directory /etc/ndiswrapper.mn520. Make sure you are running as root"

Probably an easy answer to this for someone but I just decided to dive into Linux and am struggling a bit to say the least.[/QUOTE]

Precede the commands you are entering with "sudo" - this gives you effectively root status for that command. You will need to enter your password when prompted. Also don't forget to do "sudo ndiswrapper -m" and "sudo ndiswrapper -hotplug" t o get ndiswrapper loading at boot time with the correct hotplug info. Well done on getting as far as you did though :)

---

### Post by dswatuga on 2005-11-21
Thanks.

I am still having a little trouble though. I keep getting "mn520 invalid driver" and "mb720 invalid driver" after I look at the list of drivers installed.

My card is plugged in and I thought I followed the directions. Do I have the wrong driver or should I not have my card plugged in yet? If I don't have the right driver does anyone with a 520 know where I can find it?

---

