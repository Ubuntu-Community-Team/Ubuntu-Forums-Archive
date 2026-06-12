---
title: "Install Ubuntu Studio on Mac - no +mac version?"
date: 2012-04-15
forum: Apple Hardware Users
---

### Post by RagnarDa on 2012-04-15
[FONT=Century Gothic][SIZE=3]EDIT: THIS IS HOW YOU GET LATEST UBUNTU STUDIO WORKING ON A MAC / MACBOOK![/SIZE][/FONT]

Installing Linux on a Macintosh is tricky because of two reasons:

1. Mac's don't use the same partitioning table as everyone else. They use GPT instead of MBR and in order to boot OS's other than MacOSX you need to setup a GPT/MBR hybrid partitioning table. If you will only run one OS on your computer then this is not a problem. [rEFIt]("http://refit.sourceforge.net/") will help you with creating a hybrid table aswell as Apple's own BootCamp. Be aware that tools like Parted/GParted might destroy your partition table leaving you with a unbootable system.[URL="http://refit.sourceforge.net/"]
[/URL]
2. Mac's don't have BIOS nor do they have UEFI (the new industry standard) but they instead use EFI and a BIOS-emulation mode. The Ubuntu Studio install DVD supports BIOS and UEFI but, probably because of a bug or something in Mac's EFI implementation, Mac's can't boot it. Regular Ubuntu have a specific Mac version sans UEFI which won't confuse your mac and let it boot in BIOS-emulation mode. Ubuntu Studio don't have this version which is the reason for this thread.

**Install Ubuntu Studio:**
Good things to have before you start:
- The [rEFIt install CD ]("http://downloads.sourceforge.net/refit/rEFIt-0.14.cdr.gz?use_mirror=")
- Atleast one backup distro that you are sure boots on your Mac and includes Parted or GParted in case you screw up (I am using [SystemRescueCD)]("http://www.sysresccd.org/")
- A second computer in case you need to download another distro or something.

Now, download and burn [Xubuntu]("http://xubuntu.org/"). I used the "Alternate CD" 32-bit version so I'm not sure if the "Desktop CD" works. Put the CD in your drive, restart the computer and hold down the "alt" ("option" in mac-lingo) key. Choose the "Windows" CD. Install Xubuntu on your harddisk (probably prefereably the whole drive) and let it install GRUB if it's not already installed and you are planning on using just one OS. Restart the computer and you should now be running Xubuntu. If it doesnt boot, if you are having multiple OS's installed or if you have rEFIt installed you need to update your MBR-table via rEFIt's Partitioning tool. Hold down alt while starting the computer, eject the Xubuntu disc and insert the rEFIt cd, shutdown your mac (by holding the power button pressed for a few sec) and start it up again holding alt. Choose rEFIt and the partition tool and let it do its thing.

Once in Xubuntu, download and install Ubuntu Studio as per [these instructions]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu"). Since you are running Xubuntu you don't have gedit but should instead use leafpad. Read the instructions carefully as it says again and again that you should modify /etc/udev/rules.d/65-permission-raw.rules and /etc/security/limits.conf while it also says that you shouldn't (which in this case is the correct thing to do: don't modify them!).

**Install realtime-kernel**
At the time of this writing there doesnt seem to be any realtime kernel available for Ubuntu 11.10. You need a real time kernel if you are planning on recording music. Therefore I needed to upgrade to 12.04 beta (everything with $ at the start of the line is a command you run in the Terminal):
```
$ update-manager -d
``` I installed the realtime kernel from [here]("https://launchpad.net/%7Eabogani/+archive/realtime"):
```
$ sudo add-apt-repository ppa:abogani/realtime
$ sudo apt-get update
$ sudo apt-get install linux-realtime
```I guess this is an alternative:
```
$ sudo apt-get install linux-lowlatency
```Make sure you check whch kernel you are currently using:
```
$ uname -a
```**Setup Firewire sound**
If you are using a Firewire soundboard like me you need to set the IRQ-priorities that you can read about [here:]("https://help.ubuntu.com/community/FireWire")
```
$ sudo leafpad /etc/default/rtirq
```Change the line that says ```
RTIRQ_NAME_LIST="rtc snd usb i8042"
```into this:```
RTIRQ_NAME_LIST="rtc ohci1394 snd usb i8042"
``` and save it.


**Fix alt - key**
This is how you fix the "alt" - key not working on your non-US Mac ("third level" or AltGr - so you can type the at-sign @ for example) in Xfce / Xubuntu:
```
$ sudo dpkg-reconfigure keyboard-configuration
```Choose your keyboard modell (mine was "MacBook/MacBook Pro (Intl)") and follow the instructions until you get to which key to use for AltGr in which case you choose "Alt, left".


**Set CPU Frequency Scaling**
Lastly you should set CPU Frequency Scaling to "performance" setting:
```
$ sudo apt-get install cpufrequtils sysfsutils
$ gksudo leafpad /etc/init.d/ondemand
```Change the line that reads:
```
echo -n ondemand > $CPUFREQ
```into this:
```
echo -n performance > $CPUFREQ
```and restart your computer. Verify that the setting stuck with this command:
```
$ cpufreq-info
```[B]Install rEFIt boot menu
[/B]You need a partition of HFS+ type (maybe FAT32 will also work). Latest SystemRescueCD has the capability to create this for you in GParted or you can just do it in MacOSX or through the MacOSX install CD and Diskutil. I think a 20 MiB size should be enough but a little more dont hurt. Maybe you kept your "EFI System Partition" and that could probably also work. Make sure to name your partition, for example I named it just "EFI".

Now copy the "efi" - folder from [the rEFIt archive]("http://downloads.sourceforge.net/refit/refit-bin-0.14.tar.gz?use_mirror=") to the root of the partition. Boot your MacOSX install-CD/DVD or MacOSX if you still have it installed, hit the terminal (Utilites-menu and Terminal on the install-CD) and run this command:
```
bless --folder="/Volumes/*[Name of your EFI partition]*/efi/refit" --file="/Volumes/*[Name of your EFI partition]*/efi/refit/refit.efi" --labelfile="/Volumes/*[Name of you EFI partition]*/efi/refit/refit.vollabel" --setBoot
```Make sure to substitute *[Name of your partition]* with the actual name of your EFI-partition. It might give you errors but just ignore them, seems to work anyway. This command tells the Mac-firmware to boot the rEFIt application when you start the computer. There are Linux - implementations of the "bless"-command but i couldnt make them work. Would be really nice if someone would tell me how to so you could take MacOSX completely out of the picture.


Hope this helps anyone since it took me forever to get this to work!



Original post:

> I'm having trouble installing Ubuntu Studio on my MacBook 2.1. The same problem arises when trying to install regular amd64 iso on regular Ubuntu. Regular Ubuntu has a "+mac" version though that works for me. It's explained here:[http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image](http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image)
Is there a similar version for Ubuntu Studio or can I build one?

---

### Post by Bucky Ball on 2012-04-15
Which release are you attempting to install? Is Ubuntu running okay from the disk when you 'Try Ubuntu'?

---

### Post by RagnarDa on 2012-04-15
Trying with version 11.10 amd64. Should I try 32-bit or older release?

I'm running Ubuntu (only) on the machine so there's no 'Try Ubuntu' option. When I insert the disc it asks me if I want to upgrade to the one on the disc. Would that install a complete Ubuntu Studio system? Because I want to run regular Ubuntu and Ubuntu Studio side-by-side could I just install another regular Ubuntu on a new partition and 'upgrade' it to Ubuntu Studio?

Edit: I'm having trouble with xruns and high latency on my FireWire - sound card when running Ubuntu so the switch to Ubuntu Studio is solely to try if that works better. So I need US's optimization features and lighter system load.

---

### Post by Bucky Ball on 2012-04-15
You could just install ubuntustudio-desktop and that will put you there. You are looking for the RT kernel (realtime kernel) for latency. 

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")

But yes, if you have 11.10 already installed you could install studio on another partition and dual-boot ...

---

### Post by RagnarDa on 2012-04-15
Ok. This is what I did:

Installed xubuntu 11.10 32bit "alternative" install (which works on Mac) on a new partition next to regular Ubuntu.
The installation unforfunately screwed up the MBR and created the "no bootable device"- error. I solved this by burning a rEFIt disc and booting it, then syncing the MBR in the rEFIt partition tool.

Followed all the instructions in the above link, except I couldn't get the real time or low latency kernel anywhere. They mention [here]("http://ubuntustudio.org/Oneiric+Ocelot") that newest US ships with the -generic kernel instead, in which you can set the IRQ priorities - but how? Do I need to build my own kernel or what?

When I try recording, I get a little less xrun's now but still way to many. I have used this setup with both MacOSX and Windows XP so I know it *should* work and the comp can handle it. I'm guessing the missing real time kernel is the key here...

Any help?

---

### Post by RagnarDa on 2012-04-16
I'm still struggling with this but here's how far I am currently:

Figured out that there was no real time kernels for 11.10 so I upgraded to 12.04 beta. Now I could install the real time kernel from [here]("https://launchpad.net/~abogani/+archive/realtime") and after [setting IRQ prioirities]("https://help.ubuntu.com/community/FireWire") I had no xrun's!

Problem was, the grub bootloader seemed to be installed on the first partition (Im guessing some kind of GPT/MBR hybrid since we are on a Mac) where I couldn't touch it. I had to manually change the menu-entry on every boot to be able to run the real time kernel. I tried to fix this by booting into SystemRescueCD and changing the boot flag in GParted to my Ubuntu Studio partition but this gave me a unbootable system :(

I'm currently reinstalling the whole thing from the beginning but meanwhile I am wondering about these two things I noticed the few minutes I was able to record xrun-free:

1. When I lowered the buffering settings in Qjackctl so I had a latency of 5,8msec and turned on software-monitoring in Ardour, the sound became heavily distorted and the volume started go up and down? I'm guessing that I have pushed my comp to the limit but there was no xrun's?

2. It seems very unstable. I was able to work with it approx two minutes before the sound card disconnected and Ardour crashed. I am not able to connect to the device at every try either. Really have to shutdown the comp and disconnect everything before trying again. What's wrong?

---

### Post by RagnarDa on 2012-04-18
Ok got it working good now.:guitar:

I think the distortion issue might have been a glitching guitar cable. I am able to record 24bit/96Khz at 8 channels which is the max of my Firepod (FP10) soundboard. MIDI is also working. Still having issues with the JACK and my Firepod but it's not a showstopper. I will write instructions how to get Ubuntu Studio working on a mac in the first post of this thread.

---

### Post by Bucky Ball on 2012-04-18
Nice work, mate! Please mark as 'Solved' and that will hopefully help others. ;)

---

### Post by millerthegorilla on 2012-12-30
Can anyone tell me how to burn rEFIt under linux?  I tried converting it from .dmg to img and then mounting it and then burning the files as an iso but the mac pro that I have doesn't recognise it.

I am trying to install rEFIt and also reinstall/upgrade the firmware as I have not got any boot up screen.  If you know how to get the firmware cd to boot I'd be grateful.  Of course first I have to burn it from the dmg file but on the firmware download page it states that I have to keep the power button pressed down and I will get three short flashes or tones and then 3 long f/t followed by 3 short (or poss the other way round).

Instead I get a series of very short flashes, perhaps about ten and then one long tone.

Many thanks

James

ps I know this thread is solved but so many people on the net are having problems burning dmg files from linux that it would be good to put the answer here as well.

---

### Post by millerthegorilla on 2013-01-22
I found a way of burning the dmg file.  Install acetoneiso using apt.  Then select 'image conversion' menu and the 'convert mac image'.  You will have to say yes to the download of poweriso.  Choose to save to a folder and then convert to an iso and burn to disk.

When you install the x86 ubuntu studio on the mac - does it install as 64 bit?

---

