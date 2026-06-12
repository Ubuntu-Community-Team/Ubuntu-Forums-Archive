---
title: "i need an ubuntu live cd for powerpc that comes with gnash flash player"
date: 2012-01-22
forum: Apple Hardware Users
---

### Post by kdude55 on 2012-01-22
i have a powerbook g4 alinimum with a dead hard drive and i have ubuntu 12.04 running off live cd its good for doing my homework and thats it 
i want to play some online games but stock ubuntu dosent come with flash or gnash
i was wondering if any one made there own live cd that comes with flash and perfurably has mp3 codecs also. i dont care what version and it dosent even need to be ubuntu it just has to have flash and suport powerpc
ps. sorry about my speling

---

### Post by canhoto on 2012-01-22
> **kdude55 said:**
> i have a powerbook g4 alinimum with a dead hard drive and i have ubuntu 12.04 running off live cd its good for doing my homework and thats it 
i want to play some online games but stock ubuntu dosent come with flash or gnash
i was wondering if any one made there own live cd that comes with flash and perfurably has mp3 codecs also. i dont care what version and it dosent even need to be ubuntu it just has to have flash and suport powerpc
ps. sorry about my speling

Have you tried to find a cheap HD on Ebay? There are really very cheap ones, you know? Running from the live CD is slow.

---

### Post by gwjvan on 2012-01-23
A live USB stick would be faster than Live CD (it is possible for PPC, not too hard, but a couple more steps than on x86)


Also: You can kind of work around a live cd/usb by loading packages when you startup the live session. 

First, boot the live cd/usb without installing any extra programs/packages. Then download each extra package you want to add with:

    sudo apt-get install -d [package-name]


This will not install the packages, but will save them to /var/cache/apt/archives. After you've downloaded the files, copy the contents of /var/cache/apt/archives to an extra flash drive (not the one you boot from, if you decide to go that route). In this example, we're going to assume you copied the files to a directory called "startup_packages" on your usb stick (in this example it has the label "USB_DRIVE_NAME").


Now, whenever you reboot, on startup, mount your extra usb stick and run:

    sudo dpkg -i /media/USB_DRIVE_NAME/startup_packages/*.deb


An advantage of doing it this way (over creating a custom live image) is you can add/remove extra programs without too much effort.

---

### Post by conal on 2012-01-24
I hate to be a naysayer but gnash really is not up to task for on-line flash games, and there is no adobe flash for powerpc linux. When my kids want to play Friv I have to reboot into Mac Os X. IF you are using a powerpc mac and have the original tiger (or leopard) install disk you could install this on a USB drive if a new hard drive is really not on option - but a second hand hd on ebay could be almost as cheap as a USB stick anyway! I think the latest version of adobe flash for powerpc os x is 10.1.102.64, but I believe there is a hack to get sites that require flash 11 working.

---

### Post by kdude55 on 2012-01-24
i also forgot to say i dont have an osx install disk an i would like to know how to boot from usb i tried to instal to extrnal hard drive but it wont show up on the mac boot loader and i dont realy know anything about yaboot

---

### Post by conal on 2012-01-25
You can make a live usb with the instructions here: [https://wiki.ubuntu.com/PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ")

Afraid I don't know how to make a 'persistence loop' on a powerpc (to save changes). If you want a proper install on usb, you can do that from the live cd/usb. then you can either chose it by holding down the alt key when you switch it on (even if your extenal HD won't show up, a usb stick might), or you are feeling brave with yaboot can edit the yaboot.conf file according to the advice here [https://wiki.ubuntu.com/PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ") and here [http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10#manual_yaboot]("http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10#manual_yaboot")

---

### Post by svtguy88 on 2012-01-27
Be forewarned that Flash on PPC is pitiful, regardless of what player you use...

I'm not sure exactly what you are trying to do, but my setup was a dual 1.8 Ghz G4 tower with 1.5 GB RAM, and any "HD" flash was totally unusable, if you plan to watch youtube and the like...

Heck, even on OS X, Flash for PPC is reallly bad.

---

### Post by kdude55 on 2012-02-06
i am trying to play a flash game that will run in flash 7 and ubove and i made a bootable usb stick and it would not load my understanding is that the only way to run any os from usb on powerpc is if you back up your internal to external using superduper and it will only work usin mac osx and i dont have a mac os x disk i actualy found this laptop in the trash it came with tiger but when i get the monie to buy leopard im just going to buy that and run that in the mean time im just going to run ubuntu 12.04

---

### Post by kdude55 on 2012-02-06
(erly alpha) live cd i will try to run apps that are on a flash drive

---

