---
title: "Installing ndiswrapper"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by thrasher on 2005-11-24
I know, i'm getting annoying ;) 

well, i tried to install my usb wlan-dongle, just like i did in suse... 
i got the newest ndiswrapper from sourceforge and took a look in the manual for installation hints. ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation))

Well, first thing is that i have to install kernel-source and to compile it... so i loaded the kernel-sources and gcc (which wasn't installed) and tried

**root@ubuntu:/usr/src/linux-source-2.6.10# make**

it said, that there's no config and i should do make config /menuconfig first...
i did this (but made no changes) and saved the new config - then 

**root@ubuntu:/usr/src/linux-source-2.6.10# make**

worked without any error..
then i placed a link to the source in /lib/modules
**root@ubuntu:/usr/src/linux-source-2.6.10# ln -s /usr/src/linux-source-2.6.10-5-686 /lib/modules/2.6.10-5-686/build**

so i got to the ndiswrapper-directory and continued installation: 

**root@ubuntu:/tmp/ndiswrapper/ndiswrapper-1.5# make**
**root@ubuntu:/tmp/ndiswrapper/ndiswrapper-1.5# make install**

no errors on both
next step: 

**root@ubuntu:/tmp/ndiswrapper/ndiswrapper-1.5# ndiswrapper -i /WinXp/WlanUIG.inf**

(with /WinXp being the folder which contains both .inf and .sys)
no problems either... but when i modprobe'd ndiswrapper

**root@ubuntu:/tmp/ndiswrapper/ndiswrapper-1.5# modprobe ndiswrapper**
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and this is the dmesg output for ndiswrapper: 
ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
ndiswrapper: Unknown symbol per_cpu__softnet_data
ndiswrapper: disagrees about version of symbol misc_deregister
ndiswrapper: Unknown symbol misc_deregister
ndiswrapper: disagrees about version of symbol create_proc_entry
ndiswrapper: Unknown symbol create_proc_entry
ndiswrapper: disagrees about version of symbol proc_net
ndiswrapper: Unknown symbol proc_net
ndiswrapper: disagrees about version of symbol proc_mkdir
ndiswrapper: Unknown symbol proc_mkdir
ndiswrapper: disagrees about version of symbol misc_register
ndiswrapper: Unknown symbol misc_register
ndiswrapper: disagrees about version of symbol netif_rx
ndiswrapper: Unknown symbol netif_rx
ndiswrapper: disagrees about version of symbol remove_proc_entry
ndiswrapper: Unknown symbol remove_proc_entry
ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
ndiswrapper: Unknown symbol per_cpu__softnet_data
ndiswrapper: disagrees about version of symbol misc_deregister
ndiswrapper: Unknown symbol misc_deregister
ndiswrapper: disagrees about version of symbol create_proc_entry
ndiswrapper: Unknown symbol create_proc_entry
ndiswrapper: disagrees about version of symbol proc_net
ndiswrapper: Unknown symbol proc_net
ndiswrapper: disagrees about version of symbol proc_mkdir
ndiswrapper: Unknown symbol proc_mkdir
ndiswrapper: disagrees about version of symbol misc_register
ndiswrapper: Unknown symbol misc_register
ndiswrapper: disagrees about version of symbol netif_rx
ndiswrapper: Unknown symbol netif_rx
ndiswrapper: disagrees about version of symbol remove_proc_entry
ndiswrapper: Unknown symbol remove_proc_entry
ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
ndiswrapper: Unknown symbol per_cpu__softnet_data
ndiswrapper: disagrees about version of symbol misc_deregister
ndiswrapper: Unknown symbol misc_deregister
ndiswrapper: disagrees about version of symbol create_proc_entry
ndiswrapper: Unknown symbol create_proc_entry
ndiswrapper: disagrees about version of symbol proc_net
ndiswrapper: Unknown symbol proc_net
ndiswrapper: disagrees about version of symbol proc_mkdir
ndiswrapper: Unknown symbol proc_mkdir
ndiswrapper: disagrees about version of symbol misc_register
ndiswrapper: Unknown symbol misc_register
ndiswrapper: disagrees about version of symbol netif_rx
ndiswrapper: Unknown symbol netif_rx
ndiswrapper: disagrees about version of symbol remove_proc_entry
ndiswrapper: Unknown symbol remove_proc_entry
ndiswrapper: disagrees about version of symbol per_cpu__softnet_data
ndiswrapper: Unknown symbol per_cpu__softnet_data
ndiswrapper: disagrees about version of symbol misc_deregister
ndiswrapper: Unknown symbol misc_deregister
ndiswrapper: disagrees about version of symbol create_proc_entry
ndiswrapper: Unknown symbol create_proc_entry
ndiswrapper: disagrees about version of symbol proc_net
ndiswrapper: Unknown symbol proc_net
ndiswrapper: disagrees about version of symbol proc_mkdir
ndiswrapper: Unknown symbol proc_mkdir
ndiswrapper: disagrees about version of symbol misc_register
ndiswrapper: Unknown symbol misc_register
ndiswrapper: disagrees about version of symbol netif_rx
ndiswrapper: Unknown symbol netif_rx
ndiswrapper: disagrees about version of symbol remove_proc_entry
ndiswrapper: Unknown symbol remove_proc_entry

where did i mess up again? :mad: 

Thrasher (sorry for the loads of text, but i hope this specifies my problem more clearly)

---

### Post by aznboi on 2005-11-24
you could have easily done apt-get install ndiswrapper-utils

what happens when you do:
ndiswrapper -l
(that character is a lowercase L so u dont get confused cuz it looks similar to |)

---

### Post by thrasher on 2005-11-24
yeah, forgot that apt feature...
ndiswrapper -l

Installed ndis drivers:
wlanuig         driver present

to me (as a noob) it seems like i did something wrong with the kernel-source, but i can't point my finger on it...

edit: and ndiswrapper-utils doesn't contain kernel-module

---

### Post by aznboi on 2005-11-24
try following this guide, I did it and my wifi card works great.
```
http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver
```

---

### Post by thrasher on 2005-11-24
hmpf..

> 
i got the newest ndiswrapper from sourceforge and took a look in the manual for installation hints. ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation))


doesn't work on my system :confused: did the same thing with suse and it worked within a few minutes...

---

### Post by marlobello on 2006-04-02
Problems like this are what is really keeping Linux from the average users desktop. Trying to get a wireless connection on my linux desktop has been the biggest fiasco I have ever experienced. I did find a nice tutorial on how to get my new wireless card working at 

[http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide](http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide)

However this leaves me with a huge chicken and the egg problem. Apparently ndiswrapper doesn't come with ubuntu. I obviously need wireless to get on my network, yet I need network to apt-get ndiswrapper and in theory to get the win32 driver (though I was able to get this and transport it with a flash drive). So unless I am missing something, I have three options:

1. Download ndiswrapper and compile it from scratch (I am not to fond of this on a packaged based system).
2. Haul my computer to where my internet connection is, plug in a land line so I can get ndiswrapper from apt.
3. Buy a uber-long patch cable to stretch from my internet connection to my desktop so I can get ndiswrapper from apt (kinda defeats the purpose of using a wireless card)

So it seems to me that in this case my grandma couldn't use linux cuz she doesn't know how to compile source code, can't lift a desktop around the house and can't afford a 100 meter patch cable.

Just my $0.02

---

### Post by CromagTheTech on 2008-04-22
I'm at the same dilema...a guy I work with swears by ubuntu however in my recent experiences there is no simple way to do anything with linux or atleast the ubuntu distro. None of my wireless cards -ever- work...so therefore I can't apt-get anything. If I want to copy a program for instance drag and drop..oh wait i can't do that either unless I first open up a terminal and sudo my rights in. Oh then if I finally get the rights to write to a folder I might have to compile the program anyway. This is supposed to be the most user friendly distro out there but it hasn't been friendly at all to me. I'm constantly having to look up commands to do menial tasks that I could just 'do' in windows...maybe because i'm so used to windows. I can't get used to something this complicated. No wonder its not mainstream used or sold in Wal-Mart..average joe can run windows whether he knows anything about it or not, i would like to see your average joe install ubuntu on a laptop and wonder why his wireless network isn't picking up..oh yeah..he has to run a script or compile ndiswrapper and make sure that he has the latest kernel. So far..I am NOT happy with ubuntu or any linux distro..I couldn't even get Backtrack 2 to install right...its alot of work and there is no pay off cause most of the time it's probably not gonna work right anyway.

---

### Post by kevdog on 2008-04-22
Please stop complaining.  Learning a new OS is not easy.  If you guys ever heard of a USB flash drive, you could download things like the ndiswrapper source packages and drivers onto a flash driver and bring them to the ubuntu machine.  The rest of the build utilities are on the installation disk.  Ive written a post that basically describes most of this process -- installing ndiswrapper from svn (search for it).  MS doesnt come with a built in compiler to compile your programs.  You might at first say "who cares" but after you compile a few programs and really learn the benefits of this approach, you'll be unhappy with the old MS model -- and the software linux repository -- that is fantastic!  Give it a chance -- all beginners including myself complained at the beginning.  After about a week however Ive been flying ever since.

---

### Post by sk10us on 2008-05-02
refer to this 

venkatmsk.blogspot.com

---

### Post by Ditzzodawg on 2008-05-09
Hi - I am new (2 weeks old) to the Linux world as well. I have learned a lot in my 2 weeks just using google and Wiki. I have just switched from Freespire to Ubuntu as I was having no luck on Freespire installing NDISwrapper with my WG311V3 card. I did get some positive action out of Ubuntu, but haven't successfully completed the install yet. My point is, we are not complaining, just asking for help. Linux is a world of difference from the Win world (which I still like for it's "ease" of use). I am very dedicated to learning linux right now, just frustrated with how hard it is to get started. I am going to try one of the GUI programs for installing NW and see if I can get anywhere like that. BTW these forums are a great help!

---

