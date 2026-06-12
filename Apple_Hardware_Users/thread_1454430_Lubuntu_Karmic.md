---
title: "Lubuntu Karmic"
date: 2010-04-14
forum: Apple Hardware Users
---

### Post by linuxopjemac on 2010-04-14
Ok I got my second Pismo G3/400 PowerBook via Ebay. It looks really unused, really great for a machine of 10 years old. I wanted Karmic Koala on the machine. Some background information first. Pismo's are known to have very bad CDROM readers. This one was no exception. I was not able to load the packages from CD as it would constantly bork loading other packages. I therefore tried the mini.iso netboot Karmic. This one is not working, the developers did not do a good job here. It still wants to load the packages from the CD. The netboot mini.iso from Jaunty was however successful ([http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)).

I dd-ed the iso to a USB stick (CDROM is not an option as it would bork).

```
sudo dd if=/home/jeroen/Desktop/mini.iso of=/dev/sdb

```
I did this from my Macbook. I then booted the USB in open firmware:

```
boot usb1/disk@1:2,\\yaboot
```

I chose the default "install" and there we went. I chose only a base system as I didn't want to upgrade a desktop too.

After this was done I rebooted in my new Jaunty box. I then wanted Karmic, so I edited the /etc/apt/sources.list to have only Karmic. Then I did:

sudo apt-get update
sudo apt-get dist-upgrade

After quite some time I could reboot into Karmic :)

I am now installing the lubuntu-desktop
```

sudo apt-get install lubuntu-desktop
```

---

### Post by wbar2 on 2010-05-12
I'm attempting to follow your procedure. I have gotten the mini.iso on my thumb drive using dd (it is formatted as Mac OS Standard). I'm able to get into the firmware and find my USB device upon booting up the mac. However, I can't seem to open anything up or boot the system. I try to use DIR to at least look at the files and it says "can't OPEN the DIR device." I try to boot and it says "can't OPEN: ____"

I believe there is only one partition on the disk. I noticed you booted from a second partition. Is it necessary to have two partitions?

---

### Post by linuxopjemac on 2010-05-12
It does not matter how it was formatted as it overwrites it anyway. I would however make it emtpy in gparted before dd.

The powerpc version of mini.iso has two partitions. One for the partition table and one which contains the netbooter and yaboot (nr 2).

try in open firmware:

```
dev / ls
```

then see which usb is connected with an extra disk.

then see which of usb0 or usb1 is connected to the last one with
```
devalias
```

so probably you either boot with
```
boot usb0/disk@1:2,\\yaboot
```
or
```
boot usb1/disk@1:2,\\yaboot
```


**PS note that the Lucid mini.iso works now. I did that 2 days ago!!!**
[http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

---

### Post by wbar2 on 2010-05-12
Ok, I re-did everything, so now it seems to be booting from the USB! We'll see what happens!

---

### Post by linuxopjemac on 2010-05-12
then it will work, have an internet cable connected to your Mac and enjoy the ride...To my opinion, this is the best way of installing Linux...

---

### Post by wbar2 on 2010-05-12
> **linuxopjemac said:**
> then it will work, have an internet cable connected to your Mac and enjoy the ride...To my opinion, this is the best way of installing Linux...

Definitely! It worked. Much more simple than I had anticipated. I had been scouring the web, and everything seemed so complicated. But, its up and running with Lubuntu Lucid!

---

### Post by corrytonapple on 2010-10-14
> **linuxopjemac said:**
> 
```
sudo dd if=/home/jeroen/Desktop/mini.iso of=/dev/sdb

```
I tried mounting this using my iMac G3, which it did not, then, I decided just to make sure it was on there. I put the Flash Drive in my Laptop with Ubuntu, and It now shows up as "CDROM". Also, all the files that were on the flash drive are not visible. How do I reverse the first code I typed in Ubuntu? When I say reverse, I mean make it so all of my files that were on there visible again. I also want to try a good usb stick that I just bought. :)

---

### Post by linuxopjemac on 2010-10-20
Once you have "burned", or in better terms, dd-ed the contents of the iso onto the USB stick you have to boot from the stick from within open firmware. See post #3 how to do that. In OF you either do:

```
boot usb0/disk@1:2,\\yaboot
``` or
```
boot usb1/disk@1:2,\\yaboot
```

depending on which of the two (I presume you have two) USB slots you put the stick in (don't use a hub).

To boot in Open Firmware:
Press power button and hold Option+command+o+f

Hope this helps.

More info you will find on
[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)
at 3. Booting from a USB memory stick, Booting the USB stick.

---

### Post by corrytonapple on 2010-10-20
Thank you for your prompt response. See, I do not want to use this particular flash drive, because it is in bad shape, and I got a new one today. I got to putting the files on via DD, but now the flash drive is a read only, and wont let me do anything to it. I also cannot see the 1GB of files that were on it. I can put those back on, but I know the space is there. So how do I make this flash drive read and write (There are no permissions errors), remove the new files you had me put on it, and make the old files visible. I have no choice but to have this flash drive back to normal without formating. Thank You!

:guitar:

---

### Post by linuxopjemac on 2010-10-21
Make the old files visible? They are gone forever. You dd-ed data over it.

---

### Post by corrytonapple on 2010-10-21
OK. Although I can live with that, others can't. For others sake, could you please add something that says, "WARNING: All of your files that are on there now will be deleted!". So, how do I make the drive both read and writable? Currently it is just read. If you do not know I understand, it is not your "field" here on the forums.
:popcorn:

---

### Post by linuxopjemac on 2010-10-22
format it again within gparted.

---

### Post by Dan Lucier on 2011-01-29
This may be a stupid question, but I've only been using Linux for a few months so please forgive me.

When using the command, "sudo apt-get install", how do you know to put "lubuntu-desktop"? Is this just a very common format  or is there a list somewhere that tells a person what can be installed? Will this procedure work with Peppermint OS too?

Thanks

---

