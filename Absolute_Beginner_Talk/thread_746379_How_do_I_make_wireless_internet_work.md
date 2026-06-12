---
title: "How do I make wireless internet work?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by PFSpectrum on 2008-04-05
I just installed Linux for the first time... I am completely new to it and have never even used it before... I cant get my wireless internet to work and I have looked all over these forums for how to make it work... when I click on the wireless thing in the corner I don't even see my connection... help? =[

---

### Post by upthelum on 2008-04-05
It will depend on your hardware. Run lspci, post the output and maybe someone can help.

---

### Post by PFSpectrum on 2008-04-05
Ok... i entered that command that you gave me and this is what i came up with

mike@mike-pc:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary) (rev 9a)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by upthelum on 2008-04-05
You should try installing the latest drivers for your hardware. 

Try _iwlist scan_ and post this output.

---

### Post by PFSpectrum on 2008-04-05
Ok  here is what i got when i did the iwlist scan

mike@mike-pc:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


=]

---

### Post by sneeks on 2008-04-05
what wireless device are you using to connect?

---

### Post by upthelum on 2008-04-05
Looks like the device isn't picking up your access points if i'm correct. Try re-configuring your hardware, uninstall reinstall drivers and i'll bump it for input from others. If i run iwlist i get a list of available access points. Also check the hardware vendor for linux support for your device. Sorry i cant help you anymore.

---

### Post by ghost_ryder35 on 2008-04-05
```

sudo apt-get install bcm43xx-fwcutter
sudo modprobe bcm43xx

```
that should get you up and running :)

You can also do this in the GUI by going to the Restricted Drivers under System and Administration and clicking the tick next to your BCM card under the ENABLE colum

---

### Post by SunnyRabbiera on 2008-04-05
Just be warned that wireless is still a work in progress here, you may need something called Ndiswrapper.

---

### Post by ghost_ryder35 on 2008-04-05
> **SunnyRabbiera said:**
> Just be warned that wireless is still a work in progress here, you may need something called Ndiswrapper.
the BCM43XX driver has been part of the kernel since Fiesty, not saying that it works perfect, but it works

---

### Post by brian_p on 2008-04-05
> **PFSpectrum said:**
> 
05:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Broadcom. Fiddly. This might help:

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/)

---

### Post by SunnyRabbiera on 2008-04-05
still ndiswrapper might be needed

---

### Post by ghost_ryder35 on 2008-04-05
> **SunnyRabbiera said:**
> still ndiswrapper might be needed
Speaking of NDISwrapper does it support WPA and packet injection yet?

---

### Post by PFSpectrum on 2008-04-05
Every time i try one of these commands i get errors about how I'm not allowed to modify them. And i don't think i have some of the required files... i am completely new to Linux can someone post a detailed description of how i can do this... with commands and everything. I'm not sure how big it would be for someone to spend their time writing a guide for me ... but i really want to use ubuntu =]

---

### Post by ghost_ryder35 on 2008-04-05
did you try?
> **ghost_ryder35 said:**
> ```

sudo apt-get install bcm43xx-fwcutter
sudo modprobe bcm43xx

```
that should get you up and running :)
 
You can also do this in the GUI by going to the Restricted Drivers under System and Administration and clicking the tick next to your BCM card under the ENABLE colum

---

### Post by PFSpectrum on 2008-04-05
Yes, this is what happened when i entered those 

mike@mike-pc:~$ sudo apt-get install bcm43xx-fwcutter
[sudo] password for mike:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter
mike@mike-pc:~$ sudo modprobe bcm43xx
mike@mike-pc:~$ 


=[

---

### Post by brian_p on 2008-04-05
> **PFSpectrum said:**
> Every time i try one of these commands i get errors about how I'm not allowed to modify them. And i don't think i have some of the required files... i am completely new to Linux can someone post a detailed description of how i can do this... with commands and everything. I'm not sure how big it would be for someone to spend their time writing a guide for me ... but i really want to use ubuntu =]

Specially for you and hot off the press

[http://www.debiantutorials.org/content/view/153/213/](http://www.debiantutorials.org/content/view/153/213/)

---

### Post by brian_p on 2008-04-05
> **PFSpectrum said:**
> Yes, this is what happened when i entered those 
E: Couldn't find package bcm43xx-fwcutter


It is in all the distributions. Is your package information complete?

---

### Post by ghost_ryder35 on 2008-04-05
you need to enable the restricted repository under System, Administration, Software Sources

---

### Post by PFSpectrum on 2008-04-05
I'm not sure, how would i check that... I'm really new to this Linux thing... I'm not completely sure what I'm doing

i downloaded that bcm43xx-fwcutter file and now i just have a lot of files in a folder on my desktop... can someone tell me how i can use these files... I'm sorry i don't know how to do this stuff i just downloaded Linux today =]

---

### Post by ghost_ryder35 on 2008-04-05
> **PFSpectrum said:**
> **I'm not sure, how would i check that...** I'm really new to this Linux thing... I'm not completely sure what I'm doing
 
i downloaded that bcm43xx-fwcutter file and now i just have a lot of files in a folder on my desktop... can someone tell me how i can use these files... I'm sorry i don't know how to do this stuff i just downloaded Linux today =]
 
[quote=ghost_ryder35]you need to enable the restricted repository under **System, Administration, Software Sources**[/quote]  Thats how

---

### Post by PFSpectrum on 2008-04-05
Ok i did that ... but my internet still isn't working... i got that ndiswrapper thing and i installed the drivers for my card... but it told me the drivers are already installed.... now whenever i try to use it, it tells me that I'm not allowed to access the files or something like that.... D=.... i tried installing the wifi radar thing and my card is not picking up any signals... and i went to the wireless drivers menu and i found the file for the driver in my cd and its still not working.... ]=

---

### Post by grumpylad77 on 2008-04-05
Follow the instructions in this link and your wireless should work no problem.
It's easy to follow.
[http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html]("http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html")

---

### Post by PFSpectrum on 2008-04-05
No thats still not working... I'm just gonna give up on this because this is not working        ]=

---

