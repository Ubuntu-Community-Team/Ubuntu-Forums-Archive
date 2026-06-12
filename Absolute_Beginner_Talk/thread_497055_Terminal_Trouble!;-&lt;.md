---
title: "Terminal Trouble!;-&lt;"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by t99 on 2007-07-09
Hello all!
A few days ago I dove in head first and deleted windows and installed Ubuntu!Yaay!
However im having some teething problems.
Im trying to extract ndiswrapper to install it for my Broadcom Wireless Card(4311) but havnt got very far because im confused about the syntax in the terminal.
Ndiswrapper is in my home directory
So far iv used 
countless variations of the extract commands iv seen on this forum and on the web
but it always returns an error like

tar : ndiswrapper.1.47.tar.gz : Cannot open : no such file or directory
tar : Error is not recoverable: exiting now
tar : Child returned status 2
tar: Error exit delayed from previous errors

!!Help would be much appreciated!!

Im on a Hp Compaq Presario f500.
Also having mad problems with my  mouse which seems to cut and paste on its own and act very erratically!

Thanks

---

### Post by KIAaze on 2007-07-09
[LIST]
[*]_For the tar problem:_
Have you tried extracting by "right-click/extract here"? ^^'
That usually works and adapts to the file format.

Now for the tar options:
> 
-x, --extract, --get
	      extract files from an archive

 -z, --gzip, --gunzip, --ungzip
	      filter the archive through gzip

 -j, --bzip2
	      filter  archive  through	bzip2,	use  to decompress .bz2 files.
	      WARNING: some previous versions of tar used option -I to	filter
	      through  bzip2.  When writing scripts, use --bzip2 instead of -j
	      so that both older and newer tar versions will work.

 -v, --verbose
	      verbosely list files processed

 -f, --file [HOSTNAME:]F
	      use archive file or device F (default "-", meaning stdin/stdout)


cf ```
man tar
``` for more info.

The "-f" option is essential, otherwise it won't work.
The "-v" option is optional. It will list the files as they are being extracted giving you an idea of the extraction process.
The "-x" is for extracting. ("-c" for compress)
The "-z" if it's a tar.gz.
The "-j" if it's a tar.bz2.

So generally:
```
tar -xzvf package.tar.gz
tar -xjvf package.tar.bz2

```

In your case:
```
tar -xzvf ndiswrapper.1.47.tar.gz
```
**But first make sure, you are in the directory where the tar.gz is!!!**
To change directories use the "cd" command:
"cd ~/Desktop" for example to go to the desktop. "~" means home (/home/<login>).


[*]_Now for the mouse problem:_
The default behaviour (and I don't know how to change it or even if it can be changed) is that "middle-click" pastes the last text you selected.
This is quite practical (personal opinion), but takes some getting used too.


[*]_How to install after successful extraction of the archive:_
```

cd ndiswrapper.1.47
./configure
make
sudo make install

```
[/LIST]

---

### Post by t99 on 2007-07-09
Well i did get it extracted before by right-clicking etc
I was trying to follow the instructions on the install
So to install it in the terminal now ,do i  have to switch to the directory its in?

As for the mouse thing,Ubuntu must think my touchpad is the middle button because any time i tap it,it pastes!Cant find an option to change it though?
Thanks

---

### Post by KIAaze on 2007-07-09
Yes, just switch to the extracted directory using the "cd" command and then run the configure/make/make install process.

For the paste problem, there must be some configuration panel for the touchpad somewhere in the menus. If not, try "right-click->edit menus" on the top taskbar and look if you can add it among the system/preferences shortcuts.
I'm not on my laptop right now and don't have any experience with that since I always use a mouse.

---

### Post by t99 on 2007-07-09
cant seem to get the ./configure command to work!
Its ssays theres no such file or directory?

---

### Post by RomeReactor on 2007-07-09
Hi. I think you need to install **build-essential** first, if you haven't done so already; look for it in Synaptic, or from the terminal:
```
sudo apt-get install build-essential
```
Also, make sure you *are* inside the ndiswrapper directory. Type
```
ls
```
to make sure the configure file is indeed there. By the way, is there a particular reason you need to compile ndiswrapper? you can install it through Synaptic, if you can connect to your modem/router with a LAN cable.

---

### Post by t99 on 2007-07-09
I got build essential but terminal stilll doesnt recognise the command,do i need to restart?

---

### Post by t99 on 2007-07-09
Ah jesus i didnt even think of that!Its installed now and i realised that iv wasted hours trying that!Well at least i learnt a thing or two!
Thanks for the help and the patientce putting up with a complete newbie!

---

### Post by t99 on 2007-07-09
Back again unfortunately! 

Im using this guide for
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

but when i get to this part

sudo apt-get install ndiswrapper-utils-1.9 cabextract

it says



Couldn't find package ndiswrapper-utils-1.9

Is it the wrong utility for feisty?Should it be something else?

---

### Post by KIAaze on 2007-07-09
Probably a repository problem.

You can add extra repositories using the Software Sources application, which can be found in the menu: System -> Administration -> Software Sources. Check the repositories you think you will need (main, universe, restricted, multiverse). You probably won't need the 'sources' repository. This is the recommended way to add extra repositories.

I would suggest selecting all.
After that retry the command:
```
sudo apt-get install ndiswrapper-utils-1.9 cabextract
```

[See here for more info about adding repositories.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

If that doesn't work, just download the package here:
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9]("http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9")

The download links are at the bottom. You'll have to choose the one for your architecture (intel processors usually mean i386. i386 is the most common anyway, so unless you know you have amd64, choose i386.).

To install the package after downloading, just double-click it and follow the instructions.

---

### Post by Hollywood on 2007-07-10
> **t99 said:**
> Ah jesus i didnt even think of that!Its installed now and i realised that iv wasted hours trying that!Well at least i learnt a thing or two!
Thanks for the help and the patientce putting up with a complete newbie!

What didn't you think of? I am having the exact problem at the moment and was following along. I, too, just installed build essential, but am having the same problem. What did you do after that? And did you get ndiswrapper installed?

---

### Post by RomeReactor on 2007-07-10
Hi **Hollywood**; did you try installing ndiswrapper through Synaptic?

---

### Post by Hollywood on 2007-07-10
> **RomeReactor said:**
> Hi **Hollywood**; did you try installing ndiswrapper through Synaptic?

Yes, it's not on there. I currently have no internet connection due to driver issues which is why I'm "dowloading" it. Yesterday or the day before, I found it and it told me to put in my live cd, which I did. It then said I'd need an internet connection, which I don't, but went ahead anyway and managed to get half the download. So today I started fresh and downloaded ndiswrapper to the computer I'm using now, then burnt it to cd and am trying to install it that way. I've right-clicked and extracted the files that way, but keep getting error messages when I try to install.
Do you have any suggestions for me? I would virtually wash your virtual car for a month for some help!

---

### Post by RomeReactor on 2007-07-10
What are the errors that come up? Also, an easy way to work around this is (if possible) to connect your Ubuntu system to the modem/router through a LAN cable. If that is not an option, then we'll need to keep going with the downloaded packages; what Version of Ubuntu do you have (Feisty, Edgy, Dapper) and for what architecture (i386, AMD64)?

---

### Post by Hollywood on 2007-07-10
First, yeah, no direct connect is possible. damn
As far as errors, it depends what I'm entering, and to be honest, I have no idea if I'm doing this right. I've just been trying what I've been seeing on the forums for days. In a search to find why I was getting [B]exit status 2[B] I found this thread, whose situation sounded similar. So as far as the tar commands tried in this thread, I get:
for tar -xzvf ndiswrapper-1.47.tar.gz
tar: ndiswrapper-1.47.tar.gz: Cannot open: no such file or directory
tar : Error is not recoverable: exiting now
tar : Child returned status 2
tar: Error exit delayed from previous errors

for dpkg --install ndiswrapper-1.47.tar.gz
dpkg: error processing ndiswrapper-1.47.tar.gz (--install)
cannot access archive: no such file or directory
Errors were encountered while processing ndiswrapper-1.47.tar.gz

And when I tried apt-cdrom add 
it says that it was unable to locate any package files, perhaps this is not a Debian disk

Sorry for the response delay, I can't save off openoffice which is how I was transferring my copy and pastes to this computer.

BTW I have Feisty installed

---

### Post by RomeReactor on 2007-07-10
OK, here's an alternative that I think will be better: you need to download two packages in your windows system: [ndiswrapper-common]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb") and [ndiswrapper-utils-1.9]("http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb"). Once you have both, transfer them to Ubuntu using a USB drive (even a floppy will do, the combined size of the packages is 49 Kb). When you have them in your Ubuntu system, double-click on **ndiswrapper-common** first; that will bring up Gdebi, an application to install .DEB files. Next, do the same for **ndiswrapper-utils-1.9**.

---

### Post by Hollywood on 2007-07-10
I'm going to try downloading those again. I tried to open the first one like you said but it says that it can not open because the file may be corrupt or I don't have permission, and I can't make changes to the permissions of the file because they auto-revert back to original settings.

---

### Post by Hollywood on 2007-07-10
Okay, installation was successful! Now what?:)

---

### Post by RomeReactor on 2007-07-10
Do you have the drivers for your wireless card? if not, and/or you don't know which one you have, enter this in the terminal:
```
sudo lshw -class network
```

EDIT: From here on it's where it gets *really* interesting! I suggest you take notes of what you're about to do, and save them for future reference.

---

### Post by Hollywood on 2007-07-10
My driver shows up as RT2500USBSTA
I actually tried installing a driver from Ralink directly but was having major problems which is why I said to heck with it and tried installing ndis like the rest of the noobs.

---

### Post by RomeReactor on 2007-07-10
You're going to need a XXXXX.INF file and a XXXXX.SYS. If you have both, move them to your home folder (putting the files there makes it easier to use the terminal since you don't have to navigate elsewhere; the terminal opens up right there), and enter this:
```
sudo ndiswrapper -i FILENAME.INF
```
substitute FILENAME.INF for the actual name of your file.

---

### Post by Hollywood on 2007-07-10
Do I enter the X's as X's or am I supposed to substitute something in there?
Do I make these files or are they somewhere already?

---

### Post by RomeReactor on 2007-07-10
If you have the installation CD for your wireless card (which seems to be a USB device) load the CD  in Ubuntu and search it for drivers (one XXXXX.INF and one XXXXX.SYS); I used XXXXX as a sort of wildcard, it's not the name of the driver. We can also find the drivers knowing what chipset your wireless device uses:
```
lsusb
```
you can also try:
```
sudo lshw -class network
```
post the results of both commands to make sure what we're dealing with.

**EDIT**: Or if you know where those drivers are in your windows system, copy them over to your Ubuntu home folder.

---

### Post by Hollywood on 2007-07-10
Again, had to write out by hand and type here so sorry about delay
sudo lshw -class network
* -network
Description: wireless interface
physical id: 1
bus info: firewire@4
logical name: rausb1
serial: 00:13:46:74:76:51
capabilities: ethernet physical wireless
configuration: broadcast=yes driver= RT2500USBSTA driverversion 1.0.0 BETA 2
ip=192.168.0.101 link =yes multicast=yes wireless= RT2500USB WLAN

sudo lsusb
BUS 004 Device 004: ID 2001: 3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
BUS 004 Device 001: ID 0000:0000
BUS 003 Device 001: ID 0000:0000
BUS 002 Device 002: ID 043d:0079 Lexmark International Inc.
BUS 002 Device 001: ID 0000:0000
BUS 001 Device 002: ID 045e:00db Microsoft Corp.
BUS 001 Device 001: ID 0000:0000

---

### Post by RomeReactor on 2007-07-10
This seems odd:
```
* -network
Description: wireless interface
physical id: 1
bus info: firewire@4
logical name: rausb1
serial: 00:13:46:74:76:51
capabilities: ethernet physical wireless
[B]configuration: broadcast=yes driver= RT2500USBSTA driverversion 1.0.0 BETA 2
ip=192.168.0.101 link =yes multicast=yes wireless= RT2500USB WLAN[/B]
```

It seems it already has a driver. Try this from the terminal:
```
ndiswrapper -l
```

---

### Post by Hollywood on 2007-07-10
It goes straight to my command line prompt again, no info.

---

### Post by RomeReactor on 2007-07-10
Well, that was odd. In any case, have you found the drivers in your windows system, or the Installation CD of your wireless USB? Remember, you must find a **.INF** and a **.SYS** file. We can't go further without them. Try searching for files named **rtXXXXusb.sys** and **rtXXXXusb.inf** in your **C:\Windows\System32** folder. They may be **rt2500usb** or **rt2750usb**, I'm not sure.

---

### Post by Hollywood on 2007-07-10
I am still looking for my install CD. Could I possibly ask you to check back tomorrow sometime? I should have it by then and you've been so patient and helpful that I would love for you to continue to assist me if that's possible? I really appreciate what you've done for me so far! I will get back to looking for the disc now. Have a great night/morning and thanks again!
BTW I don't have Windows partioned, I did the full ubuntu because Windows was ruined.

---

### Post by RomeReactor on 2007-07-10
OK, no problem. I've searched for information about your wireless usb, and it seems it's a tricky one to configure; you may need [SerialMonkey]("http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz") drivers to get it working. Here's the [Ubuntu Community Documentation]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29") page describing how to go about it, though the page seems outdated and looks like you'll need a few packages installed as well ([coreutils]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fc%2Fcoreutils%2Fcoreutils_5.97-5.2ubuntu3_i386.deb&md5sum=1d0bc911442c6238c3a6951300847752&arch=i386&type=main"), [linux-headers-2.6.20-16]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-16_2.6.20-16.29_i386.deb&md5sum=5d253be23169cd73d23387413610f95a&arch=i386&type=security"), [linux-headers-2.6.20-16-generic]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-16-generic_2.6.20-16.29_i386.deb&md5sum=d8801e237c379ea0a144a0c801369323&arch=i386&type=security"), and [linux-headers-generic]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-meta%2Flinux-headers-generic_2.6.20.16.28.1_i386.deb&md5sum=49a011da0fc7b3a07ba56f8f0348c4ca&arch=i386&type=security")).

---

### Post by Hollywood on 2007-07-10
Alright, I've found my driver install disc. I'm going to try following your earlier suggestion about loading it to ubuntu and looking for the .inf and .sys files. If I can't (and it sounds like I won't) I'll try the slightly outdated community documentation and cross my fingers. I'll let you know!

---

### Post by Hollywood on 2007-07-10
> **RomeReactor said:**
> You're going to need a XXXXX.INF file and a XXXXX.SYS. If you have both, move them to your home folder (putting the files there makes it easier to use the terminal since you don't have to navigate elsewhere; the terminal opens up right there), and enter this:
```
sudo ndiswrapper -i FILENAME.INF
```
substitute FILENAME.INF for the actual name of your file.

Okay, I put all the driver files from my install disk into my home folder. I had 4 files total, one .inf.
entered sudo ndiswrapper -i NetRTUSB.inf and it installed no problem
I have 2 .sys files so I entered them both in this order:
sudo ndiswrapper -i rt2500usb.sys
sudo ndiswrapper -i RT25U98.SYS

Both of those said couldn't find source file, installation *may* be incomplete, so I did
sudo ndiswrapper -i NetRTUSB.cat 
for good measure because it was the only remaining file in the driver folder so I figured there might be info in there that was required first before the others could be installed properly. I then retried 
sudo ndiswrapper -i rt2500usb.sys again to see if it would be any better, but it said that it was already installed so I'm assuming it is complete.

Do I still have to go through with the outdated community doc info because I'm having a little trouble with that, as in no luck. OR can I continue down our original path since I now have those files?

---

### Post by bobplano on 2007-07-10
those .sys files should be copied to /etc/ndiswrapper/*nameofdevice*

---

### Post by RomeReactor on 2007-07-10
Hi again. To install the drivers, preferably those for winXP, ndiswrapper uses **only** the **.inf** file; it also copies the **.sys** files to **/etc/ndiswrapper/DRIVER_NAME**, which in your case would probably be **/etc/ndiswrapper/NetRTUSB**. If I'm not mistaken, the driver that should be installed is **rt2500usb.sys**.

You already did the first step:
```
sudo ndiswrapper -i FILENAME.INF
```

To continue, note that **no errors** must show up after entering the following commands; if they do show up, something must be changed before proceeding furhter. Now, the next step is to:
```
ndiswrapper -l
```
to check that the drivers installed correctly (has to show: Installed ndis drivers: DRIVER_NAME driver present, hardware present); next:

```
sudo depmod -a
```
(depmod  creates  a  list of module dependencies); then:

```
gksudo gedit /etc/network/interfaces
```
to edit the configuration; now, according to your [other post]("http://ubuntuforums.org/showthread.php?p=2992372#post2992372") in Networking & Wireless, your **interfaces** file should have a section like this:
```
auto rausb1
iface rausb1 inet dhcp
wireless-essid Alchemy
```
Add it if it's not here; or close Gedit and use **iwconfig** to configure your device. I suggest you disable encryption in your router if it's on, at least while you get the wireless USB going. Next step:

```
sudo ndiswrapper -m
```
(this loads ndiswrapper automatically when the wlan0 interface is used). Now:

```
gksudo gedit /etc/modules
```
and write **ndiswrapper** at the end of the file (to load ndiswrapper automatically at boot time);

```
sudo iwconfig rausb1 mode Auto
```
and that's it; reboot. If wireless doesn't start along with the system:
```
sudo dhclient rausb1
```
should get your wireless working.

--------------ADDITIONAL STEPS (OPTIONAL)---------------

 This next step is up to you to do or not; I found my wireless card won't correctly work without disabling ACPI. You may want to skip this step and perhaps try it if, at the end, your device doesn't work properly:
```
gksudo gedit /boot/grub/menu.lst
```
and add **acpi=off** between **### BEGIN AUTOMAGIC KERNELS LIST** and **## DO NOT UNCOMMENT THEM, Just edit them to your needs**.

For some people, their internet connection will be slow if they don't disable IPV6:
```
gksudo gedit /etc/modprobe.d/aliases
```
search for **alias net-pf-10 ipv6** and change it to **alias net-pf-10 off**.

---

### Post by Hollywood on 2007-07-10
First off, here is what I get for ndis.. -l
netrtusb : driver installed 
        device (2001:3C00) present (alternate driver: rt2570) 
rt2500usb.sys : invalid driver! 
rt25u98.sys : invalid driver! 

According to other outputs, I also thought I needed rt2500, but it won't go. Should I remove it and try it again? I'm assuming that invalid drivers are considered errors, but can I remove those invalid drivers and just keep the installed one or do I really need the rt2500 for it to work? Those two .sys file were the only ones on the install disk.

---

### Post by Hollywood on 2007-07-11
Okay, I've made it towards the bottom of your list. Everything was going fine until:

Code:
sudo iwconfig rausb1 mode Auto

I keep getting Error for wireless request "Set Mode" (8806):
   SET failed on device rausb1 ; Invalid argument

The first time this happened, I did the lshw -c network and found that my rausb1 was now rausb0. I adjusted the command line accordingly but still had the same error message. I restarted my computer and did lshw... again and found it back to rausb1 again. I checked my interfaces and modules to make sure they were still correct and they were, so I tried
sudo iwconfig rausb1 mode Auto

again, but keep getting the same message.  I'll keep at it and let you know

sudo dhclient rausb1
gets me:
No DHCPOFFERS Received
No networking leases in persistent database - sleeping

---

### Post by Hollywood on 2007-07-11
Okay I also tried
gksudo gedit /boot/grub/menu.lst
but the page was blank, when I exited back to the terminal it said:
(gedit: 5411): GnomeUI - WARNING **:While connecting to session manager:
Authentification Rejected, reason: None of the authentification protocols specified are supported and host-based authentification failed.

I did disable the IPV6, though. Still no connection.

---

### Post by KIAaze on 2007-07-11
It's strange that you have problems editing /boot/grub/menu.lst with gedit. Do you dual-boot or do you only have Ubuntu on your PC?

Try:
```
sudo nano /boot/grub/menu.lst
```
"nano" is a console based text editor which is probably already installed on your system.
Editing is straightforward and the available commands are displayed at the bottom.
"^" means "ctrl". So "ctrl+O" for example will "write out"="save as...".

And just to make sure it's a permission problem and not something else, you can open the menu.lst file as read-only in gedit by doing:
```
gedit /boot/grub/menu.lst
```

---

### Post by Hollywood on 2007-07-11
> **KIAaze said:**
> It's strange that you have problems editing /boot/grub/menu.lst with gedit. Do you dual-boot or do you only have Ubuntu on your PC?

Try:
```
sudo nano /boot/grub/menu.lst
```
"nano" is a console based text editor which is probably already installed on your system.
Editing is straightforward and the available commands are displayed at the bottom.
"^" means "ctrl". So "ctrl+O" for example will "write out"="save as...".

And just to make sure it's a permission problem and not something else, you can open the menu.lst file as read-only in gedit by doing:
```
gedit /boot/grub/menu.lst
```

I tried both and again the screens were blank, no writing.

---

### Post by KIAaze on 2007-07-11
Do you have only Ubuntu on your PC?
If so, it's possible that Grub isn't even installed in which case there is also no menu.lst file.

Check if the file /boot/grub/menu.lst exists:
```
ls /boot/grub/menu.lst
```

You can eventually install Grub through synaptic if it isn't installed.

---

### Post by Hollywood on 2007-07-11
Sorry about the delay but these pages started timing out and I could open them until now.
Yes, I only have ubuntu.
When I start up, before the ubuntu screen comes on, there is something about grub doing something, so I assume it's on there. But I'll double check now..

No such file or directory

I'm going to see if I can download that from synaptic

According to Synaptic, I have the most current version installed

---

### Post by RomeReactor on 2007-07-11
> **Hollywood said:**
> First off, here is what I get for ndis.. -l
netrtusb : driver installed 
        device (2001:3C00) present (alternate driver: rt2570) 
rt2500usb.sys : invalid driver! 
rt25u98.sys : invalid driver!

Looks like you'll have to blacklist those conflicting drivers:
```
gksudo gedit /etc/modprobe.d/blacklist
```
add at the end of the file:
```
blacklist RT2500USBSTA
blacklist rt2500usb
blacklist rt25u98
```
reboot, and then try **ndiswrapper -l**.

---

### Post by KIAaze on 2007-07-11
For the Grub issue (I know nothing about ndiswraper ^^):

Run:
```
sudo update-grub
```

It should generate the menu.lst file.

After that, it should be easy to edit.
A menu entry with ACPI=off looks like this for example:
> title		Debian GNU/Linux, kernel 2.6.18-3-amd64
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro acpi=off noapic
initrd		/boot/initrd.img-2.6.18-3-amd64
savedefault


See [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto") for detailed info about menu.lst.

---

### Post by Hollywood on 2007-07-11
> **RomeReactor said:**
> Looks like you'll have to blacklist those conflicting drivers:
```
gksudo gedit /etc/modprobe.d/blacklist
```
add at the end of the file:
```
blacklist RT2500USBSTA
blacklist rt2500usb
blacklist rt25u98
```
reboot, and then try **ndiswrapper -l**.

I actually already removed them (I think) using ndiswrapper -r rt2500usb.sys etc. then did ndis... -l again and they don't show up. I just did ndiswrapper -l again and this is what it still says:

netrtusb: driver installed
   device (2001:3c00) present (alternate driver rt2570)

After I got this, I proceeded with the rest of your list until the menu.1st screen was blank. I've been searching some more and was wondering if I needed to blacklist the alternate driver. I read something that alluded to that but I am a little unsure if I understood it correctly

---

### Post by RomeReactor on 2007-07-11
Make sure you're writing **menu.lst**, as in "menu-dot-letter l-st", and not **menu.1st**, as in "menu-dot-number one-st". If in doubt, copy/paste the commands.

On a side note, it seems to me that if the drivers were going to work, they would've done so by now; on quite a few ndiswrapper guides, I've seen people having problems with the drivers that come with the CD. As I said [earlier]("http://ubuntuforums.org/showpost.php?p=2995454&postcount=29"), from the (admittedly not thorough) search for information about your USB wireless device, most threads were riddled with problematic installations, most non-working. Maybe you *do* need the SerialMonkey drivers...

---

### Post by Hollywood on 2007-07-11
First, DUH! I was using the 1 instead of l so that is done.
But I am still having a problem with
Code:
sudo iwconfig rausb1 mode Auto

I keep getting Error for wireless request "Set Mode" (8806):
SET failed on device rausb1 ; Invalid argument

I'm going to keep trying to install the monkey, just not having any luck

---

### Post by RomeReactor on 2007-07-11
Try:
```
sudo iwconfig rausb0 mode Auto
```
I've seen most threads refer to your USB as **rausb0** instead of **rausb1**.

After a bit more searching I found [this guide for DWLG122 USB WiFi devices]("http://doc.gwos.org/index.php/HowToDWLG122"), although it seems to be using the same drivers as you (**rt2500usb.sys** and **NETRTUSB.inf**, from **/Drivers/WINXP2K** on your CD).

I found [your device's entry on the NdisWrapper site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/#d") (scroll down to #9); it seems there's a native driver for it, though I don't know how to install it.

Or you could also try the [SerialMonkey]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29") driver solution. I'll keep searching to see if someone else has a less complicated solution.

---

### Post by Hollywood on 2007-07-11
I've already removed those .sys files. I took a quick look at the walkthrough for the other version of G122 basically the only thing that may be different from what I've done is the network/interfaces. I'm going to bring it up again and see if those changes will help.
Still can't manage to install the serialmonkey driver.
I tried tar -xzvf rt2500-cvs-daily.tar.tar and tried entering it with the .gz ending but it doesn't work either and it's listed as a .tar.tar file.
I've tried apt-get install. If I could only get that installed tonight, I could go to sleep peacefully and start fresh tomorrow.

I just tried sudo iwconfig rausb0 mode Auto
 and got:
Error for wireless request "Set Mode" (8806):
SET failed on device rausb0 ; No such device

---

### Post by RomeReactor on 2007-07-11
I just downloaded the [file]("http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz"); it extracted correctly here:
```
tar -xzvf rt2570-cvs-daily.tar.gz
```
If you're having trouble extracting it in Ubuntu, try extracting it in windows with [Gzip]("http://www.gzip.org/gzip124xN.exe"). It should extract as a folder named **rt2570-cvs-2007071103**. Then move that folder to Ubuntu.

**EDIT**: WinRar also extracts .tar.gz files.

---

### Post by jw5801 on 2007-07-11
> **t99 said:**
> As for the mouse thing,Ubuntu must think my touchpad is the middle button because any time i tap it,it pastes!Cant find an option to change it though?

Try qsynaptics
```
sudo apt-get install qsynaptics
```
Then just type qsynaptics into the command line to start the program.
It has lots of options for fiddling with touchpads, worked for mine! However any changes revert at startup unless you run:
```
qsynaptics -r
```
but this is easily fixed by adding the above line to the commands that are run at startup (System > Preferences > Sessions).

---

### Post by RomeReactor on 2007-07-11
> **Hollywood said:**
> I just tried sudo iwconfig rausb0 mode Auto
 and got:
Error for wireless request "Set Mode" (8806):
SET failed on device rausb0 ; No such device

So neither **rausb0** or **rausb1** work? try:
```
cat /etc/network/interfaces
```
what devices are listed there?

---

### Post by Hollywood on 2007-07-11
> **RomeReactor said:**
> I just downloaded the [file]("http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz"); it extracted correctly here:
```
tar -xzvf rt2570-cvs-daily.tar.gz
```
If you're having trouble extracting it in Ubuntu, try extracting it in windows with [Gzip]("http://www.gzip.org/gzip124xN.exe"). It should extract as a folder named **rt2570-cvs-2007071103**. Then move that folder to Ubuntu.

**EDIT**: WinRar also extracts .tar.gz files.

I have tried that exactly, many times. Same with the timestamped one. They also have a more unstable beta version available but that is a last resort.
Is WinRar already installed by default? I'm a little unsure how to unzip a file in a program like that. When I loaded it off the burnt disk, and extracted the files, it created a timestamped file like above, so is that alright or do I still need to do more to it?

Also, the native driver link has gone bust. Ralink no longer has those available, I explored that yesterday. As for the other option, that is identical to the files right off the original install disk.

I'll try using the timestamped version in tar again.

cat /etc/network/interfaces
shows 
auto eth1
iface eth1 inet dhcp
etc......

iface rausb1 inet dhcp
address....
netmask...
gateway...

auto rausb1
wireless channel 6

---

### Post by RomeReactor on 2007-07-11
The **rt2570-cvs-2007071103** has to be a folder; if it is, move it to your home folder and:
```
cd rt2570-cvs-2007071103/Module
```
then:
```
make
```

---

### Post by KIAaze on 2007-07-11
> Is WinRar already installed by default? I'm a little unsure how to unzip a file in a program like that.

No, not installed by default.

_Under Windows:_
*Installation:
Go to the WinRAR site, download the windows installer and install it.
*Usage:
Right-click, extract here

_Under ubuntu:_
*Installation:
Add the multiverse repository as a source.
Then:
```
sudo aptitude install unrar
```
*Usage:
```
unrar x <package>
```

---

### Post by Hollywood on 2007-07-11
> **RomeReactor said:**
> The **rt2570-cvs-2007071103** has to be a folder; if it is, move it to your home folder and:
```
cd rt2570-cvs-2007071103/Module
```
then:
```
make
```

After "make" it said it cannot create directory
Permission denied
rt2570.ko failed to build
make ***[module] Error1

It just struck me that rt2570.ko was listed under the drivers list earlier. Maybe this is a duplicate of a driver I've already tried like the link you gave me from the ndiswrapper list was a copy of my install disk. If so, does this mean I don't have to mess around with UnRar and all that (at least for now)?

---

### Post by Hollywood on 2007-07-11
Okay, I just did sudo modprobe -l | grep rt25
and got:
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko

So, I'm thinking I already have that driver?

---

### Post by RomeReactor on 2007-07-11
Hmmm... looking at the [instructions]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29"), it seems like there's already a **rt2570** driver that comes with Ubuntu, but doesn't work (that happened to me before; Ubuntu came with a Marvell driver that was useless). So perhaps it would be a good idea to continue; further down on the instructions, there are commands to unload the existing driver and register the new one.

As for the make error, try changing permissions on the folder: press CTRL+SHIFT+T to make a new tab in the terminal, and on the new tab enter:
```
cd
```
then
```
sudo chmod 777 -R rt2570-cvs-2007071103
```
now close the new tab, and try **make** again.

---

### Post by Hollywood on 2007-07-11
So basically back to trying to get the new one to unpack properly and compile without these error messages. I thought it was starting to sound too easy. At least once it's done, the rest seems straight forward (jinxed myself)

---

### Post by RomeReactor on 2007-07-11
Found the link to the [native Ralink drivers]("http://www.ralinktech.com/ralink/Home/Support/Linux.html"). Seems to be the fourth one, if I'm not mistaken ([RT2500USB(RT2571/RT2572) (source Code)]("http://www.ralinktech.com.tw/data/RT25USB-SRC-V2.0.8.0.tar.gz")).

---

### Post by Hollywood on 2007-07-11
Now that you brought it up again, I just clicked your link and saw the file. I have that one as well and can't seem to install it either. Going to try the chmod thing now.

OKAY! chmod worked! Did make again and magic happened!  Those instructions are a little outdated however and I'm not sure if I, too, NEED to make a backup copy or just create a directory or something altogether new now that we're in the age of Feisty. I was thinking I could go ahead and do the 
sudo rmmod rt2570
 listed under the Dapper version

---

### Post by RomeReactor on 2007-07-11
I suggest you make the backup anyway; and afterwards copy the driver to the correct folder:
```
sudo cp rt2570.ko /lib/modules/$(uname -r)/kernel/drivers/usb/net/rt2570
```

---

### Post by Hollywood on 2007-07-11
What is the (uname -r)?

---

### Post by RomeReactor on 2007-07-11
It tells the terminal to put there the name of your current kernel. The terminal will interpret it, don't worry.

**EDIT**: Found a more up-to-date [version of the guide]("http://ubuntuforums.org/showthread.php?t=400236") (thread started on April 3rd, 2007).
**ANOTHER EDIT**: Sorry! The guide is for **rt73** drivers.

---

### Post by Hollywood on 2007-07-11
Okay... I knew I jinxed myself.
On the OLD guide, right after:
>./rt2570-backup/rt2570.ko
I got
cp: cannot stat '/lib/modules/....../rt2570.ko': no such file or directory

So I said screw it, and started the For Breezy part and created a proper directory for the new driver

After entering the compile code however:
cp: cannot stat 'rt2570.ko': no such file or directory

Then I thought, these instructions are for 2 different versions, I'm sure I don't need to do the steps for BOTH of them, surely, so I went back to Dapper and

sudo rmmod rt2570

it gave me:
ERROR Module rt2570 is in use 
yes, I did remove my USB adapter before executing this command.

Now, if I start following this NEWER guide...
I assume I replace rt73 with rt2570 where appropriate, but on the part where it says to install build essential, it has "linux-headers-`uname -r`" after it. I didn't have that when I installed it. Because I didn't, is that why I am now having trouble with the above commands in the OLD guide? Could it be caused by not having something that deals with (uname -r)?
If I have to reinstall build essentials with this new ending, I'm thinking that's where I start this guide, and skip over the oversize module stuff to the make install. Am I right?

---

### Post by RomeReactor on 2007-07-11
> **Hollywood said:**
> Okay... I knew I jinxed myself.
On the OLD guide, right after:
>./rt2570-backup/rt2570.ko
I got
cp: cannot stat '/lib/modules/....../rt2570.ko': no such file or directory

That driver in Feisty appears to be in **/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko** (at least in my machine) so the correct command would seem to be:
```
cp /lib/modules/$(uname -r)/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko /home/YOUR_USER_NAME/rt2570-cvs-2007071103/Module/rt2570-backup/rt2570.ko
```
Change **YOUR_USER_NAME** for the name you use to log into Ubuntu (it should be your home folder's name also).

---

### Post by RomeReactor on 2007-07-11
Post the output of:
```
uname -r
```
to know what kernel you have.

---

### Post by Hollywood on 2007-07-11
> **RomeReactor said:**
> Post the output of:
```
uname -r
```
to know what kernel you have.

2.6.20-15-generic

Still after >./rt2570-backup/rt2570.ko
I get an error cp:cannot stat /lib/modules/........ko' not a directory.
Should I try and continue this one or jump in the newer one do you think?

---

### Post by RomeReactor on 2007-07-11
OK, you're going to need the kernel headers for [2.6.20-15]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15_2.6.20-15.27_i386.deb&md5sum=dbe032628ed1d485fa3d642e8da8437a&arch=i386&type=main") and [2.6.20-15-generic]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb&md5sum=510cbf1efb528a0322690009cdb9d233&arch=i386&type=main") (install them in that order).

As for Ubuntu not finding the driver to copy, try it like this:
```
cp /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko /home/YOUR_USER_NAME/rt2570-cvs-2007071103/Module/rt2570-backup/rt2570.ko
```
Remember to change YOUR_USER_NAME for the name you use to log into Ubuntu (it should be your home folder's name also).

Sorry, I've got to go. I'll be back later. In case you need to install more packages, look for them [here]("http://packages.ubuntu.com/").

---

### Post by Hollywood on 2007-07-11
Still gives me the same thing when I type that command. Well, not that command per say as it will lead me to the 
>
part to enter the rt2570-back-up/rt2570.ko, but after I enter that, it gives me the error.

As for the kernel packages, I already have them installed, the same versions, too. I was wondering if blacklisting it would help? Because I can't even delete it at this point. It just says that the module is in use.

---

### Post by RomeReactor on 2007-07-11
I don't know why the guide says to issue the copy command that way; probably because it's outdated. This (>./rt2570-backup/rt2570.ko) is part of the **cp** command; it's one line. The command in my previous post does the same (check your **/home/YOUR_USER_NAME/rt2570-cvs-2007071103/Module/rt2570-backup** folder, there shoud be a copy of the rt2570.ko driver there).

So the next step would be: **Now copy the freshly compiled driver to its place:**
```
sudo cp rt2570.ko /lib/modules/$(uname -r)/kernel/drivers/usb/net/rt2570
```
Remember that for this, your terminal has to be in **/home/YOUR_USER_NAME/rt2570-cvs-2007071103/Module**.
Or, if your terminal is elswhere (or if you just opened it), you can specify the full path:
```
sudo cp /home/YOUR_USER_NAME/rt2570-cvs-2007071103/Module/rt2570.ko /lib/modules/$(uname -r)/kernel/drivers/usb/net/rt2570
```
although in my system (and likely yours) the driver's actual location is **/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko**, so the command should be
```
sudo cp /home/YOUR_USER_NAME/rt2570-cvs-2007071103/Module/rt2570.ko /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570
```
which is the intention of the guide: to overwrite the old driver with the compiled one.

---

### Post by Hollywood on 2007-07-11
Okay, there is rt2570.ko in rt2570-backup

I started with a newly opened terminal, and entered it exactly like you have it in the third box (new term., location of drivers on your sys. which is same as mine, I checked). After hitting return, it gave the response that there was no location apperand at the end of it all. So I did it again ending it with \ like the old guide showed, and of course it sent me to 
>
then what?

I then did it again the first way and got into /home/YOUR_USER_NAME/rt2570-cvs-2007071103/Module first, then entered
sudo cp rt2570.ko /lib/modules/$(uname -r)/kernel/drivers/usb/net/rt2570
There seemed to be no problem, it returned me to command prompt again ending with Module
Still in Module,  I then did depmod -a, no errors just returned me to Module command prompt so 
I did modprobe rt2570 same thing again, back to Module command prompt 
Went to interfaces, everything is there with appropriate substitutions
Did ifup rausb0 and it said it was already configured
No network connection. Will not ping 192.168.0.1 etc
So did dhclient rausb0
Still sleeping
I even rebooted and tried pinging again, nothing. Tried dhclient again, still sleeping.

---

### Post by Hollywood on 2007-07-11
The good news is that at least my adapter is blinking now.
 dhclient rausb0 -still sleeping
lshw
driver:ndiswrapper

---

### Post by RomeReactor on 2007-07-12
Ndiswrapper seems to be conflicting with the newly installed driver (which doesn't use ndiswrapper, since it's native). I think you'll need to uninstall ndiswrapper or at least remove it from the kernel modules:
```
sudo modprobe -r ndiswrapper
```
and remove its entry from **/etc/modules**:
```
gksudo gedit /etc/modules
```
and remove the **ndiswrapper** line. You could also blacklist it:
```
gksudo gedit /etc/modprobe.d/blacklist
```
and add **ndiswraper** at the end of the file, though I think removing it from the modules is enough.

---

### Post by Hollywood on 2007-07-12
I followed all of those steps, even blacklisting and it still shows up as the driver

---

### Post by RomeReactor on 2007-07-12
Let's remove the driver ndiswrapper is using:
```
ndiswrapper -l
```
to see if **netrtusb** is still the only driver being used by ndiswrapper; and
```
ndiswrapper -r netrtusb
```
to remove it. If **ndiswrapper -l** shows more, remove them also. And you could also uninstall it afterwards:
```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by Hollywood on 2007-07-12
Okay last night just before I zonked out, ndiswrapper was said to be blacklisted. Now lshw shows that the network is disabled. 
netrusb is still the driver when ndiswrapper -l is entered but also rt2500usb... so I'll follow your above steps.

Okay, ndiswrapper -r netrtusb, and the same for the other listed invalid driver, and now when I enter ndiswrapper -l nothing comes up, it returns to command prompt.I did lshw to check things out and
Network DISABLED
No drivers show up and yet AGAIN, the logical name has changed, back to rausb1 again.  I don't know how much I worked using rausb0 yesteday, but is it all wasted now?

---

### Post by RomeReactor on 2007-07-12
Looks like either the installation of the rt2570.ko didn't work, or the driver itself isn't the right one for you. In any case, ndiswrapper detected the **netrtusb** as a valid driver. The [ndiswrapper site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/#d") mentioned only two drivers: the native one from [Ralink]("http://www.ralinktech.com/ralink/Home/Support/Linux.html"), and the WinXP driver from the [D-Link site]("http://support.dlink.com/products/view.asp?productid=DWL%2DG122%5FrevB") (which seem to be the *exact* same ones that you found on your CD: NetRTUSB.cat, NetRTUSB.inf, rt25u98.sys, and rt2500.sys). That the lights on your USB WiFi were blinking while ndiswrapper was loaded and using those drivers could mean they were the right ones.

However, at this point my only suggestions would be to install the Win XP drivers through ndiswrapper again, as it could mean that--if the lights on the USB were binking-- the drivers **were** working and the problem was with the actual configuration of the wireless device (using iwconfig, ifconfig, etc).

My other suggestion is to start a new thread in the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=136") section and ask for advice on the Ubuntu IRC channel (#ubuntu @ irc.freenode.net) so people more knowledgeable and with real experience with your USB device can help you. I'm out of new suggestions at the moment, and I'm sorry that I likely made invest more time into solving this problem than necessary. I'm not an expert on ndiswrapper, though I've used it successfully with other devices; but, as I said before, your card seems tricky to get going and I have no experience with it.

---

### Post by Hollywood on 2007-07-13
Okay, I'll reload those other drivers as suggested. I thought the blinking lights were good news! Even at that stage, after doing iwconfig and ifconfig, the information listed looked correct, just no AP. That is weird to me because I had an AP earlier in the process, I think under the rt2500 driver. Oh well. I greatly appreciate all of your time and help on this issue. My particular problem may not be solved, but you've definitely helped me gain a ubuntu education in the process, and knowledge is priceless. Thank you very much! I'll try posting as you suggested after putting that other driver back.

---

### Post by RomeReactor on 2007-07-13
I think you're not that far away from making the USB work; you just need the advice of someone with more experience and who has the same WiFi as you. I hope you get it working soon! Good Luck!

---

### Post by RomeReactor on 2007-07-13
I found a [thread]("http://ubuntuforums.org/showthread.php?t=489035&highlight=DWL-G122+rev+B1") where someone with the same USB WiFi as you (which I think has the same chipset) managed to get it working, following less complicated steps. You could PM **kevdog** and ask him for help. 

In case he suggests starting from scratch, remember to first remove the blacklisted drivers:
```
gksudo gedit /etc/modprobe.d/blacklist
```
and removing these lines:
```
blacklist RT2500USBSTA
blacklist rt2500usb
blacklist rt25u98
```
You could also undo the changes made to your interfaces file:
```
gksudo gedit /etc/network/interfaces
```
and make your **rausb0** or **rausb1** section look like the rest. Or ask him if a reinstall is necessary (hopefully not).

---

