---
title: "ndiswrapper is a pain!"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-06-07
OK. I compile the new version of ndiswrapper via [this Wiki](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto), right?

IMPORTANT: I have recently upgraded to 6.06 Ubuntu.

Anyway, I try to use fakeroot, and this happens:

```
coleman@ColemanNetwork:~/ndis/ndiswrapper-1.17$ fakeroot debian/rules binary-modules
/usr/bin/fakeroot: line 150: debian/rules: No such file or directory

```

OK... So fakeroot isn't working, even though I used apt-get to update it. Whatever, no big deal, I just run 'sudo make' and 'sudo make install'. Fine. Now it's installed.

I get through the terminal, telling it to install my .inf file. I typ 'ndiswrapper -l', it recodnizes the driver and the hardware. Good start.

I go into Network Settings. The WiFi settings aren't there... Oh yea, forgot to modprod.

Then THIS CRAP HAPPENS!

```
coleman@ColemanNetwork:~$   sudo depmod -a
coleman@ColemanNetwork:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/misc/ndiswrapper.ko): Invalid argument
```

Cute. Real cute. I can't work around the damn thing...

Can someone PLEASE help? I post topics but people just blow them off.

ndiswrapper worked perfectly with 5.10. UGH.

---

### Post by az on 2006-06-07
If it worked fine in breezy, it's probably because ther ewas nothing getting in the way for it to work.  You probably have a device that now has linux support in Dapper.

Find out what device it actually is and see if you can get the native linxu driver to work for you, or find out what kernel module to blacklist.

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by Nequeo on 2006-06-07
[QUOTE=SZF2001]OK. I compile the new version of ndiswrapper via [this Wiki](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto), right?

IMPORTANT: I have recently upgraded to 6.06 Ubuntu.

Anyway, I try to use fakeroot, and this happens:

```
coleman@ColemanNetwork:~/ndis/ndiswrapper-1.17$ fakeroot debian/rules binary-modules
/usr/bin/fakeroot: line 150: debian/rules: No such file or directory

```

OK... So fakeroot isn't working, even though I used apt-get to update it. 
[/quote]

Fakeroot is fine, I'm pretty sure. There simply isn't a debian/rules script in the tar.gz file any more.

For the rest, I'm afraid I can't help. I do agree, NDISwrapper can be a pain. But don't blame fakeroot! :) 

Is the version that ships with Dapper not working with your card?

---

### Post by SZF2001 on 2006-06-07
[QUOTE=azz]If it worked fine in breezy, it's probably because ther ewas nothing getting in the way for it to work.  You probably have a device that now has linux support in Dapper.

Find out what device it actually is and see if you can get the native linxu driver to work for you, or find out what kernel module to blacklist.

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)[/QUOTE]
Looking around and finding my USB card,
> 
Linksys
	

WUSB11B Ver.2
	

?
	

Unknown/Likely
	

Yes
	

Yes
	

No command-line needed, works perfect the first try. Tested on Dapper Beta 2
	

2006/05/09
	

USB
That's all I could really find on WUSB11v4. I don't want to do the CVS method unless it's my only option...

---

### Post by az on 2006-06-07
Boot, open a terminal and run this

tail -f /var/log/messages

and then plug in your device for the first time.  Wait a few seconds and then post the output.  That will show what chipset your device is and what the kernel does when you pop it in.

---

### Post by ComplexNumber on 2006-06-07
**SZF2001**
if you have any questions about setting up your wireless card, feel free to ask. i've jsut spend the last 2 days searching high and low throughout this forum, fedora forum, and the rest of the internet for clues as to how to get my belkin wireless card to work. i now have a fully working card, although i really don't dont why for the most part. i was doing everything right along the path, but it seems very temperemental. now it works flawlessly all the time. here is a tip when you're nearly there: in firefox, type in "about:config"(without the quotes) in the address bar. then do a search for "v6". set it to "true". then firefox will be able to resolve IP address to hostnames. if you don't do that, you will find that evn though you can successfully ping anywhere on the net, firefox won't load a webpage if you type in the address as "www.......". it will only work if you type in the IP address such as "216.259...." apaprently, IPv6 isn't very good at this time, so the reason has something to do with that.

also, the ndiswrapper is meant to wrap around windows drivers. i don't know if you know. so don't forget to get windows drivers (ie the inf and sys file), place them in the same directory and type "ndiswrapper -i <drivername>.inf" ont he command line. also, don't forget to put "mosprobe ndiswrapper" in your /etc/rd.d/rd.local file because this command needs to be executed each time you login. other tips: switch OFF the wpa_suppliment and don't have it start at boot. don't install the IPv6 packaages.

---

### Post by escapee from Winhell on 2006-06-09
i too had searched everywhere to get my belkin working b/c this is my 1st go at Linux....however i had breezy for 3 days and up'd to dapper yesterday...i tried several meth's for getting it to work but it never would..but i took the windows files put'm in a folder on desktop used terminal..got to that directory and these three commands (which i'm sure you guys already know) got me here..I'm online now with the usb Belkin f5d7050 wireless now...but here's how i did it...don't know if it'll help or not..as for errors...i haven't a clue..i've seen so many over the past 4/5 days i'm not sure what all they were anymore..but this works9 considering you have the same setup as me...i made sure to run the update manager 3 times after upgrading to dapper

(once in the directory of the folder containg windows driver files)
sudo ndiswrapper -i rt73.inf      (that's the driver i had to use)
sudo modprobe ndiswrapper
sudo if wlan0                               (wasn't sure if i needed sudo for that or not but  
                                                          did it anyway just to make sure)

hope that helps guys..

---

