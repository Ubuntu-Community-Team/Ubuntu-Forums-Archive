---
title: "unable to add wireless device"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by flemingms on 2006-07-19
I just installed ubuntu 6.06 on my pc clone. Everything works well except my wireless connection. I am using a usb link a WUSB11. The links I've found say it works, simply add a wireless network from the networking window.

The problem I'm having: The networking window does not have an option to add a network. It displays ethernet and modem but does not have a tab to add another resource. The documentation shows an "add" option. Do you have any ideas regarding why I am not seeing an option to add a wireless network?

When I click on system, administration, networking, the system does ask for a password, so I assume that means I am active as administrator.

Thanks for your consideration.

---

### Post by Dr. Nick on 2006-07-19
the wusb11 is a funny card, Thier are several revesions of that model, all who behave differently. I have a wusb11 v3 which I got working a few different ways, 1 being ndiswrapper the other being the native build in drivers.

Look at the sticker on bottom of the card and find out which version you have, it in the top corner I believe. Once you find the version it will be alot easier to get help since its a somewhat differnet procedure for each.

---

### Post by flemingms on 2006-07-21
Thanks for your reply. The WUSB11 is version 4.

---

### Post by Dr. Nick on 2006-07-21
hmm.. Not much mention of the V4 on the forums, Run the following command from a terminal and look at the line that says "usbcore" 

**lsmod**

the usbcore line will tell you if their are any native drivers loaded for that card. If thier are native drivers loaded then you can research how to get them to work, or disbale them and go the ndiswrapper route, which will require a set of windows drivers for the card

---

### Post by skale on 2006-07-21
Remember that USB wirelesses are cranky, I gave up on mine and bought a long ethernet cable. ;)

---

### Post by bensexson on 2006-07-21
Post the output from lsusb.

---

### Post by bensexson on 2006-07-21
Also post the output from ifconfig -a and iwconfig.

---

### Post by foxjwill on 2006-07-21
I'm having the exact same problem (with WUSB11 v4).

```
usbcore               129668  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

root@celloboy:~# lsusb
Bus 005 Device 004: ID 046d:08c5 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 005: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 004: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

root@celloboy:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:07:E9:7E:55:EA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1656 (1.6 KiB)  TX bytes:1656 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@celloboy:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

---

### Post by Dr. Nick on 2006-07-21
foxjwill

It looks like their isnt a driver for your card judging by the lsmod output.

I would look into ndiswrapper so you could use the windows drivers

---

### Post by foxjwill on 2006-07-21
> **Dr. Nick said:**
> foxjwill
I would look into ndiswrapper so you could use the windows drivers

The installation directions for ndiswrapper ask me to use the command 'make install', but when I do, it says
```
bash: make: command not found
```
And I'm in the 'ndiswrapper-1.21' directory.

---

### Post by flemingms on 2006-07-21
Thanks for the suggestions. I executed the commands suggested. The output looks very similar to the other wusb11v4 user so I am guessing that the next step is the ndiswrapper. Anyway, I'll post my outputs in case I missed some difference.

Thanks,
Matt

matt@matt-desktop:~$ lsmod

usbcore               129668  2 ohci_hcd

matt@matt-desktop:~$ lsusb
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 002 Device 001: ID 0000:0000

matt@matt-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:06:F2:16:4F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1556 (1.5 KiB)  TX bytes:1556 (1.5 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

matt@matt-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by foxjwill on 2006-07-21
I found that, instead of using the entry on the ndiswrapper list for WUSB11v4, using the one that came with my cd worked. Their way didn't.

---

### Post by Dr. Nick on 2006-07-22
so is your wireless working now foxjwill? I noticed you were doing the make install routine, That is most likely not necessary. You can easily install ndiswrapper in synaptic or using apt-get/aptitude, may not have to download and compile the source.

The package needed is ndiswrapper-utils. Their is also a gui for it called ndisgtk. It will add a option to setup the drivers 
System - Adminstraion - Windows Wireless Drivers


I had the best luck using my wusb11 v3 driver cd aswell.

---

### Post by foxjwill on 2006-07-22
yes. It's working now. Thank you *very* much.

---

### Post by bensexson on 2006-07-22
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by flemingms on 2006-07-25
Thanks to all. This morning I am typing this message from my new Ubuntu driven machine!

Steps that ended in success for me:
1) loaded ndiswrapper utils and graphical interfaces as described in help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper.
2) In Ubuntu, loaded drivers from my WUSB11R4 CD that came from Linksys into a directory on my harddrive. I copied all the stuff from the driver folder on the CD.
3) Used System/Administration/WindowsWirelessDrivers to install the driver (WUSB11V4.inf). 
4) Moved to Networking section and the wireless network was FINALLY there. Used properties to set keys.
5) Firefox now loads the internet!:)

---

### Post by flemingms on 2006-07-25
Well almost. When I turn the machine off, the network does not come back. I've found that re-activating the wireless network works but  it's annoying to do that each time. 

I've seen on other threads that this may be a problem with Ubuntu. LMK if you have a fix.

Thanks.

---

### Post by Dr. Nick on 2006-07-25
Just a idea but have you went into the net control panel and disabled eth0 if it is not necessary? Just open eth0 and uncheck "enable this connection" that may help some.

---

### Post by FlowerPunk on 2006-07-30
Calling Dr Nick!

After a loooong and fruitless search of this and other forums, I am up against a brick wall with trying to get my WUSB11 v3 working with the latest version if Ubuntu... Dr. Nick, you say you managed to get your usb card to work - would you mind posting a quick & dirty "how-to"? :D 

FlowerPunk

---

### Post by Dr. Nick on 2006-07-30
I can try ;)

first you have to decide if you want to use the native prism2_usb driver, or if you want to get rid of it and use ndiswrapper.

A few pros and cons that I have noticed between the 2, this is over a long period of time and some of that time spent on older versions of ubuntu, so some cons may be better now.

Ndiswrapper

**[COLOR=PaleGreen]Pros: [/COLOR]**
**Pretty easy to setup if you have the origional driver cd**
You can do all the configuration through GUI tools
[COLOR=Red]Cons:[/COLOR]
**My signal stregnth was always 100%, even when I was a long way away, obviously it doesnt work :)**
Programs like kismet and a few other "wireless security" tools will not work with ndiswrapper
**You must blocklist the prism2 driver to prevent conflict**

Prism2 driver
[B][COLOR=PaleGreen]
Pros[/COLOR][/B]
signal stregnth works
** kismet will work**
Its a native driver (If that matters)

[COLOR=Red] Cons:[/COLOR]

** For me and others it has been a pain to get going**
requires you to edit configuration files by hand due to the next reason
[B] The included GUI configuration tools are not of much use since prism2 drivers do not use the standard system to make changes(actually just saw a possible fix just now, I havent tried it yet, will post link at the end)

[/B]If you decide you want to use ndiswrapper then get your cdrom and enable the extra repositories in apt-get then run the following command, If you want native skip to the very bottom
```

sudo aptitude install ndiswrapper-utils ndisgtk
``` 
then you must blacklist the native prism2 driver

run the below command and check the usbcore line, you should see prism2_usb listed if it is a v3 card.

```
lsmod
``` 
To blacklist it run the following command and add the line to the bottom, then save and exit

```
gksudo gedit /etc/modprobe.d/blacklist 
``` [B]
blacklist prism2_usb[/B]

At this point you may either restart the computer and make sure prism2_usb doesnt load by rerunning lsmod, or you can just remove the prism2_usb module by hand temporarily. the following command only works until a reboot, but with the blacklist it shouldnt matter
```

sudo modprobe -r prism2_usb
``` 
The above should effectively stop the native driver from loading thus avoiding conflicts.

Now to set up ndiswrapper

In gnome go to System - Adminsitration -  Windows wireless drivers

Hit install new driver and navigate to the lspmusb.inf file from your cd, after loading that it should say Hardware Present:Yes

Then hit configure network and your wireless device should appear in the list, set it up and you should be good to go. if your card still doesnt show then run 

```
sudo modprobe ndiswrapper
``` followed by ```
lsmod
``` to confirm that ndiswrapper is loaded and prism2_usb isnt.

To confirm that ndiswapper loads up on boot run
```

gksudo gedit /etc/modules
``` 
and add

**ndiswrapper**

to that file if it isnt their already


Now If you want to use the native prism2 driver then the wireless device should appear in the networking control panel already. If so then look here
[https://launchpad.net/distros/ubuntu/+source/linux-wlan-ng/+bug/37451](https://launchpad.net/distros/ubuntu/+source/linux-wlan-ng/+bug/37451)

I need to test that out aswell. After my initial prism2 expierence i went to ndiswrapper, but may apply the patch and try prism2 again

---

### Post by FlowerPunk on 2006-07-31
Dr. Nick - 

Success!

I couldn't use the native drivers, as the device didn't appear in the networking control panel. It did however show up under device manager as an unknown USB wireless device (go figure). 

Anyways, I used ndiswrapper and am wireless as we speak! :D

Thank you for you help. 


FlowerPunk

---

### Post by Dr. Nick on 2006-07-31
Glad it worked for you!

---

### Post by flemingms on 2006-08-02
My wireless usb link (WUSB11V4) was up for a little while. The system was very unstable. I tried to update Ubuntu via the internet connection. On first try, the system crashed. On reboot, when I tried to continue, I got an error message to execute a command from the terminal to fix something (I failed to write that command down). After fixing that, the download seemed to work.

From package manager, I attemted to install the upgrades. The system crashed and would not reboot.

I reinstalled Ubuntu from the CDROM. Now, when I load drivers from the wireless grapical interface, the configuration is not working. The networking software does not recognize that the device is there. I thought I did everything identically to the first time.

Can you suggest how to debug the problem?

Also, the list of wireless USB devices at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) suggests a file for the WUSB11V4 that is an EXE file. What do I do with that? Ubuntu does not run WINE (I think) so I do not know how to use that file on my system.

Thanks (argh!)

---

### Post by Dr. Nick on 2006-08-02
the .exe file can probably be extracted using file-roller or another unzip utility in linux, or windows if you have it aswell. It is most likely just a self-unzipping exe in windows.

If you happen to still have you driver cd for the card that should work aswell and will not require extraction.

---

### Post by flemingms on 2006-08-05
I loaded the driver from the CD that came with the WUSB11V4. It loads and configures. However, my system is quite unstable after I've loaded the driver. It crashes frequently when downloading from the internet. From what I've read, this seems fairly common but I've not seen many clear solutions.

Any suggestions appreciated. 

I'm considering getting a PCI card or wireless bridge. Do you know of any inexpensive ones with high likelihood of success?

Thanks.

---

### Post by Dr. Nick on 2006-08-05
sorry, cant be of much help their, my wusb11 v3 is the only wireless expierence i have had so I am not sure how the pci cards and bridges work

---

### Post by flemingms on 2006-08-23
I gave up. I got the WUSB11V4 to work, but never very reliably. When using the internet, my system would frequently crash. It made loading updates very exciting. From what I've been able to gleen from other posts, this is not an unusual situation as lots of folks have found the USB interface unstable. It might be possible to make it work, but I never hit on the right combination.

So... I popped $40 on ebay for a WET11 ethernet bridge. It works right out of the box and so far (fingers crossed), the system seems very stable. I hated to spend extra $$ on a free operating system, but it was just too unstable to play. 

BTW, the bridge seems to run a lot faster than the USB did, even under windows.

Thanks for the help and suggestions on this problem. I learned a lot in the process.

---

### Post by Dr. Nick on 2006-08-23
Glad you got it worked out one way or another, I didnt have the best luck with the v3 either, I rarely had it take out the system though, Hopefully they can get native drivers that are a little better then using ndiswrapper.

---

