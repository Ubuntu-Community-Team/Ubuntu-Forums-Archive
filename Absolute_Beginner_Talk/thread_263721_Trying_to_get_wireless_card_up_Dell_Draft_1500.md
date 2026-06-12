---
title: "Trying to get wireless card up: Dell Draft 1500"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by EmmDoubleEw on 2006-09-23
I'm trying to get my wireless card working, here are the steps I have taken:


My card is supported under ndiswrapper:
Card: Dell Wireless 1500 (802.11draft-n/a/g) WLAN MiniCard 
Chipset: Broadcom BCM4321(?) (rev 01) 
pciid: 14e4:4328 
Driver: [http://ftp.us.dell.com/network/R129083.EXE](http://ftp.us.dell.com/network/R129083.EXE) 
Other: ndiswrapper v1.22-rc1, Ubuntu kernel 2.6.15-26-386

My ndiswrapper version is:

```
martin@martin-laptop:~$ ndiswrapper -v
utils version: 1.7
driver version:        1.8

```

I tried following this tutorial:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-d270600ddc317f671085f088b8eb4b1604d51a91](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-d270600ddc317f671085f088b8eb4b1604d51a91)

But my card doesn't show up under lshw, so none of the tutorial makes sense. For example, it tells me to "add information that should look like this:
```
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)
  bind "ath_pci"
  
```

What?? Do they expect me to know off the top of my head what manfid, function, whatever whatever is for my card? I'm utterly confused.

I tried installing the .inf file with ndiswrapper, and it shows up in the driverlist:


But that has made absolutely no difference: I still can't connect without a cable and it still doesn't show up under "Network Settings."

Help would be greatly appreciated.

---

### Post by RobsterUK on 2006-09-23
Forgive me if this is a stupid question but have you tried rebooting?

I recently installed a wireless network adapter with ndiswrapper, and at first it didnt work, then i thought "hang on this is a windows driver" and reboot did the trick.

As you have directed ndiswrapper to the relevant inf file then the driver should be installed.

good luck

---

### Post by EmmDoubleEw on 2006-09-24
That's not a stupid question, but the answer is yes. As a matter of fact I've been following tutorials left and right to change this and that and not a single one has worked so far. I'm starting to wonder what's wrong.

---

### Post by got_nix on 2006-09-24
i'm assuming that all the tutorials are using ndiswrapper but different routes/methods to arrive at the same end right. did you completely remove the ndiswrapper package and the modprobe and the drivers after each attempt to try the next method? it may kinda weird but it worked for me when i first messed with ndiswrapper.

---

### Post by atenlaugh on 2006-10-30
This card works perfectly for me now. The thing that made it work for me was installing the latest version, found here: 
[http://sourceforge.net/projects/ndiswrapper/]("http://sourceforge.net/projects/ndiswrapper/")

This method does involve compiling, however, which you may or may not have done before. Here are installation/running directions: [Ndiswrapper installation and use]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation"). Following this carefully should do it for you. 

I also used the official dell driver from their website (using unzip to extract, then getting the files from the DRIVER folder), but I didn't test if this actually made any difference. Your milage may vary, of course.

---

