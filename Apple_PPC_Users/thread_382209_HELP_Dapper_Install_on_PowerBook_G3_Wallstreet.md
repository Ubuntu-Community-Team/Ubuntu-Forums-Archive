---
title: "*HELP* Dapper Install on PowerBook G3 Wallstreet"
date: 2007-03-11
forum: Apple PPC Users
---

### Post by Macmania on 2007-03-11
Ok, I am very new to linux. I wanted to breathe new life into my G3 Powerbook which was running OS 9.2.2 and OS X 10.04 Cheetah no not 10.4 Tiger like my eMac, 10.04 which is like a pc that is still running Windows 98. So I decided to install Ubuntu since Apple only supports OS X up to 10.2 Jaguar. What I have is a PowerBook G3 300 "Wallstreet", 8gb harddrive, 320mb ram, Ati rage graphics, etc. I finally got BootX working and was able to start up the installer. It seems to go along fine untill I get to the partitioner. I set it up to use the largest continuous space and it proceeds seemingly fine. It sets up Linux as HDA9, Swap as HDA10 and OS 9 is HDA8. I tell it yes to apply changes and it says something along the lines of writing changes to disk. Now here is my problem, it goes to a blank blue screen for a few minutes and then a box pops up saying starting up partitioner and it goes back to the partitioner menu. I was like what the hell?? So I press on. I make sure the partitions are still set up like they were before and they are, I select apply changes and same thing again. Blue screen then the partitioner starts up again. So this time I just select apply changes without checking things and same deal. Now when the partition menu comes up I select go back which takes me to the install menu and I select the next option which is set time zone. When I select it the partitioner starts up again. I select go back and select another option on the install menu and same deal. No matter what I select the partitioner starts up again. Why could this be? Am I doing something wrong? I was about to throw the computer out the window yesterday and if it was not in near mint condition I probably would have. Also it does not recognize my pcmcia wireless card or my ethernet port. It asks if I intend to use firewire ethernet but don't have firewire. Any ideas? The wireless card I have is a Linksys WPC11 version 4. Any help would be awesome. Thanks

---

### Post by x64Jimbo on 2007-03-11
Any particular reason you're not using the current release Edgy?

---

### Post by Macmania on 2007-03-12
The computer is kinda old, and I didn't want to bog it down too much. When I upgrade the processor to a G4, bigger hard drive and 512mb ram I may try Edgy. I also installed Dapper on a PC before and liked it.

---

### Post by x64Jimbo on 2007-03-12
Unlike Windows, upgrading to Edgy from Dapper will not tax your system any more. It does not change the memory footprint or the hard disk usage by very much at all. However, Edgy is leaps and bounds better than Dapper in many ways, including WiFi support.

---

### Post by Macmania on 2007-03-12
Really? Thats good to know. I might download Edgy. I am having problems installing Dapper anyway. Is Edgy easier to install than Dapper? The Dapper install is driving me crazy.

---

### Post by x64Jimbo on 2007-03-12
Seriously, Edgy is at least twice as easy to work with in general, especially since that's where all the current development and how-to's are targeted.

---

### Post by Macmania on 2007-03-12
I am downloading Edgy as we speak. I see it has an advanced partitioner. Thats good because the one in Dapper refuses to work properly and I have seen that several other people have the same problem on Intel, Power PC and even AMD machines.

---

### Post by x64Jimbo on 2007-03-12
Seeing as you'll be installing it on a laptop, I recommend upgrading to NetworkManager (from the default network interface software) right off the bat.

---

### Post by Macmania on 2007-03-12
Network Manager? Is that just a download or do I need to buy it? My Linksys card did not work in Mac OS X so if it gets it working, that would be cool. That's why I got this laptop, I wanted something portable. I hope Edgy breathes some new life into this computer because it was like using Windows 95 or 98 on a pc, totally out of date and unsupported.

---

### Post by x64Jimbo on 2007-03-12
NetworkManager is free, just like (nearly) all the software in Linux. I say nearly because there are only a handful of commercial products for Linux. 99.5% of the apps you'll need are free though, and NM is one of those. It just helps you automate your network connection process. It manages all your network cards at once, selecting the best connection for you to use. It can be used to manage your Ethernet connections, wireless connections, your wireless encryption keys, your VPN connections, and more. It's really an all-in-one solution. About the only thing it doesn't do is your dishes.

---

### Post by Macmania on 2007-03-12
Cool, I think I will give it a try after I get Edgy installed. Do you know where can I download it from?

---

### Post by Tommy on 2007-03-14
> **Macmania said:**
> Cool, I think I will give it a try after I get Edgy installed. Do you know where can I download it from?

I believe the Network Manager is available in the Ubuntu repositories along with everything else. It's really just the "new technology" that all Ubuntu versions will be using in the future. Great for laptops (if your hardware is recognized).

For now, let us know whether Edgy will boot and partition your machine.

I have a PowerBook G3 Series "Wallstreet II / PDQ" 266 Mhz, currently running Dapper, HOWEVER I have upgraded it all the way from Warty (a few versions back). 

The sad news is some of the recent stock kernels and installers don't always work on oldworld Macs (those that require BootX), at least not without some fiddling. Ubuntu doesn't "officially" support oldworld at all so you have to work around some things, like copying the kernels to the OS 9 partition when they're updated. I know a few of the installer and kernel versions just didn't get along with my Wallstreet, but the upgrades have been OK.

It was a hassle upgrading from 5.10 to 6.06 (Dapper) so I hope you can get Edgy to boot and partition. I have a PowerMac 9600 (G3 300 Mhz) I have wanted to install Edgy onto, but I haven't found the magic incantations yet.

On the plus side, I've been VERY happy with Ubuntu on my PowerBook. It's great having such an old machine run the latest stuff.

P.S.: I'm adding a note here -- I believe I got the PowerMac 9600 to boot from the Edgy live CD (the ordinary desktop disk), but I had trouble with the installer -- on that attempt, the installer failed trying to detect the CD-ROM. It takes some effort to get BootX to boot to the live CD (you have to pick out the command from the yaboot menu file)... BUT since you made it to a later stage in the installer, maybe you can get it going on yours with one of the other kernels. I downloaded all three varieties of disks -- the server, the alternate and the Desktop, and could not install from any of them. But that machine has been a pain all the way around...

All this is speculation, though... and since I'm using my Wallstreet for my daily work I don't want to break it to test Edgy (or even Feisty) just yet. Let me know how you fare.

---

### Post by Macmania on 2007-03-15
> Let me know how you fare.
Well this is where I am at so far....
[http://ubuntuforums.org/showthread.php?t=384205]("http://ubuntuforums.org/showthread.php?t=384205")

---

