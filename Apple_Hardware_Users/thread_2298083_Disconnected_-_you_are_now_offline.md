---
title: "Disconnected - you are now offline"
date: 2015-10-08
forum: Apple Hardware Users
---

### Post by tommy25 on 2015-10-08
I just installed ubuntu 15.04 on a 2009 macbook air (it only has wifi, no ethernet port). Everything is working fine except ever since I've first logged in, I have gotten this message "Network disconnected - you are now offline". I have almost no knowledge on how to troubleshoot issues like this, but what I do know is that when I go to 'System Settings>Software & Updates>Additional Drivers' under "Broadcom Corporation: BCM4321 802.11a/b/g/n (AirPort Extreme)" (That's the wireless chip) it says "This device is using an alternative driver" and under that there is a checked box saying " Using Broadcom 802.11 Linux STA Wireless driver source from bcmwl-kernel-source (proprietary)" and an unchecked box saying "Do not use the device". How do I get the wifi working?

---

### Post by QIII on 2015-10-08
*Moved to **Apple Hardware Users***

---

### Post by mystics on 2015-10-09
Have you checked to make sure that you enabled WiFi and that your computer is trying to connect to a network? It's possible everything is turned off or that it currently doesn't recognize any networks in the area. 

If the Wi-Fi is turned on and there is a saved network in the area, please confirm that the driver is installed by opening up a terminal and typing:

```
dpkg -s bcmwl-kernel-source
```

It may sound like an odd request, but I personally had an issue when I first installed Ubuntu where the driver wasn't installed but the Additional Drivers said that it was there. 

If it turns out to not be installed, you could download it and the dependencies from here: [http://packages.ubuntu.com/vivid/bcmwl-kernel-source](http://packages.ubuntu.com/vivid/bcmwl-kernel-source)

Once gotten on a computer with Internet, you can get them on a USB drive, move them to your Ubuntu partition, open up a terminal where they're at, and type in:

```
sudo dpkg -i [package name]
```

Be sure all dependencies are installed first.

Alternatively, if your phone supports tethering and your contract allows you to tether it, then you could always temporarily get Internet that way and just run:

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by tommy25 on 2015-10-09
[SIZE=3][FONT=arial]I have a PC and I first tried downloading the drivers and installing them. I noticed that I know have the option to enable and disable WiFi... but I still can't find my WiFi signal, even after a restart. I am connected to my WiFi just fine on my iPhone 4 and kindle HDX so I don't think that it is the problem. After that I put this into the terminal.

```
 dpkg -s bcmwl-kernel-source 
```

This is what I got back.

```
tommy@MACBOOK-UBUNTU:~$ dpkg -s bcmwl-kernel-source
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 7850
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.248+bdcom-0ubuntu2
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>


```

Could this possibly be a hardware issue? I had no problems with the WiFi on Mac OS X before I wiped the hard drive and installed Ubuntu though.
[/FONT][/SIZE]

---

### Post by mystics on 2015-10-09
OK, the driver is definitely installed.

It is possible that your network is hidden. Try seeing if you can connect by putting in the network information under "Connect to a Hidden Wi-Fi Network..."

Edit: If you don't know the information, it is possible that it might be on the router. You may also be able to find it from network information on Windows or iOS. Unfortunately, I don't know how to do it on either of those.

---

### Post by tommy25 on 2015-10-09
When I just booted my mac book up I was able to see my WiFi network, along with both of my neighbors... but I couldn't connect to mine. I was able to connect to my hot spot on my iPhone, but that was draining my phone battery quick. So I tried restarting my mac book, but after the reboot I wasn't able to see any WiFi networks anymore. After the reboot I tried to connect to my WiFi as if it was a hidden network (using the router information from my iPhone) but it didn't work. I have an app on my kindle HDX called PdaNet and with that I can share internet from my kindle to computers via Bluetooth or USB tethering. I've used it on my PC because they provide software for windows but not for Linux, so I'm not sure if I could use that to share internet with my mac book. If I were to buy a USB Ethernet adapter, could I use that temporarily as a solution for internet? 

[http://www.amazon.com/USB-Ethernet-Adapter-Satisfaction-Guarantee/dp/B00PIW2I96/ref=sr_1_1?ie=UTF8&qid=1444429692&sr=8-1-spons&keywords=usb+ethernet+adapter&psc=1](http://www.amazon.com/USB-Ethernet-Adapter-Satisfaction-Guarantee/dp/B00PIW2I96/ref=sr_1_1?ie=UTF8&qid=1444429692&sr=8-1-spons&keywords=usb+ethernet+adapter&psc=1)

Could I maybe buy that and do all the system updates to see if that fixes the problem? Also, I just now suspended Ubuntu then turned it back on and I noticed that I could see WiFi networks again. I still can't connect to them but I can see them.

---

### Post by mystics on 2015-10-10
Well, it is a cheap way of getting connected to the Internet, but I'm not entirely sure it is necessary unless you really want to have the Linux itself connected when trying to solve the problem rather than downloading files, transferring them, and then installing them. I'm also not sure an update will fix the problem. 

I'm also not entirely convinced it is hardware failure. That's possible, but it seems a little too coincidental.

Anyways, there are some other drivers that might work with your chipset. Are you able to post the output of

```
lspci | grep -i broadcom
```

That would help in determining if other drivers should work with the chipset.

---

### Post by tommy25 on 2015-10-11
Alright so I put that in to the terminal and this was the output
```
tommy@MACBOOK-UBUNTU:~$ lspci | grep -i broadcom
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05)


```

---

### Post by mystics on 2015-10-12
Unfortunately, it appears that the only driver that works with the chipset is the one you've already installed, at least according to this page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

(Note: That site does give a little information regarding some troubleshooting, but none of it is based around 15.04, so I don't know how it will work for you).

I guess, if you have mobile data to spare, you could connect that way and run

```

sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source

```

just to make sure it is installed correctly. It's also possible to try:

```

sudo apt-get update
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source

```

The basis of these two is to update the repositories and then reinstall the package. The first one is just designed to reinstall the package. The second one first removes the packages and removes configurations. It then will install the package. Basically, it's possible you missed a dependency when installing the package earlier, and that dependency would be necessary for it to run correctly and get Internet access. Using apt-get will help resolve dependencies.

If you don't want to put your mobile data through that, let me know and I'll see if I can get a list of all the stuff you need to check and possibly install.

---

### Post by salmacis on 2015-10-13
I just installed onto a 2009 mac mini. I don't know if the wifi card is the same, but it seems likely. I tried the bcmwl-kernel-sources package, but didn't get it to work. It looked like the card was working, but it just couldn't see any wifi networks. I purged it, and installed firmware-b43-installer instead, and that did the trick.

---

### Post by mystics on 2015-10-13
> **salmacis said:**
> I just installed onto a 2009 mac mini. I don't know if the wifi card is the same, but it seems likely. I tried the bcmwl-kernel-sources package, but didn't get it to work. It looked like the card was working, but it just couldn't see any wifi networks. I purged it, and installed firmware-b43-installer instead, and that did the trick.

Would you mind typing the following into a terminal and post the results here:

```
lspci | grep -i broadcom
```

You're right, it might be the same WiFi card. However, I do want to make sure, as I'm not sure if Apple uses different ones for different devices of the same year. The site I linked to earlier says that tommy's card shouldn't work with the firmware-b43-installer, but if you have the same one and it worked for you, it is possible that that site is simply outdated and that trying it might be very useful.

---

### Post by salmacis on 2015-10-14
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05)

---

### Post by mystics on 2015-10-14
Thank you! That's the same one as the OP! It appears that the Community Wiki is outdated in that regard.

tommy25, if you want to install the package with your mobile data, it only will take up 30 KB (plus whatever data is necessary for an update). Just open up a terminal and type

```

sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install firmware-b43-installer

```

The above will purge the non-working bcmwl-kernel-source, update repositories, and install the firmware-b43-installer. Hopefully, it works as well for you as it did for salmacis.

Please let us know how that goes for you.

---

### Post by tommy25 on 2015-10-18
Sorry for the late response, I got a little preoccupied by school.
I first tried this (While connected to my hot spot)
```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-sources
```
This is what I got back (I just copied and pasted the whole thing)
```
thomas@MACBOOK-UBUNTU:~$ sudo apt-get update
[sudo] password for thomas: 
Hit http://us.archive.ubuntu.com vivid InRelease                               
Get:1 http://security.ubuntu.com vivid-security InRelease [64.4 kB]   
Get:2 http://us.archive.ubuntu.com vivid-updates InRelease [64.4 kB]           
Hit http://us.archive.ubuntu.com vivid-backports InRelease                     
Hit http://security.ubuntu.com vivid-security/main Sources                     
Hit http://security.ubuntu.com vivid-security/restricted Sources
Hit http://security.ubuntu.com vivid-security/universe Sources                 
Hit http://security.ubuntu.com vivid-security/multiverse Sources               
Hit http://security.ubuntu.com vivid-security/main amd64 Packages              
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages        
Hit http://security.ubuntu.com vivid-security/universe amd64 Packages          
Hit http://security.ubuntu.com vivid-security/multiverse amd64 Packages        
Get:3 http://us.archive.ubuntu.com vivid-updates/main Sources [93.8 kB]        
Hit http://security.ubuntu.com vivid-security/main i386 Packages               
Hit http://security.ubuntu.com vivid-security/restricted i386 Packages         
Hit http://security.ubuntu.com vivid-security/universe i386 Packages           
Hit http://security.ubuntu.com vivid-security/multiverse i386 Packages         
Get:4 http://us.archive.ubuntu.com vivid-updates/restricted Sources [3,687 B]  
Hit http://security.ubuntu.com vivid-security/main Translation-en              
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en        
Get:5 http://us.archive.ubuntu.com vivid-updates/universe Sources [40.8 kB]    
Hit http://security.ubuntu.com vivid-security/restricted Translation-en        
Hit http://security.ubuntu.com vivid-security/universe Translation-en          
Get:6 http://us.archive.ubuntu.com vivid-updates/multiverse Sources [1,957 B]  
Get:7 http://us.archive.ubuntu.com vivid-updates/main amd64 Packages [211 kB]  
Get:8 http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages [13.1 kB]
Get:9 http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages [112 kB]
Get:10 http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [5,195 B]
Get:11 http://us.archive.ubuntu.com vivid-updates/main i386 Packages [209 kB]  
Get:12 http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages [12.8 kB]
Get:13 http://us.archive.ubuntu.com vivid-updates/universe i386 Packages [113 kB]
Get:14 http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages [5,394 B]
Hit http://us.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://us.archive.ubuntu.com vivid-backports/restricted Sources
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Sources
Hit http://us.archive.ubuntu.com vivid-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com vivid-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com vivid-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com vivid-backports/main i386 Packages
Hit http://us.archive.ubuntu.com vivid-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com vivid-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com vivid-backports/main Translation-en
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com vivid/main Sources
Hit http://us.archive.ubuntu.com vivid/restricted Sources
Hit http://us.archive.ubuntu.com vivid/universe Sources
Hit http://us.archive.ubuntu.com vivid/multiverse Sources
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages                 
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages               
Hit http://us.archive.ubuntu.com vivid/main i386 Packages                      
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages                
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages                  
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages                
Hit http://us.archive.ubuntu.com vivid/main Translation-en                     
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en               
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en               
Hit http://us.archive.ubuntu.com vivid/universe Translation-en                 
Hit http://us.archive.ubuntu.com vivid-updates/main Translation-en             
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en       
Hit http://us.archive.ubuntu.com vivid-updates/restricted Translation-en       
Hit http://us.archive.ubuntu.com vivid-updates/universe Translation-en         
Hit http://us.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://us.archive.ubuntu.com vivid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com vivid-backports/universe Translation-en       
Fetched 951 kB in 3min 35s (4,408 B/s)                                         
Reading package lists... Done
thomas@MACBOOK-UBUNTU:~$ sudo apt-get install --reinstall bcmwl-kernel-sources
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-sources
thomas@MACBOOK-UBUNTU:~$

```
I restarted after that and nothing had changed. After that, I tried the second set of commands you provided
```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-sources
sudo apt-get install bcmwl-kernel-sources
```
This is what I got back (again, I just copied and pasted the whole thing)
```
thomas@MACBOOK-UBUNTU:~$ sudo apt-get update
[sudo] password for thomas: 
Hit http://security.ubuntu.com vivid-security InRelease                     
Hit http://us.archive.ubuntu.com vivid InRelease                            
Get:1 http://us.archive.ubuntu.com vivid-updates InRelease [64.4 kB]  
Hit http://security.ubuntu.com vivid-security/main Sources
Hit http://security.ubuntu.com vivid-security/restricted Sources         
Hit http://security.ubuntu.com vivid-security/universe Sources                 
Hit http://us.archive.ubuntu.com vivid-backports InRelease        
Hit http://security.ubuntu.com vivid-security/multiverse Sources         
Hit http://us.archive.ubuntu.com vivid/main Sources
Hit http://security.ubuntu.com vivid-security/main amd64 Packages
Hit http://us.archive.ubuntu.com vivid/restricted Sources          
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com vivid/universe Sources        
Hit http://security.ubuntu.com vivid-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com vivid/multiverse Sources     
Hit http://security.ubuntu.com vivid-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages        
Hit http://security.ubuntu.com vivid-security/main i386 Packages  
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages  
Hit http://security.ubuntu.com vivid-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages    
Hit http://security.ubuntu.com vivid-security/universe i386 Packages
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages  
Hit http://security.ubuntu.com vivid-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com vivid/main i386 Packages      
Hit http://security.ubuntu.com vivid-security/main Translation-en
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages     
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages     
Hit http://security.ubuntu.com vivid-security/restricted Translation-en
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages    
Hit http://security.ubuntu.com vivid-security/universe Translation-en
Hit http://us.archive.ubuntu.com vivid/main Translation-en         
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en
Hit http://us.archive.ubuntu.com vivid/universe Translation-en
Hit http://us.archive.ubuntu.com vivid-updates/main Sources
Hit http://us.archive.ubuntu.com vivid-updates/restricted Sources              
Hit http://us.archive.ubuntu.com vivid-updates/universe Sources                
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com vivid-updates/main amd64 Packages             
Hit http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages         
Hit http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages       
Hit http://us.archive.ubuntu.com vivid-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com vivid-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com vivid-updates/main Translation-en             
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en       
Hit http://us.archive.ubuntu.com vivid-updates/restricted Translation-en       
Hit http://us.archive.ubuntu.com vivid-updates/universe Translation-en         
Hit http://us.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://us.archive.ubuntu.com vivid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com vivid-backports/main amd64 Packages           
Hit http://us.archive.ubuntu.com vivid-backports/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com vivid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com vivid-backports/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com vivid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://us.archive.ubuntu.com vivid-backports/restricted Translation-en     
Hit http://us.archive.ubuntu.com vivid-backports/universe Translation-en       
Fetched 64.4 kB in 12s (5,354 B/s)                                             
Reading package lists... Done
thomas@MACBOOK-UBUNTU:~$ sudo apt-get purge bcmwl-kernel-sources
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-sources
thomas@MACBOOK-UBUNTU:~$ sudo apt-get install bcmwl-kernel-sources
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-sources
thomas@MACBOOK-UBUNTU:~$ 

```
Once again, I restarted and nothing changed. Next, I tried what salmacis suggested:
```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-sources
sudo apt-get install firmware-b43-installer
```
and I got this back (Copy and pasted)
```
thomas@MACBOOK-UBUNTU:~$ sudo apt-get update
[sudo] password for thomas: 
Hit http://us.archive.ubuntu.com vivid InRelease                            
Hit http://security.ubuntu.com vivid-security InRelease               
Get:1 http://us.archive.ubuntu.com vivid-updates InRelease [64.4 kB]  
Hit http://security.ubuntu.com vivid-security/main Sources
Hit http://security.ubuntu.com vivid-security/restricted Sources         
Hit http://security.ubuntu.com vivid-security/universe Sources                 
Hit http://security.ubuntu.com vivid-security/multiverse Sources               
Hit http://us.archive.ubuntu.com vivid-backports InRelease                     
Hit http://security.ubuntu.com vivid-security/main amd64 Packages              
Hit http://us.archive.ubuntu.com vivid/main Sources                            
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/restricted Sources                      
Hit http://security.ubuntu.com vivid-security/universe amd64 Packages          
Hit http://us.archive.ubuntu.com vivid/universe Sources                        
Hit http://us.archive.ubuntu.com vivid/multiverse Sources                      
Hit http://security.ubuntu.com vivid-security/multiverse amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages                     
Hit http://security.ubuntu.com vivid-security/main i386 Packages               
Hit http://security.ubuntu.com vivid-security/restricted i386 Packages         
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages                 
Hit http://security.ubuntu.com vivid-security/universe i386 Packages           
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages               
Hit http://security.ubuntu.com vivid-security/multiverse i386 Packages         
Hit http://us.archive.ubuntu.com vivid/main i386 Packages                      
Hit http://security.ubuntu.com vivid-security/main Translation-en              
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages                
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages                  
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages                
Hit http://security.ubuntu.com vivid-security/restricted Translation-en        
Hit http://us.archive.ubuntu.com vivid/main Translation-en                     
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en               
Hit http://security.ubuntu.com vivid-security/universe Translation-en          
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en               
Hit http://us.archive.ubuntu.com vivid/universe Translation-en                 
Get:2 http://us.archive.ubuntu.com vivid-updates/main Sources [93.8 kB]        
Get:3 http://us.archive.ubuntu.com vivid-updates/restricted Sources [3,687 B]  
Get:4 http://us.archive.ubuntu.com vivid-updates/universe Sources [40.8 kB]    
Get:5 http://us.archive.ubuntu.com vivid-updates/multiverse Sources [1,957 B]  
Get:6 http://us.archive.ubuntu.com vivid-updates/main amd64 Packages [211 kB]  
Get:7 http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages [13.1 kB]
Get:8 http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages [112 kB]
Get:9 http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [5,195 B]
Get:10 http://us.archive.ubuntu.com vivid-updates/main i386 Packages [209 kB]  
Get:11 http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages [12.8 kB]
Get:12 http://us.archive.ubuntu.com vivid-updates/universe i386 Packages [113 kB]
Get:13 http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages [5,394 B]
Hit http://us.archive.ubuntu.com vivid-updates/main Translation-en             
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en       
Hit http://us.archive.ubuntu.com vivid-updates/restricted Translation-en       
Hit http://us.archive.ubuntu.com vivid-updates/universe Translation-en         
Hit http://us.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://us.archive.ubuntu.com vivid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com vivid-backports/main amd64 Packages           
Hit http://us.archive.ubuntu.com vivid-backports/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com vivid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com vivid-backports/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com vivid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://us.archive.ubuntu.com vivid-backports/restricted Translation-en     
Hit http://us.archive.ubuntu.com vivid-backports/universe Translation-en       
Fetched 886 kB in 45s (19.6 kB/s)                                              
Reading package lists... Done
thomas@MACBOOK-UBUNTU:~$ sudo apt-get purge bcmwl-kernel-sources
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-sources
thomas@MACBOOK-UBUNTU:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 277 not upgraded.
Need to get 27.4 kB of archives.
After this operation, 158 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/main b43-fwcutter amd64 1:019-2 [23.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid/multiverse firmware-b43-installer all 1:019-2 [4,120 B]
Fetched 27.4 kB in 3s (8,458 B/s)                 
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 171226 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a019-2_amd64.deb ...
Unpacking b43-fwcutter (1:019-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a019-2_all.deb ...
Unpacking firmware-b43-installer (1:019-2) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up b43-fwcutter (1:019-2) ...
Setting up firmware-b43-installer (1:019-2) ...
No chroot environment found. Starting normal installation
--2015-10-18 20:04:27--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... 173.254.28.119
Connecting to www.lwfinger.com (www.lwfinger.com)|173.254.28.119|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: ‘broadcom-wl-5.100.138.tar.bz2’

broadcom-wl-5.100.1 100%[=====================>]  12.89M  76.7KB/s   in 5m 15s s

2015-10-18 20:09:47 (41.9 KB/s) - ‘broadcom-wl-5.100.138.tar.bz2’ saved [13514651/13514651]

Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
thomas@MACBOOK-UBUNTU:~$ 


```
After that I restarted and nothing had changed. I was still able to connect to my iPhone's hot spot but not my wifi.

---

### Post by tommy25 on 2015-10-18
Sorry for the late response, I got a little preoccupied by school.
I first tried this (While connected to my hot spot)
```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-sources
```
This is what I got back (I just copied and pasted the whole thing)
```
thomas@MACBOOK-UBUNTU:~$ sudo apt-get update
[sudo] password for thomas:
Hit http://us.archive.ubuntu.com vivid InRelease                              
Get:1 http://security.ubuntu.com vivid-security InRelease [64.4 kB]  
Get:2 http://us.archive.ubuntu.com vivid-updates InRelease [64.4 kB]          
Hit http://us.archive.ubuntu.com vivid-backports InRelease                    
Hit http://security.ubuntu.com vivid-security/main Sources                    
Hit http://security.ubuntu.com vivid-security/restricted Sources
Hit http://security.ubuntu.com vivid-security/universe Sources                
Hit http://security.ubuntu.com vivid-security/multiverse Sources              
Hit http://security.ubuntu.com vivid-security/main amd64 Packages              
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages        
Hit http://security.ubuntu.com vivid-security/universe amd64 Packages          
Hit http://security.ubuntu.com vivid-security/multiverse amd64 Packages        
Get:3 http://us.archive.ubuntu.com vivid-updates/main Sources [93.8 kB]        
Hit http://security.ubuntu.com vivid-security/main i386 Packages              
Hit http://security.ubuntu.com vivid-security/restricted i386 Packages        
Hit http://security.ubuntu.com vivid-security/universe i386 Packages          
Hit http://security.ubuntu.com vivid-security/multiverse i386 Packages        
Get:4 http://us.archive.ubuntu.com vivid-updates/restricted Sources [3,687 B]  
Hit http://security.ubuntu.com vivid-security/main Translation-en              
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en        
Get:5 http://us.archive.ubuntu.com vivid-updates/universe Sources [40.8 kB]    
Hit http://security.ubuntu.com vivid-security/restricted Translation-en        
Hit http://security.ubuntu.com vivid-security/universe Translation-en          
Get:6 http://us.archive.ubuntu.com vivid-updates/multiverse Sources [1,957 B]  
Get:7 http://us.archive.ubuntu.com vivid-updates/main amd64 Packages [211 kB]  
Get:8 http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages [13.1 kB]
Get:9 http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages [112 kB]
Get:10 http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [5,195 B]
Get:11 http://us.archive.ubuntu.com vivid-updates/main i386 Packages [209 kB]  
Get:12 http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages [12.8 kB]
Get:13 http://us.archive.ubuntu.com vivid-updates/universe i386 Packages [113 kB]
Get:14 http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages [5,394 B]
Hit http://us.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://us.archive.ubuntu.com vivid-backports/restricted Sources
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Sources
Hit http://us.archive.ubuntu.com vivid-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com vivid-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com vivid-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com vivid-backports/main i386 Packages
Hit http://us.archive.ubuntu.com vivid-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com vivid-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com vivid-backports/main Translation-en
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com vivid/main Sources
Hit http://us.archive.ubuntu.com vivid/restricted Sources
Hit http://us.archive.ubuntu.com vivid/universe Sources
Hit http://us.archive.ubuntu.com vivid/multiverse Sources
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages                
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com vivid/main i386 Packages                      
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages                
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages                  
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages                
Hit http://us.archive.ubuntu.com vivid/main Translation-en                    
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en              
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en              
Hit http://us.archive.ubuntu.com vivid/universe Translation-en                
Hit http://us.archive.ubuntu.com vivid-updates/main Translation-en            
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com vivid-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com vivid-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://us.archive.ubuntu.com vivid-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com vivid-backports/universe Translation-en      
Fetched 951 kB in 3min 35s (4,408 B/s)                                        
Reading package lists... Done
thomas@MACBOOK-UBUNTU:~$ sudo apt-get install --reinstall bcmwl-kernel-sources
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package bcmwl-kernel-sources
thomas@MACBOOK-UBUNTU:~$

```
I restarted after that and nothing had changed. After that, I tried the second set of commands you provided
```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-sources
sudo apt-get install bcmwl-kernel-sources
```
This is what I got back (again, I just copied and pasted the whole thing)
```
thomas@MACBOOK-UBUNTU:~$ sudo apt-get update
[sudo] password for thomas:
Hit http://security.ubuntu.com vivid-security InRelease                    
Hit http://us.archive.ubuntu.com vivid InRelease                            
Get:1 http://us.archive.ubuntu.com vivid-updates InRelease [64.4 kB]  
Hit http://security.ubuntu.com vivid-security/main Sources
Hit http://security.ubuntu.com vivid-security/restricted Sources        
Hit http://security.ubuntu.com vivid-security/universe Sources                
Hit http://us.archive.ubuntu.com vivid-backports InRelease        
Hit http://security.ubuntu.com vivid-security/multiverse Sources        
Hit http://us.archive.ubuntu.com vivid/main Sources
Hit http://security.ubuntu.com vivid-security/main amd64 Packages
Hit http://us.archive.ubuntu.com vivid/restricted Sources          
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com vivid/universe Sources        
Hit http://security.ubuntu.com vivid-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com vivid/multiverse Sources    
Hit http://security.ubuntu.com vivid-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages        
Hit http://security.ubuntu.com vivid-security/main i386 Packages  
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages  
Hit http://security.ubuntu.com vivid-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages    
Hit http://security.ubuntu.com vivid-security/universe i386 Packages
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages  
Hit http://security.ubuntu.com vivid-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com vivid/main i386 Packages      
Hit http://security.ubuntu.com vivid-security/main Translation-en
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages    
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages    
Hit http://security.ubuntu.com vivid-security/restricted Translation-en
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages    
Hit http://security.ubuntu.com vivid-security/universe Translation-en
Hit http://us.archive.ubuntu.com vivid/main Translation-en        
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en
Hit http://us.archive.ubuntu.com vivid/universe Translation-en
Hit http://us.archive.ubuntu.com vivid-updates/main Sources
Hit http://us.archive.ubuntu.com vivid-updates/restricted Sources              
Hit http://us.archive.ubuntu.com vivid-updates/universe Sources                
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com vivid-updates/main amd64 Packages            
Hit http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages        
Hit http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages      
Hit http://us.archive.ubuntu.com vivid-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com vivid-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com vivid-updates/main Translation-en            
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com vivid-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com vivid-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://us.archive.ubuntu.com vivid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com vivid-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com vivid-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com vivid-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com vivid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/main Translation-en          
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com vivid-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com vivid-backports/universe Translation-en      
Fetched 64.4 kB in 12s (5,354 B/s)                                            
Reading package lists... Done
thomas@MACBOOK-UBUNTU:~$ sudo apt-get purge bcmwl-kernel-sources
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package bcmwl-kernel-sources
thomas@MACBOOK-UBUNTU:~$ sudo apt-get install bcmwl-kernel-sources
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package bcmwl-kernel-sources
thomas@MACBOOK-UBUNTU:~$

```
Once again, I restarted and nothing changed. Next, I tried what salmacis suggested:
```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-sources
sudo apt-get install firmware-b43-installer
```
and I got this back (Copy and pasted)
```
thomas@MACBOOK-UBUNTU:~$ sudo apt-get update
[sudo] password for thomas:
Hit http://us.archive.ubuntu.com vivid InRelease                            
Hit http://security.ubuntu.com vivid-security InRelease              
Get:1 http://us.archive.ubuntu.com vivid-updates InRelease [64.4 kB]  
Hit http://security.ubuntu.com vivid-security/main Sources
Hit http://security.ubuntu.com vivid-security/restricted Sources        
Hit http://security.ubuntu.com vivid-security/universe Sources                
Hit http://security.ubuntu.com vivid-security/multiverse Sources              
Hit http://us.archive.ubuntu.com vivid-backports InRelease                    
Hit http://security.ubuntu.com vivid-security/main amd64 Packages              
Hit http://us.archive.ubuntu.com vivid/main Sources                            
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/restricted Sources                      
Hit http://security.ubuntu.com vivid-security/universe amd64 Packages          
Hit http://us.archive.ubuntu.com vivid/universe Sources                        
Hit http://us.archive.ubuntu.com vivid/multiverse Sources                      
Hit http://security.ubuntu.com vivid-security/multiverse amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages                    
Hit http://security.ubuntu.com vivid-security/main i386 Packages              
Hit http://security.ubuntu.com vivid-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages                
Hit http://security.ubuntu.com vivid-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages              
Hit http://security.ubuntu.com vivid-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com vivid/main i386 Packages                      
Hit http://security.ubuntu.com vivid-security/main Translation-en              
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages                
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages                  
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages                
Hit http://security.ubuntu.com vivid-security/restricted Translation-en        
Hit http://us.archive.ubuntu.com vivid/main Translation-en                    
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en              
Hit http://security.ubuntu.com vivid-security/universe Translation-en          
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en              
Hit http://us.archive.ubuntu.com vivid/universe Translation-en                
Get:2 http://us.archive.ubuntu.com vivid-updates/main Sources [93.8 kB]        
Get:3 http://us.archive.ubuntu.com vivid-updates/restricted Sources [3,687 B]  
Get:4 http://us.archive.ubuntu.com vivid-updates/universe Sources [40.8 kB]    
Get:5 http://us.archive.ubuntu.com vivid-updates/multiverse Sources [1,957 B]  
Get:6 http://us.archive.ubuntu.com vivid-updates/main amd64 Packages [211 kB]  
Get:7 http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages [13.1 kB]
Get:8 http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages [112 kB]
Get:9 http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [5,195 B]
Get:10 http://us.archive.ubuntu.com vivid-updates/main i386 Packages [209 kB]  
Get:11 http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages [12.8 kB]
Get:12 http://us.archive.ubuntu.com vivid-updates/universe i386 Packages [113 kB]
Get:13 http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages [5,394 B]
Hit http://us.archive.ubuntu.com vivid-updates/main Translation-en            
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com vivid-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com vivid-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://us.archive.ubuntu.com vivid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com vivid-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com vivid-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com vivid-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com vivid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/main Translation-en          
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com vivid-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com vivid-backports/universe Translation-en      
Fetched 886 kB in 45s (19.6 kB/s)                                              
Reading package lists... Done
thomas@MACBOOK-UBUNTU:~$ sudo apt-get purge bcmwl-kernel-sources
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package bcmwl-kernel-sources
thomas@MACBOOK-UBUNTU:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 277 not upgraded.
Need to get 27.4 kB of archives.
After this operation, 158 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/main b43-fwcutter amd64 1:019-2 [23.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid/multiverse firmware-b43-installer all 1:019-2 [4,120 B]
Fetched 27.4 kB in 3s (8,458 B/s)                
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 171226 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a019-2_amd64.deb ...
Unpacking b43-fwcutter (1:019-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a019-2_all.deb ...
Unpacking firmware-b43-installer (1:019-2) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up b43-fwcutter (1:019-2) ...
Setting up firmware-b43-installer (1:019-2) ...
No chroot environment found. Starting normal installation
--2015-10-18 20:04:27--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... 173.254.28.119
Connecting to www.lwfinger.com (www.lwfinger.com)|173.254.28.119|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: ‘broadcom-wl-5.100.138.tar.bz2’

broadcom-wl-5.100.1 100%[=====================>]  12.89M  76.7KB/s   in 5m 15s s

2015-10-18 20:09:47 (41.9 KB/s) - ‘broadcom-wl-5.100.138.tar.bz2’ saved [13514651/13514651]

Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
thomas@MACBOOK-UBUNTU:~$


```
After that I restarted and nothing had changed. I was still able to connect to my iPhone's hot spot but not my wifi.

---

### Post by mystics on 2015-10-19
I'm sorry, I misspelled the package name, multiple times for that matter.

Try running

```
sudo apt-get purge bcmwl-kernel-source
```

As of right now, that should be the only one you need to run.

In my older (now edited) posts, I added an 's' to source. That misspelling would be the cause of your errors. Again, sorry for not double checking for that.

As for continued problems with firmware-b43-installer, I've read that it doesn't work well if bcmwl-kernel-source is still installed, so try remove that and then see if things work.

---

