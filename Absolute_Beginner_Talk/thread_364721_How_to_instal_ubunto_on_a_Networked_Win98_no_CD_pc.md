---
title: "How to instal ubunto on a Networked Win98 no CD pc"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-18
Hi,

I have already asked much the same question on these boards, but I wonder if it has missed the people who can help. 

My situation is:

I have an aged win98 pc without a working CD

I can boot to linux from tomsrtbt floppy.

I have tried instluxNetubuntu6_06english.exe but each time I have tried it, my system rebooted into win98 and asked me to uninstall the instlux program.

I know anyone who answers does so out of the goodness of their own hearts (I read the sticky's at the top of this forum). I hope you don't think I am cheeky posting much the same question twice, but I am enjoying ubuntu so much on my (ex) XP machine and would like to make it better on my Win98 pc.

So can you help me install ubuntu from a machine without a CD drive, but with a network connection and the ability to run a small version of linux (but no diskspace in the small version of linux)? 

TIA

---

### Post by kingcharles1666 on 2007-02-18
Hi,

Are you just looking to install linux or does it have to be ubuntu?
Because I have had a similar issue (with a laptop) but I managed to get DSL (Damn Small Linux) on it by  taking out the harddrive and by copying the DSL stuff onto it.
worked fine. I used this method:
[http://www.damnsmalllinux.org/wiki/index.php/Talk:Installing_to_the_Hard_Disk](http://www.damnsmalllinux.org/wiki/index.php/Talk:Installing_to_the_Hard_Disk)

Cheers

---

### Post by ubername on 2007-02-27
> **kingcharles1666 said:**
> Hi,

Are you just looking to install linux or does it have to be ubuntu?
Because I have had a similar issue (with a laptop) but I managed to get DSL (Damn Small Linux) on it by  taking out the harddrive and by copying the DSL stuff onto it.
worked fine. I used this method:
[http://www.damnsmalllinux.org/wiki/index.php/Talk:Installing_to_the_Hard_Disk](http://www.damnsmalllinux.org/wiki/index.php/Talk:Installing_to_the_Hard_Disk)

Cheers

Hi

Thanks for that. It's a good idea (but I guess if you get your hard drive read/write able from another PC you could load ubuntu or anything else you like!) Also my PC is so ancient it doesn't have USB ports or I would have used 'install from memory stick' options.

I think I am intrigued by the possibility of booting linux from a floppy, getting enough RAM available to run some kind of disk partitioner, accessing the net to download (any version of) linux, rebooting and *voila* booting into linux.

Is this a pipe dream?

I am also hoping that when I do boot into linux it will sort out my CD drive, which worked for the first 5 years or so of the PC's life but has been sporadic (to say the least) since then (the subsequent 6 years!). I have switched the actual drive, I found some advice suggesting moving the network card from one slot to another (!) which worked for a while, I got it working by just plain messing a couple of days ago but stupidly did not have the linux disk in, and when I tried again it had gone.

My stumbling block so far seems to be getting the RAM. I have tried initrd but to no avail. In fact any help on using initrd would be welcome.

TIA

---

### Post by arochester on 2007-02-27
And how much RAM do you actually have?

You could, for example, see "Installing Ubuntu on a machine with no CDROM drive" at [http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)

---

### Post by justifier on 2007-02-27
> **kingcharles1666 said:**
> Hi,

Are you just looking to install linux or does it have to be ubuntu?
Because I have had a similar issue (with a laptop) but I managed to get DSL (Damn Small Linux) on it by  taking out the harddrive and by copying the DSL stuff onto it.
worked fine. I used this method:
[http://www.damnsmalllinux.org/wiki/index.php/Talk:Installing_to_the_Hard_Disk](http://www.damnsmalllinux.org/wiki/index.php/Talk:Installing_to_the_Hard_Disk)

Cheers

just for future notice i also managed to do this with ubuntu, just do it untill you get the remove disc message, and when it reboots switch off and replace the HDD and finish the instiallation from there. 

Or plug a CD drive in?

---

### Post by actuary286 on 2007-02-27
Debian, on which Ubuntu is based, offers the ability to boot from a set of floppy disks then download packages over the internet for installation. Here is the link: [http://www.debian.org/distrib/floppyinst]("http://www.debian.org/distrib/floppyinst").

Good Luck!

---

### Post by oilchangeguy on 2007-02-27
the user states his computer has no usb ports. then this computer was born with the first generation of windows 95 (usb support came in a later version of 95). it's probably got a pent. 1 cpu of around 100mhz. and maybe 32mb of ram and a hard drive of less than 10gb. this computer while great when new, is not worth going thru the trouble of trying to install any version of linux or any other operating system. the user should consider retiring this computer, as the user states they have an xp machine. the logical choice would be make that computer a dual boot computer.

---

### Post by ubername on 2007-02-28
> **oilchangeguy said:**
> the user states his computer has no usb ports. then this computer was born with the first generation of windows 95 (usb support came in a later version of 95). it's probably got a pent. 1 cpu of around 100mhz. and maybe 32mb of ram and a hard drive of less than 10gb. this computer while great when new, is not worth going thru the trouble of trying to install any version of linux or any other operating system. the user should consider retiring this computer, as the user states they have an xp machine. the logical choice would be make that computer a dual boot computer.

Well said.  My computer (built from bits, but not by me) originally came with win95 (233Mhz processor, I was cutting edge!) and I managed to upgrade it to win98. Then I added some more memory so it now has 133Mb. It has an original HD of 3Gb, and another I added with 8Gb (the 3Gb disk has 2 partitions, one of  2Gb and one of 1 Gb, the 8Gb is one partition)

I still relish the challenge of running any Linux flavour on it, even with its limitations. FWIW I have actually quite a responsive Win98  on it, although it does take a lot of housekeeping to keep it running smoothly.

I am also a bit short of cash (so another box is out of the question), and my children love nothing better than playing flash-based games on a PC so keep trying to get me off my newer (dual boot Ubuntu and XP, 3Ghz Pent, 512Mb RAM, 80Gb HD) machine. I have shown them that Ubuntu is much faster on this (once XP) box than XP is, so if I could get a version of Linux running on the old box I could point them there.


Further advice welcome, but I take the point that perhaps I am asking too much of old kit.

TIA

---

### Post by kingcharles1666 on 2007-02-28
I think the usb method was not understood. No big deal but just to clarify.
You take out the hd of the machine without CD.
Then hook it to a modern machine using the usb casing and partition it and load the files on.
Then you drop it back into the old laptop/desktop and run the install from there.
You need to run the install on the machine that you will use it on because it will need to configure the hardware.

If you want to try linux on old hardware this link is very useful also:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

You will be surprised what you can do with an old P1 at 75Mhz!!!

---

### Post by ubername on 2007-02-28
> **kingcharles1666 said:**
> I think the usb method was not understood. No big deal but just to clarify.
You take out the hd of the machine without CD.
Then hook it to a modern machine using the usb casing and partition it and load the files on.
Then you drop it back into the old laptop/desktop and run the install from there.
You need to run the install on the machine that you will use it on because it will need to configure the hardware.

If you want to try linux on old hardware this link is very useful also:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

You will be surprised what you can do with an old P1 at 75Mhz!!!

Thanks for this. I didn't misunderstand (I think!) My idea is to try and do the install without resort to any other machine, hardware or bought software. If I could find a win98 partition manager (free, as in really free, not nicked) which worked and allowed creation of Linux partitions (so SwissKnife is out), I would be a step forward.

BTW I am really grateful for all the advice and comments I am getting on this topic. I do know I might be a basket case for trying to get this to work, but I think it would be really cool to be able to get a Linux install working on a really old PC which only has a floppy  drive and a network connection (and I'm not really into burning any more floppies than I have to!)

TIA

As I may have metnioned

---

### Post by ubername on 2007-03-08
Sorry for the long post. I could have attached the file, but I suspect many people would hesitate to open an attachment.

OK Major step forward! On my rubbish old (previously) Win98 PC  with non functional CD drive, but network connection available:

I have managed to install Debian with two floppies, one called boot.img and the other called root.img. I can now run Debian with a choice of KDE or Gnome! But they dont look like ubunto or seem to offer the same facilities,

Looking at the floppies, it strikes me that I could install ubuntu via the same process if I had the right commands in a file called initrd.list. This is  (are?) the current contents of the file:

anna 1.06
archdetect 1.14
bogl-bterm-udeb 0.1.18-1.1
busybox-cvs-udeb 20040623-1
cdebconf-newt-udeb 0.74.2
cdebconf-udeb 0.74.2
choose-mirror 1.07
console-keymaps-at 2002.12.04dbs-49
console-keymaps-usb 2002.12.04dbs-49
countrychooser 1.11
dhcp-client-udeb 2.0pl5-19.1
discover1-data-udeb 1.2005.01.08
discover1-udeb 1.7.7
di-utils 1.08
di-utils-reboot 1.08
di-utils-shell 1.08
di-utils-terminfo 1.08
download-installer 1.01
ethdetect 1.14
fb-modules-2.4.27-3-386-di 1.04sarge2
firmware-modules-2.4.27-3-386-di 1.04sarge2
floppy-retriever 1.05
hw-detect 1.14
iso-3166-udeb 0.44-1
kbd-chooser 1.10
kernel-image-2.4.27-3-386-di 1.04sarge2
languagechooser 1.45
libdebconfclient0-udeb 0.74.2anna 1.06
archdetect 1.14
bogl-bterm-udeb 0.1.18-1.1
busybox-cvs-udeb 20040623-1
cdebconf-newt-udeb 0.74.2
cdebconf-udeb 0.74.2
choose-mirror 1.07
console-keymaps-at 2002.12.04dbs-49
console-keymaps-usb 2002.12.04dbs-49
countrychooser 1.11
dhcp-client-udeb 2.0pl5-19.1
discover1-data-udeb 1.2005.01.08
discover1-udeb 1.7.7
di-utils 1.08
di-utils-reboot 1.08
di-utils-shell 1.08
di-utils-terminfo 1.08
download-installer 1.01
ethdetect 1.14
fb-modules-2.4.27-3-386-di 1.04sarge2
firmware-modules-2.4.27-3-386-di 1.04sarge2
floppy-retriever 1.05
hw-detect 1.14
iso-3166-udeb 0.44-1
kbd-chooser 1.10
kernel-image-2.4.27-3-386-di 1.04sarge2
languagechooser 1.45
libdebconfclient0-udeb 0.74.2
libdebian-installer4-udeb 0.29
libiw27-udeb 27-2
libnss-dns-udeb 2.3.2.ds1-22sarge4anna 1.06
archdetect 1.14
bogl-bterm-udeb 0.1.18-1.1
busybox-cvs-udeb 20040623-1
cdebconf-newt-udeb 0.74.2
cdebconf-udeb 0.74.2
choose-mirror 1.07
console-keymaps-at 2002.12.04dbs-49
console-keymaps-usb 2002.12.04dbs-49
countrychooser 1.11
dhcp-client-udeb 2.0pl5-19.1
discover1-data-udeb 1.2005.01.08
discover1-udeb 1.7.7
di-utils 1.08
di-utils-reboot 1.08
di-utils-shell 1.08
di-utils-terminfo 1.08
download-installer 1.01
ethdetect 1.14
fb-modules-2.4.27-3-386-di 1.04sarge2
firmware-modules-2.4.27-3-386-di 1.04sarge2
floppy-retriever 1.05
hw-detect 1.14
iso-3166-udeb 0.44-1
kbd-chooser 1.10
kernel-image-2.4.27-3-386-di 1.04sarge2
languagechooser 1.45
libdebconfclient0-udeb 0.74.2
libdebian-installer4-udeb 0.29
libiw27-udeb 27-2
libnss-dns-udeb 2.3.2.ds1-22sarge4anna 1.06
archdetect 1.14
bogl-bterm-udeb 0.1.18-1.1
busybox-cvs-udeb 20040623-1
cdebconf-newt-udeb 0.74.2
cdebconf-udeb 0.74.2
choose-mirror 1.07
console-keymaps-at 2002.12.04dbs-49
console-keymaps-usb 2002.12.04dbs-49
countrychooser 1.11
dhcp-client-udeb 2.0pl5-19.1
discover1-data-udeb 1.2005.01.08
discover1-udeb 1.7.7
di-utils 1.08anna 1.06
archdetect 1.14
bogl-bterm-udeb 0.1.18-1.1
busybox-cvs-udeb 20040623-1
cdebconf-newt-udeb 0.74.2
cdebconf-udeb 0.74.2
choose-mirror 1.07
console-keymaps-at 2002.12.04dbs-49
console-keymaps-usb 2002.12.04dbs-49
countrychooser 1.11
dhcp-client-udeb 2.0pl5-19.1
discover1-data-udeb 1.2005.01.08
discover1-udeb 1.7.7
di-utils 1.08
di-utils-reboot 1.08
di-utils-shell 1.08
di-utils-terminfo 1.08
download-installer 1.01
ethdetect 1.14
fb-modules-2.4.27-3-386-di 1.04sarge2
firmware-modules-2.4.27-3-386-di 1.04sarge2
floppy-retriever 1.05
hw-detect 1.14
iso-3166-udeb 0.44-1
kbd-chooser 1.10
kernel-image-2.4.27-3-386-di 1.04sarge2
languagechooser 1.45
libdebconfclient0-udeb 0.74.2
libdebian-installer4-udeb 0.29
libiw27-udeb 27-2
libnss-dns-udeb 2.3.2.ds1-22sarge4
load-floppy 1.05
lowmemcheck 1.07
main-menu 1.02
nano-udeb 1.2.4-5
netcfg 1.08
net-retriever 1.01
nic-modules-2.4.27-3-386-di 1.04sarge2
nic-shared-modules-2.4.27-3-386-di 1.04sarge2
nic-usb-modules-2.4.27-3-386-di 1.04sarge2
rootskel 1.10.3
rootskel-locale 1.10.3
socket-modules-2.4.27-3-386-di 1.04sarge2
udpkg 1.00
wireless-tools-udeb 27-2

di-utils-reboot 1.08
di-utils-shell 1.08
di-utils-terminfo 1.08
download-installer 1.01
ethdetect 1.14
fb-modules-2.4.27-3-386-di 1.04sarge2
firmware-modules-2.4.27-3-386-di 1.04sarge2
floppy-retriever 1.05
hw-detect 1.14
iso-3166-udeb 0.44-1
kbd-chooser 1.10
kernel-image-2.4.27-3-386-di 1.04sarge2
languagechooser 1.45
libdebconfclient0-udeb 0.74.2
libdebian-installer4-udeb 0.29
libiw27-udeb 27-2
libnss-dns-udeb 2.3.2.ds1-22sarge4
load-floppy 1.05
lowmemcheck 1.07
main-menu 1.02
nano-udeb 1.2.4-5
netcfg 1.08
net-retriever 1.01
nic-modules-2.4.27-3-386-di 1.04sarge2
nic-shared-modules-2.4.27-3-386-di 1.04sarge2
nic-usb-modules-2.4.27-3-386-di 1.04sarge2
rootskel 1.10.3
rootskel-locale 1.10.3
socket-modules-2.4.27-3-386-di 1.04sarge2
udpkg 1.00
wireless-tools-udeb 27-2

load-floppy 1.05
lowmemcheck 1.07
main-menu 1.02
nano-udeb 1.2.4-5
netcfg 1.08
net-retriever 1.01
nic-modules-2.4.27-3-386-di 1.04sarge2
nic-shared-modules-2.4.27-3-386-di 1.04sarge2
nic-usb-modules-2.4.27-3-386-di 1.04sarge2
rootskel 1.10.3
rootskel-locale 1.10.3
socket-modules-2.4.27-3-386-di 1.04sarge2
udpkg 1.00
wireless-tools-udeb 27-2

load-floppy 1.05
lowmemcheck 1.07
main-menu 1.02
nano-udeb 1.2.4-5
netcfg 1.08
net-retriever 1.01
nic-modules-2.4.27-3-386-di 1.04sarge2
nic-shared-modules-2.4.27-3-386-di 1.04sarge2
nic-usb-modules-2.4.27-3-386-di 1.04sarge2
rootskel 1.10.3
rootskel-locale 1.10.3
socket-modules-2.4.27-3-386-di 1.04sarge2
udpkg 1.00
wireless-tools-udeb 27-2

libdebian-installer4-udeb 0.29
libiw27-udeb 27-2
libnss-dns-udeb 2.3.2.ds1-22sarge4
load-floppy 1.05
lowmemcheck 1.07
main-menu 1.02
nano-udeb 1.2.4-5
netcfg 1.08
net-retriever 1.01
nic-modules-2.4.27-3-386-di 1.04sarge2
nic-shared-modules-2.4.27-3-386-di 1.04sarge2
nic-usb-modules-2.4.27-3-386-di 1.04sarge2
rootskel 1.10.3
rootskel-locale 1.10.3
socket-modules-2.4.27-3-386-di 1.04sarge2
udpkg 1.00
wireless-tools-udeb 27-2

Can anyone out there help me with contents for this file which will help me with ubuntu?

I have loaded both the KDE and Gnome interfaces to the version of debian I have installed, and they both lack certain things (as far as I can find out) such as easy updates. So Ubuntu would be good for me.

TIA

---

