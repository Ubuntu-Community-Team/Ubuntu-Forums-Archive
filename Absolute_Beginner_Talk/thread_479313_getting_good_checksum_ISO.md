---
title: "getting good checksum ISO"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Linux learner on 2007-06-20
Hi all


Having a problem getting an ISO of 7.04 that will pass Winmd5sum check

have downloaded the 492MB file twice using XP SP2 on 4Mb line and no luck

Each time no files shown withing the ISO file

Short of ordering online is there anything I can try (ie download manager of some kind)?

help appreciated

---

### Post by coxy on 2007-06-20
Where are you downloading from? Try one of the official mirrors:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by kerry_s on 2007-06-20
do not open the iso.
it's way bigger than 492MB

[http://mirrors.kernel.org/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso](http://mirrors.kernel.org/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso)
should be 696M  

this is the mini.iso net installer, it installs straight from the net
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)
should be 8.4M , use as a last resort

make sure you burn as a image at 4x for the best results, when you boot the cd there's a option to check it, use it.

---

### Post by molly_001 on 2007-06-20
> **Linux learner said:**
> linux learner wrote: ...


Having a problem getting an ISO of 7.04 that will pass Winmd5sum check

have downloaded the 492MB file twice using XP SP2 on 4Mb line and no luck

Each time no files shown withing the ISO file




As far as I know, you will be unable to "see" any individual files or md5checksums for individual files when the file is in .iso form.

What I do is download the .iso image (in your case, 492.2 MB)
then use [md5deep (developed by Jesse Kornblum for the U.S. Air Force)]("http://md5deep.sourceforge.net/")
to check the known correct md5 against the .iso I downloaded.

Then after burning, you can use the "Check CD for defects" and you will
have 100% assurance of image quality and accuracy.

---

### Post by Linux learner on 2007-06-20
Thx for the answers

 BTW im downloading server edition for our network

Downloaded from Ubuntu.com/getubuntu/download both times

i'm not opening it, its 492MB on the site
on my HDD its showing as 504,234KB
I havent burned the image as md5 fails both downloads
the mini.iso method wont work (will it?) as im not loading onto this computer but a Win98SE one

one site (unsure which now though) showed pics of files within the iso image (on HDD) as correct and just the ISO file as incorrect
I did exactly as u said, downloaded and then md5 which is when it shows checksums different

---

### Post by atria on 2007-06-20
If you're running windows, try downloading cygwin and use the md5sum in it. If the checksum is still different, there might be a problem with your ram or harddisk/controller (assuming that other mirrors give corrupted files as well).

---

### Post by paparucino on 2007-06-20
> **Linux learner said:**
> Thx for the answers

 BTW im downloading server edition for our network

Downloaded from Ubuntu.com/getubuntu/download both times

This is the officicial site and the size is 698Meg
You can use this torrent [http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso.torrent)

---

### Post by molly_001 on 2007-06-20
> **Linux learner said:**
> linux learner wrote: ...


I havent burned the image as md5 fails both downloads
the mini.iso method wont work (will it?) as im not loading onto this computer but a Win98SE one

I did exactly as u said, downloaded and then md5 which is when it shows checksums different


It would be really unusual for you to acquire a corrupt download for a file size which matches as it should.

Are you certain that you used md5deep?  Your best bet is to use md5deep so that you can get md5 hash (takes about 15 seconds, on my machine) in a true 16-bit DOS environment.

Let me know if you need any help with md5deep.

Edit:  As you know, the server install is 492.2 MB.  Ubuntu 7.04 FF server install CD = 492.2 MB .iso

---

### Post by atria on 2007-06-20
paparucino, he is trying to download the server ISO, not the desktop version.

[quote=Linux Learner]on my HDD its showing as 504,234KB[/quote]
This is because in windows, 1024KB = 1MB.

There is another way to fix the corrupted download:
After downloading the corrupted iso, use bittorrent to hash-check the file and repair(download resume) the broken parts. That worked for me in the past when i had faulty ram.

Good luck

//edit
link to ubuntu-7.04-server-i386.iso torrent:
[http://torrent.ubuntu.com:6969/file?info_hash=%FA%7B%91%CB-J%F7%E1%ACZd%01y%2BU%1D/%1Cq%F1](http://torrent.ubuntu.com:6969/file?info_hash=%FA%7B%91%CB-J%F7%E1%ACZd%01y%2BU%1D/%1Cq%F1)

---

### Post by Golyadkin on 2007-06-20
Are you experiencing packetloss then? Because otherwise using a simple HTTP download over TCP should give you a perfectly fine file. If the file is too small after downloading, the server has cut off the connection too soon (maybe you downloaded too slow, and some kind of timer expired) or your harddisk was full?

---

### Post by Linux learner on 2007-06-20
downloaded again from official site - again 492.42MB this time using a download manager (no quicker)
and again winmd5sum failed it

is md5deep the same thing as winmd5sum?

will AVG intefere with the integrity?

downloaded cygwin setup.exe and winmd5sum failed it too

---

### Post by molly_001 on 2007-06-20
I could download the file you need, run it through md5deep here on my computer, verify that it passes with the correct hash, and then upload it for you to my website.

Then, you in turn, could download it onto your computer.

Then I would show you how (or voice chat, whatever) how to check its md5 hash in 16-bit DOS (with md5deep).

Let me know what you think.

---

### Post by Linux learner on 2007-06-20
> **Golyadkin said:**
> Are you experiencing packetloss then? Because otherwise using a simple HTTP download over TCP should give you a perfectly fine file. If the file is too small after downloading, the server has cut off the connection too soon (maybe you downloaded too slow, and some kind of timer expired) or your harddisk was full?


HD not full and dont think packet loss is a problem
from the site ubuntu/getubuntu/download or from any sites linked on that site
it starts download as 492.42MB

Am now downloading from the site Kerry posted which is a larger file

---

### Post by steve.horsley on 2007-06-20
492M is the correct size for a server install (i-386). I wonder if your checksummer is wrong? 
You could try this one (came up first in my Google search): [http://www.fastsum.com/](http://www.fastsum.com/)
You could always burn and try what you've got. 

Did you realise that the server edition of Ubuntu comes without a GUI? It's command-line only. Maybe you should start with the desktop version, but it depends on your intended usage.

---

### Post by kerry_s on 2007-06-20
If your wiping the 98 system just grab the mini.iso and burn it to cdrw at 4x it can install any supported *ubuntu version including the server, never mind the md5 check, just run the check disk in the boot options after you boot it. the mini requires internet access though so the machine will need to be connected to the net. you only need the full cd if you want to run it live to check compatiabilty or you don't have a connection for that machine.

---

### Post by Linux learner on 2007-06-20
Thx for all the help

downloaded the larger file and that failed winmd5sum too

looked at it with iso buster and seems it might be bootable so will burn it and try boot

dont want to wipe win98SE as hoped to install with both working

Didnt realise server was without gui so probably not so clever for rank beginner!

Will try the other checksum tool if the 696.24MB file i burn wont boot

---

### Post by atria on 2007-06-20
If the checksum doesn't match, the installation can still break even if the disc boots.

Anyway after downloading cygwin, use the following commands in your windows command prompt (Start >> Run, enter "cmd" without the quotes and click ok)

```

set PATH=C:\cygwin\bin;%PATH%
md5sum <path to your iso>

```

For example: md5sum C:\ubuntu-7.04-server-i386.iso
if your ubuntu iso is directly inside C drive.

See if the checksum matches.

---

### Post by Linux learner on 2007-06-20
Sry for the delay in responding

last download was from
[http://mirrors.kernel.org/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso](http://mirrors.kernel.org/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso)     696.24MB

downloaded Fastsum as suggested and it passed the file as no changes

burned it to cd at x4 but it failed to boot up the other computer

Wondering if there's a cd problem (BIOS?) so will investigate that before anything else

thx so far

will download the desktop instead of server once ive checked the cd rom

---

### Post by Golyadkin on 2007-06-20
Maybe there is an option you can check in your CD burning program to make the CD bootable. Because even if the BIOS is set to boot from CD before it boots from harddisk, if the CD is not burned as bootable, it will not work.

Somem motherboards have an option like F12 to enter a bootmenu from the BIOS.

---

### Post by kerry_s on 2007-06-20
> **Linux learner said:**
> Sry for the delay in responding

last download was from
[http://mirrors.kernel.org/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso](http://mirrors.kernel.org/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso)     696.24MB

downloaded Fastsum as suggested and it passed the file as no changes

burned it to cd at x4 but it failed to boot up the other computer

Wondering if there's a cd problem (BIOS?) so will investigate that before anything else

thx so far

will download the desktop instead of server once ive checked the cd rom


Did you burn it as a image? you can't just do a regular burn that will just be a copy of the iso.

---

### Post by Linux learner on 2007-06-21
Many thanks to everyone for their help (and offer of further help)

To date I have successfully burned and booted desktop version to the point
at which the disk partitioner hangs
I will investigate the forum for help on that topic and put up a new thread if no joy

Fast sum gave the ok to winmd5sum checksum so odd that md5 failed everything

Booting problem solved by making the cd rom master not slave (DOH! but old box not used in a long time)

Ubuntu frontend looks v classy!

---

### Post by molly_001 on 2007-06-22
If the disc partitioner continues to hang, burn an ISO of 6.06 .  One thing I have noticed is that the more recent versions of GParted are using some video drivers that act funny on some machines.  But the Gparted and Ubuntu versions of around June, 2006 (one year ago in case you are reading this thread much later) do not use the same video driver conventions.  For instance, I can get the June, 2006, version of Gparted to load fine on a Dell 2400.  But I can't get the June, 2007, version to do the same.  It can't find drivers to run the video (integrated) even when I use command line Forcevideo myself.

---

