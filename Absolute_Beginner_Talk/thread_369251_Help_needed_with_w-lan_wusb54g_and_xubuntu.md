---
title: "Help needed with w-lan wusb54g and xubuntu"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Lapsi on 2007-02-24
Hi!

I just installed the Xubuntu to an old computer so I could use it to access the internet. I read the manuals how to install this WUSB54G but I think the most of the were not written for Xubuntu and anyhow I did not understand a word. :P So I'm asking if there would be a lovely person which would guide me through the installation process and telling me exactly what to do/write etc.

Thanks in advance...

---

### Post by 720iD on 2007-02-24
this thread should help 
[http://www.ubuntuforums.org/showthread.php?t=192588](http://www.ubuntuforums.org/showthread.php?t=192588)

---

### Post by Lapsi on 2007-02-24
i just got stuck in the first section where is should type $sudo gedit /etc/modprobe.d/blacklist because it says that gedit: command not found

---

### Post by Lapsi on 2007-02-24
and if i try to save the new blacklist file, it says "can't open file to write"

---

### Post by 720iD on 2007-02-24
read the thread right through before doing anything. there are different instructions a bit further on and other users find solutions to problems you may expereince.

---

### Post by Lapsi on 2007-02-24
i tried and tried... but as i said, i even couldn't rewrite the blacklist file. so maybe i'll stick to windows or something...

---

### Post by 720iD on 2007-02-24
> **Lapsi said:**
> i tried and tried... but as i said, i even couldn't rewrite the blacklist file. so maybe i'll stick to windows or something...

are you able to install ndiswrapper using synaptic? 

did you read the thread right through? as people got your device working without going through all those command line instuctions.

---

### Post by Lapsi on 2007-02-25
What is synaptic and how it works? Do you have any kind of idea why I can't save the blacklist file?

---

### Post by 720iD on 2007-02-25
i am sure the people in that post got the device working with the driver you are trying to blacklist. 

you can find synaptic in the menus under system> administration> synaptic -package management


synaptic is a tool for adding removing programs it will search on the web or cd/dvd for repositories of programs that can be cleanly installed / uninstalled.

you will need a wired internet conection or dvd repository for installing all the software available but i think ndiswrapper is on the standard ubuntu live install cd.

---

### Post by 720iD on 2007-02-25
quotes here are taken from this thread
[http://www.ubuntuforums.org/showthread.php?t=192588](http://www.ubuntuforums.org/showthread.php?t=192588)



> **Linuturk said:**
> I have the same exact adapter: WUSB54G v4

I've playing with this for the last two days. Funny thing is, my adapter works ok with the native drivers if the device IS NOT PLUGGED IN DURING THE UBUNTU INSTALL OR STARTUP. If you plug it in after, and activate it, it works. I'm about to try your method, b/c occasionally it will freeze up my system completely, and I have to hard reboot.

______________________________________________

This fixed all the problems I was having. It recognizes all the networks around me now, and it doesn't freeze up! Thanks so much!

Don't forget that sudo ndiswrapper -m


> **lmp said:**
> I have a WUSB54Gv4. I had no problem at all with the native ubuntu 6.06 LTS. I did NOT need ndiswrapper for my desktop. Also my laptop had no problems with it. Only advise: first configure, then save and restart, than activate (otherwise it won't work).
I have the same issue with my laptop that after x minutes the wifi is not working anymore. I read in a windows magazine that this might be caused by the power settings of the wifi.The wifi wakes up not as fast as the computer, so it losses contact. However, were can i find this powersetting in XUBUNTU or UBUNTU??. I have an old laptop toshiba 2180 cdt. I already changed the hardware setting (bios), but this doesn't seem to help.


your device works with the drivers that come with ubuntu install you just need to configure your wirelss network in network manager then plug your device in

---

### Post by Lapsi on 2007-02-25
Ok. Maybe the problem was that i had the device plugged in during the Xubuntu install. Do you think that it WUSB54G v.1 is different from the fourth version? should i buy a newer version of the device?

Then, when configuring the wlan,  should i put something to the general, dns and hosts sections? And should i use direct connect when i connect to the internet?

And how i can see what drivers is the wlan device using? do i have to configure them myself or does the xubuntu it automatically?

Now i'm going to reinstall the whole xubuntu with the WUSB54g NOT connected :P to see if it helps...

Thanks in advance!

---

### Post by Lapsi on 2007-02-25
and another question... do i need to install something or du i just configure save restart and then plug the device in?

---

### Post by Lapsi on 2007-02-25
Ok I reinstalled the whole Xubuntu and did what that thread said (configured, booted, disconnected and activated) but it still doesn't work. do you think i should install something or choose the driver somehow or what could be the problem? or is the problem the wrong settings when configuring the device? 

Should i use the automatic DHCP option or put the IP addresses on my own... i tried both but they didnt work. I tried to put the following:

ESSID: the name of the wireless network as my laptop sees it
IP: 192.168.1.37
Subnet: 255.255.255.0
Gateway: 192.168.1.1

---

### Post by Lapsi on 2007-02-26
Ok. Now I got the system working. Here's the solution (great thread anyways)

[http://www.ubuntuforums.org/showthread.php?t=192588&page=9](http://www.ubuntuforums.org/showthread.php?t=192588&page=9)

---

