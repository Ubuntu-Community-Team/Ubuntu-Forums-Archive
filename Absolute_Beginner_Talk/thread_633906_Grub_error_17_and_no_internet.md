---
title: "Grub error 17 and no internet"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mpjf01 on 2007-12-07
Installed Kubuntu 7.10, dual boot option with XP -  got a Grub error 17. Looked in the Kubuntu forums and tried all the suggestions including supergrub - nothing fixed it. Then tried restoring the mbr from the XP cd - said it had done it, but still got the Grub error. Downloaded Ubuntu (fortunately have other Windows PC's on a LAN) and went through the whole install process again - exact same result. Wondered whether problem had something to do with the fact that my PC has 2 IDE and 2 SATA drives. Disconnected the SATA s and suddenly no Grub error - can dual boot - hooray I think (but wondered why the installers didn't warn me). Tried to install additional Ubuntu programs - wants  internet access and should have it - but every time I try to access the internet using Firefox in Ubuntu my router and line goes down. Can ping everywhere with Network Tools with no problem until I run Firefox.

Router is Dlink 604T and works fine with my other Windows PCs until I run Ubuntu Firefox. Works fine after I turn off Ubuntu Firefox. 

I want to reconnect my 2 SATA disks - from what I have read here it seems that maybe it's because Grub can't find the right disk when the SATA drives are connected - perhaps is defaulting to one of them but the MBR is on my first IDE drive (the one with XP on it). This should be able to be changed easily, I imagine, so any help would be appreciated. 

Internet access would be nice to get working too - I have looked around in Firefox to see if there are any settings to try changing but can't see anything obvious. In case its not clear my total experience with Unix/Linux is less than 1 day so I really know nothing.

---

### Post by bumanie on 2007-12-07
I would look at this link re grub and the problems encountered with mixed drives ie sata and ide
[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)
It has heaps of info. on grub so you may have to read a bit to find the specific part about hdd's.
Regarding your lack of internet access, some gutsy users have had to blacklist ipv6 to get their internet working. In terminal type
gksudo gedit /etc/modprobe.d/blacklist
This provides you with a list in a window. At the end of the list type
blacklist ipv6 
Save the change and reboot your computer. All going well, you should then get internet access.

---

