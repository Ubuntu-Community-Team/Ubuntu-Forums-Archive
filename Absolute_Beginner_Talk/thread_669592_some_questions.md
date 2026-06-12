---
title: "some questions"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by techtoast on 2008-01-16
i recently installed Ubuntu 7.10 and am very satisfied so far. however, being a complete noob to Linux, i wish to learn more. it's actually the main reason i switched. i was sick of my bill gates infected, hosed over, spyware, adware, and malware apartment of an xp computer so i blew it all out and installed Ubuntu.

i am having some issues with setting up my WLAN connection (linksys). i have my school computer setup with my wireless router and would like to know how i can recover my connection settings and password (windows xp). and second( and just important) how to use it to setup my connection in ubuntu. i am willing to setup anything (including command-line and custom scripts) as long as you give me specifics(including keyboard shortcuts) pn how to do it not just what to do.

if this isn't enough, i managed to screw up my software index. near the end of an update session, i manged to freeze my screen. not to disappointing considering i'm a noob right? but when i went back to restart/finish my updates i received this error message:

Software index is broken
it is impossible to install or remove any software. please use the package manager "synaptic" or run "sudo apt-get install-f" in a terminal to fix this at first.

any help is apreciated!

  -techtoast

---

### Post by PeterJS on 2008-01-16
> **techtoast said:**
> i recently installed Ubuntu 7.10 and am very satisfied so far. however, being a complete noob to Linux, i wish to learn more. it's actually the main reason i switched. i was sick of my bill gates infected, hosed over, spyware, adware, and malware apartment of an xp computer so i blew it all out and installed Ubuntu.

i am having some issues with setting up my WLAN connection (linksys). i have my school computer setup with my wireless router and would like to know how i can recover my connection settings and password (windows xp). It's pretty much impossible to recover the wireless password, which is a good thing, if you can't neither can anyone else. Your best bet is to login to the router from the wired connection, and then set it to a known setup.

> 
 and second( and just important) how to use it to setup my connection in ubuntu. i am willing to setup anything (including command-line and custom scripts) as long as you give me specifics(including keyboard shortcuts) pn how to do it not just what to do.

Well that depends on where in the setup process you are. Are the drivers installed? Is the interface showing up?

> 
if this isn't enough, i managed to screw up my software index. near the end of an update session, i manged to freeze my screen. not to disappointing considering i'm a noob right? but when i went back to restart/finish my updates i received this error message:

Software index is broken
it is impossible to install or remove any software. please use the package manager "synaptic" or run "sudo apt-get install-f" in a terminal to fix this at first.

any help is apreciated!

  -techtoast
 You've got your answer already fire up a terminal and run:
```

sudo apt-get install-f

```

---

### Post by techtoast on 2008-01-16
ok, i found a utility that found my hex key. but it's 64 characters long. how do i decrypt this to the 10 digit code required?

second, how do i start a terminal? (I'm a noob)

---

### Post by PeterJS on 2008-01-16
> **techtoast said:**
> ok, i found a utility that found my hex key. but it's 64 characters long. how do i decrypt this to the 10 digit code required?
Is it WEP, or WPA? for WPA good luck. For WEP just having the hex key is enough.

> 
second, how do i start a terminal? (I'm a noob)
Applications > Accessories > Terminal

---

### Post by techtoast on 2008-01-16
ah, i got a terminal running and tried to run the code but i got this message:

E: Invalid operation install-f

what does this mean/how do i fix it?

thanks for your help!

---

### Post by PeterJS on 2008-01-16
install[space]-f

Apt-get install is the standard method to install things from the command line. The install bit tells apt-get what function it's supposed to be doing (other common options are update and upgrade). The -f flag tells it to force finish any incomplete installs.

---

### Post by eolson on 2008-01-16
To start a terminal
   Applications > Accessories > Terminal

or

cntrl/alt F1 thru F6   then to return cntrl/alt F7

I prefer the first method.

On the keycode,  I don't think that's the code you need.  My particular router has the long keycode of umpteen jillian characters,  but what it wants to login is the Netkey of 10 characters.   Snoop around on the bottom and back of your router and see if you can find a 10 digit number someplace.  Probably in close proximity to the serial number.

---

### Post by perlluver on 2008-01-16
> **techtoast said:**
> ah, i got a terminal running and tried to run the code but i got this message:

E: Invalid operation install-f

what does this mean/how do i fix it?

thanks for your help!

That is ```
sudo apt-get install -f
``` note the space.

---

### Post by bodhi.zazen on 2008-01-16
sudo apt-get install -f (there is a space between install and -f )

---

### Post by techtoast on 2008-01-16
[quote]Is it WEP, or WPA? for WPA good luck. For WEP just having the hex key is enough.
[/qoute]

i believe it is WPA-PSK. is there a way to recover the password via a direct patch? if so, how would i go about doing so?

---

### Post by ugm6hr on 2008-01-16
> **techtoast said:**
> i believe it is WPA-PSK. is there a way to recover the password via a direct patch? if so, how would i go about doing so?

By direct patch - do you mean a patch cable (ethernet CAT5/6)?

You generally cannot *recover* a passphrase, but you should be able to change it to something new by going into the router setup page (probably something like 192.168.0.1)

Or it is likely the router has a hardware reset button (probably a small recessed button on the bottom or back that can only be pressed with a pen).  That generally resets *everything* though, so make sure you know your broadband username and password (from your ISP) if it is a combined modem-router before doing this.  Most routers default to an open wifi network, although apparently some have their wifi turned off as default.

---

### Post by techtoast on 2008-01-16
O.O so many complications... i retyped the sudo apt-get install -f.
it tols me to run dpkg --configure -a. 
no big deal. but when i tried to run it, it said i must have superuser privelege.

what does that mean?!?!?! i should just have to enter my admin password right?

---

### Post by techtoast on 2008-01-16
> **ugm6hr said:**
> By direct patch - do you mean a patch cable (ethernet CAT5/6)?

You generally cannot *recover* a passphrase, but you should be able to change it to something new by going into the router setup page (probably something like 192.168.0.1)

Or it is likely the router has a hardware reset button (probably a small recessed button on the bottom or back that can only be pressed with a pen).  That generally resets *everything* though, so make sure you know your broadband username and password (from your ISP) if it is a combined modem-router before doing this.  Most routers default to an open wifi network, although apparently some have their wifi turned off as default.

since i have my router connected to 3 computers, i would rather not have to do an all around reset.

---

### Post by ugm6hr on 2008-01-16
> **techtoast said:**
> O.O so many complications... i retyped the sudo apt-get install -f.
it tols me to run dpkg --configure -a. 
no big deal. but when i tried to run it, it said i must have superuser privelege.

what does that mean?!?!?! i should just have to enter my admin password right?

It means to run the command with *sudo* at the start of the line.

> since i have my router connected to 3 computers, i would rather not have to do an all around reset.

Unless you have stored the passphrase somewhere, you normally can't get it off either the router or a Windows machine.  Most routers blank out the passphrase box (like this ********), as does Windows.  If one of the other machines is Ubuntu, you can sometimes retrieve the passphrase by selecting "show password" (or something like that, I think).

Best bet is to log into the router's setting page from one of the other 3 computers, change the passphrase to something new, and then re-enter the new passphrase on all the machines.  Unless you can read the passphrase from your router's settings page.

---

### Post by techtoast on 2008-01-16
ah, that makes sense. i am now installing the 198 available updates. 1 down, 1 to go.

---

### Post by techtoast on 2008-01-16
is there a way to scan for networks in ubuntu?

---

### Post by ugm6hr on 2008-01-16
> **techtoast said:**
> is there a way to scan for networks in ubuntu?

Yes. Click on the Network Manager icon at the top right panel (in the system tray).  It looks like a computer screen, two grey/green dots or 4 grey/green bars (depending on status).

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

---

### Post by techtoast on 2008-01-16
i don't have that icon for a lack of wirless connection. i have one for a wired connection but all i can do is enter all my wireless information.

---

### Post by FenderGuy2112 on 2008-01-16
Wait, what kind of security is on your router as of now, and do you  remember the user and pass for it?


FenderGuy2112

---

### Post by ugm6hr on 2008-01-16
> **techtoast said:**
> i don't have that icon for a lack of wirless connection. i have one for a wired connection but all i can do is enter all my wireless information.

Do you broadcast your SSID?

If you do - then the problem is likely to be that Ubuntu has not configured your wifi card properly.

The outputs from these commands will help pinpoint where the issue is:
```
lspci
ifconfig
iwconfig
lshw -C network
```

---

### Post by techtoast on 2008-01-16
hmmm, i not sure what you mean by BROADCAST my ssid. can you explain?

---

### Post by techtoast on 2008-01-16
ok, i used those commands and i received this:



techtoast@techtoast-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:02.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:02.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:02.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
techtoast@techtoast-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:92:7B:3A  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe92:7b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9346778 (8.9 MB)  TX bytes:1690669 (1.6 MB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

techtoast@techtoast-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:92:7B:3A  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe92:7b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8951 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9360550 (8.9 MB)  TX bytes:1696752 (1.6 MB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

techtoast@techtoast-laptop:~$ lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

---

### Post by ugm6hr on 2008-01-17
```
02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

You have a Broadcom wifi card.  Hence it will not work out-of-the-box.  That is why you can't scan for networks.

These cards have always been a bit tricky, but a quick search revealed this: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%284318%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%284318%29)
Note this looks like it is for Gutsy, and I suspect that some of the steps in that how-to are probably unnecessary now.  If you search for 4318 on these forums, you might find something more recent.

Can your other computers scan and find your wifi router?  If yes, you are broadcasting the SSID.

And you mistyped 2 of the commands.  But never mind.  In future - copy and paste is often easier.

EDIT: Another quick forum search suggests that if you got to Restricted Driver Manager, you should be able to load the native driver firmware, which is an alternative way (from ndiswrapper) to use the Broadcom card.
[http://ubuntuforums.org/showthread.php?t=660871&highlight=4318](http://ubuntuforums.org/showthread.php?t=660871&highlight=4318)

This is another ndiswrapper How-to: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by techtoast on 2008-01-20
thanks for all the help!, i recovered windows and re-installed my router. i took note of and recorded my network passwords and names. i know it's somewhere on this forum but could someone tell me how to resize my windows partition without corrupting my windows install? i tried it once but failed. 2 hours and a headache later i wish not to try it again unless i'm sure that i will not corrupt windows. i wish to resize my windows partition so that i have free space to install ubuntu to (again). (i have programs that require windows).

---

### Post by rosegarden78 on 2008-01-20
TechToast - you consider locating and pressing the reset switch on your router.  Visit the online documentation for instruction of setting up your router.  I have a linksys it's easy to reset just hold the button for 30 sec.

Then login to router via web browser by typing 192.168.1.1
Linksys.com has instruction how to do this.

If your router and modem both use 192.168.1.1 
change your router address to 192.168.2.1
or else memory conflict cripples network.

Make sure you have network-manager or nm-applet installed.
Please consider updating User CP to tell us what distro you're using.

---

### Post by ugm6hr on 2008-01-20
> **techtoast said:**
> thanks for all the help!, i recovered windows and re-installed my router. i took note of and recorded my network passwords and names. i know it's somewhere on this forum but could someone tell me how to resize my windows partition without corrupting my windows install? i tried it once but failed. 2 hours and a headache later i wish not to try it again unless i'm sure that i will not corrupt windows. i wish to resize my windows partition so that i have free space to install ubuntu to (again). (i have programs that require windows).

There is no way to resize partitions without *some* risk to data.  However the risk is minimal.  Nevertheless, if there is anything important on there, you should back-up before starting.

If you want to try: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

