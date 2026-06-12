---
title: "Wireless Issues"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by aliasbs on 2006-08-03
Hello,

I've finally decided to cross over from windows.  The first issue i've come across so far is setting up my wireless internet connection.  I havent downloaded or installed anything else to the OS besides what was installed from the .iso.  

Since my background has been all windows, i have tried using the windows approach to the issue (click a lot).  

I currently have a "Linksys WMP54GS Wireless-G PCI Card with SpeedBooster" that is trying to connect to a "Linksys WRT54GS Wireless-G Broadband Router with SpeedBooster".  The driver for the PCI card is the default one with the installation.  It wireless is currently set up with DHCP and a 128 wep key.

Since i assumed this was a straight forward process i just configured the wireless connection with router information.  Once i try to activate it, it takes about a minute to configure each time. Once I close the networking process and reopen it, the wireless connection is not active.  The default gateway is pointing to the wireless connection and all the info "seems" correct, but I am unable to find the internet.

Under network tools i tried pinging the wireless router with 192.168.1.1 but it doesnt see the ip.  The only one i recall it pinging was a 127.0.0.1 (i cant remember the exact ip).

Is there anyone who can point me in the right direction?  I have tried the system manuals but I couldnt find the information  needed.  Also, how do i know if im connecting to the right wireless connection?  I know there are several in my area but i couldnt find a utility that scans for local wireless connections with the names that are tagged with it.  

The internet provider is Comcast.

---

### Post by popkid on 2006-08-03
Hi, firstly apologies, I'm at work at the moment so can't spend long giving any help...

I think you will need to use either ndiswrapper with your windows drivers or use bcm43xx (linux native driver) with the firmware cut from your windows driver, if you put your card name in the search box for these forums, there are a load of links to other people who have got your card working so shouldn't be too painful hopefully!

127.0.0.0 is your localhost... i.e. you are able to ping the machine you are pinging from... which doesn't help much.

Good luck.

pK

---

### Post by carlosqueso on 2006-08-03
What does it output when you type iwconfig into a terminal?

---

### Post by aliasbs on 2006-08-03
Awesome!  I was just searching for wireless and didnt realize that the my card was so popular.  I will follow the advice on the other threads then reply with the results when i get home later today.

Thank you.

---

### Post by bensexson on 2006-08-03
Do you know the chipset your wireless adapter is using?  What does sudo iwconfig show?

---

### Post by aliasbs on 2006-08-03
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"felicia"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:3934-6263-6137-3534-3033-3134-30   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Seems i have the BCM4318 wireless card

---

### Post by aliasbs on 2006-08-03
Awesome!

The tutorial from the following worked!!!
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318)

Now i feel kind of silly that im so happy with the internet working.... Now onto video/audio codecs!

---

