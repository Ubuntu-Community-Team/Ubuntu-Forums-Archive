---
title: "Intel 2200BG - a common problem it seems"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by kneewax on 2007-03-19
OK, I see there are a number of problems with Intel Wifi cards on these forums, but I have trawled through a number of them and found no solution suitable for a newbie.

I have a Fujitsu-Siemens Amilo laptop with the Intel 2200BG miniPCI integrated wireless NIC.  Looking at the details for Ubuntu prior to installation it appeared that the distro should recognise the card, but it doesn't seem to as I cannot configure the thing.  

dmesg tells me the drivers are old and need to be re-installed, but as a newbie I am struggling to successfully do this.  It is not helped that inorder to check problems I have to log out and use the dual-booting WinXP inorder to check the details online.

Can anyone give me a pointer on the simplest way to get this card working?

Thanks
Kneewax

---

### Post by happy-and-lost on 2007-03-19
The 2200 does work right out of the box.

Can you get online via enternet in Ubuntu? If you can, *sudo apt-get install wifi-radar* will install a handy graphical config tool.

Also, what's the output of iwconfig, there's a chance the card's switched off in the BIOS (Mine was)?

---

### Post by tocleora on 2007-03-19
Well I'm afraid I'm just adding insult to injury as I don't actually have anything that will help, other than knowing that it *should* work, as I have both a fujitsu laptop and an Intel 2200BG wireless nic that worked without additional configuration needed.  That's unfortunately why I can't offer assistance, because I didn't have to do anything to get it to work.  What version of Ubuntu are you running?  If it helps in any way, I initially installed 6.06 and upgraded to 6.10.  6.06 is (from my understanding?) more stable so you might try installing it first and see if it recognizes it.  YOu might do that as a last resort in case someone else has an easier solution. :)

---

### Post by kneewax on 2007-03-19
Thanks guys.  I am using 6.10. I'll check the BIOS, but as I am pretty sure it is on there by default as I set it for XP when I first got the laptop.

If necessary I can get the machine to a wired ethernet connection, but not eeasily, might try it before I consider reinstalling mind! :) 

Kneewax

---

### Post by kneewax on 2007-03-19
Ok here goes:

iwconfig:

eth1    unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

However I get this is I do a dmesg |grep ipw


[17179598.956000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179598.956000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179598.956000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179598.956000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179599.352000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)


Any ideas?

Thanks

Kneewax

---

### Post by kneewax on 2007-03-19
ooops read colon d instead of the smilies in that post!!!

---

### Post by toddhd on 2007-03-19
I have a 2200BG in a Dell XPS M180 that works fine as well. What are you trying to connect to? I have my router setup to use WPA-PSK security (as opposed to WEP security) so it does *not* work "out of the box" for me, but it does work with tweaking. 

If you have security turned on (on your router) then try turning it off, and see if you can connect. Once you have that nailed down, you can start the process of figuring out the rest.

---

### Post by kneewax on 2007-03-20
OK, I tried the suggestions above, and got nowhere, so being that install is so quick I decided to remove 6.10 and install 6.06 as suggested.  Well I got somewhere, the wifi network I want to join is now visible in the network settings and I can plug in the wep code (it is wep, BTW) and set the card to DHCP.  However that's all I get, I still cannot actually join the network.

iwconfig now returns the following:

eth1      unassociated  ESSID:"TRINITY-BRIS-CLIFTON"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and Dmesg | grep on the card results in the following:

[17179596.852000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1[17179596.852000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179596.852000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179596.852000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[17179597.580000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)


This is different  to the result I was getting under 6.10.

Please any further help for this total newbie would be grateful.  It is the difficulty with which these sorts of issues are solved that has stopped be jumping to Linux before, and I really want to see if I can make it work this time.

Cheers 


Kneewax

---

### Post by happy-and-lost on 2007-03-20
OK, to configure the card, right click on the little network applet next to the clock, click properties.

In the box which says Name, make sure the name is set to eth1. With that set, click on configure.

Type your ESSID into the ESSID box and key into key box and press OK :)

---

### Post by kneewax on 2007-03-20
OK, sorry to keep posting.  Here is what happened:

I clicked the network icon and 'lo' was displayed in the box as before.  The drop down did not include my eth1 device.  So as an experiment I typed 'eth1' into the box instead.  Surprisingly this brought up the wifi strenght icon and enabled the previously greyed out properties button.  

Clicking this brought up the network settings configuration box I had been accessing through the menu system, However even with the correct ESSID and WEP key I still cannot connect....

Thanks for all your help so far...

Kneewax

---

### Post by toddhd on 2007-03-20
See this thread as well. It spells out what your interfaces file should look like for an Intel2200BG card.

---

### Post by stalkier on 2007-03-20
Try these one at a time in the terminal:
sudo rmmod bcm43xx

sudo rmmod ndiswrapper

sudo modprobe ndiswrapper

sudo ifdown eth1

sudo ifup eth1

sudo dhclient

more info found at [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wifi+edgy](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wifi+edgy)

I hope this helps.

---

### Post by kgonda on 2007-04-05
I'm experiencing the exact same issue, Kneewax

---

