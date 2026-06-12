---
title: "USB wirless internet"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by jgrf77 on 2007-08-30
I am very new to ubuntu and don't really have a clue about much at all. I am running xubuntu and have just connected to broadband.  For convenience I have wireless internet.  I have a wireless usb dongle which when plugged in appears in my network settings (wnlan0)  (a second one also appears (wmaster0 i think but i have no idea what that is).  I am unsure what to do next to get the wireless connection up ad running.  Do i need to install a driver or not because clearly my computer detects the dongle? if not do i just need to configure it properly? several hours of internet searching has found me very little but maybr thats because i'm not looking properly........any help would be much appreciated.

cheers

jgrf77

---

### Post by chrome307 on 2007-08-30
I installed the drivers of USB dongle manually and it works for me using NDISWrapper.

Screenshots/commands/instructions are here:

[http://ubuntuforums.org/showthread.php?t=534617](http://ubuntuforums.org/showthread.php?t=534617)

[IMG]http://i11.tinypic.com/4tfqgkl.jpg[/IMG]

---

### Post by jgrf77 on 2007-09-25
thanks a lot

Looked through that link you gave me (looks very good thanks).  Tried installing ndiswrapper by following the instructions and got

justin@Justinotronic:~$ tar zxvf ndiswrapper-1.47.tar.gz
tar: ndiswrapper-1.47.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

and am not sure how to over come it
the path is

file:///home/justin/Downloads/ndiswrapper-1.47.tar.gz

any ideas?

otherwise  the situation is

justin@Justinotronic:~$ iwlist wlan0 scan
wlan0     No scan results
justin@Justinotronic:~$ iwlist wmaster0
iwlist: unknown command `wmaster0'
justin@Justinotronic:~$ iwlist wlan0 scan
wlan0     No scan results
justin@Justinotronic:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"192.168.1.1."  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
justin@Justinotronic:~$ lsusb
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 001 Device 001: ID 0000:0000  
justin@Justinotronic:~$ 


Anyone out there have any ideas as to how i can get my wireless working?

thanks a lot for all the help

justin

---

