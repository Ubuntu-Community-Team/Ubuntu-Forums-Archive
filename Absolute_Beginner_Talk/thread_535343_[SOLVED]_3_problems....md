---
title: "[SOLVED] 3 problems..."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Maqz447 on 2007-08-26
Hi everyone. I'm a lifetime DOS/windows users who's been curious about Linux for a while, and who's intrigued by the free software philosophy (and fed up with Micro$oft). I finally decided to give Ubuntu a shot, but now I'm stuck, and I can't seem to find the solution to my problem(s) in these forums. Hence this post.  

I've successfully installed Ubuntu 7.04 to dual-boot with Vista on my new Dell Inspiron 530. So far, so good. 

The first problem I encountered was that I couldn't get Ubuntu to detect the proper resolution (1680 x 1050) on my widescreen monitor. I understand this is normal, and that I should probably download the lgrfx driver from ATI and do some small tweaks to get it to work. 

However, I can't get Ubuntu to "find" my Internet connection. This is odd, because I first installed it (using the very same Live CD) on an old IBM Pentium III which I connected to the same router, and Ubuntu had no problem connecting  to the Internet on that old machine. I have an ADSL connection. When I boot into Vista, the connection is working fine.

I guess this means I need a new driver for the network card in my new Dell. This is an Intel 82562V-2 10/100 Ethernet card. I downloaded a driver from Intel that I believe is the correct one, as a tar file named  e1000-3.5.17.tar.gz. Of course, I had to download this in Vista. 

Now, since I don't have a floppy drive, the only way to get this driver into my Ubuntu partition is to burn it to a DVD then copy it to the hard drive from Ubuntu. This brings me to my third problem: Ubuntu can't "mount" the dvds I feed it. I get a dialog box saying: "Cannot mount volume" and "invalid mount option" when I insert a dvd. However, Ubuntu is able to read the name on the dvd. But I can't open it in places - computer either (I get the same message). The exact same thing happens on the old IBM, by the way. Both dvd rw drives (I have one in each machine) are working fine in Windows.

The dvd problem seems to be common, but I haven't found a solution here that has worked. I must also confess that I'm a complete noob when it comes to Linux/Unix, so if someone tells me to edit this or that, I can only respond with "how?"...

I'm motivated to spend time learning Linux, but I would like to have a working system... and without an internet connection nor a working cd/dvd drive, there isn't much I can do with my Ubuntu unfortunately. So, does anyone have any tips on how to get out of this mess? It would be greatly appreciated!

---

### Post by nonewmsgs on 2007-08-26
actually if you open gparted as a side effect it mounts all your drives including the windows partition so you actually didn't need the dvd.  there are more correct ways to do it but i find that works very well.  then the drive should be on the desktop and you just double click.

wow there have been a lot of nonworking NIC issues lately.  that's usually a very work straight out of the box thing, and intel works with the linux community so you shouldn't really need a driver AFAIK.

ok the little computer at the top right (thats the network moniter) see if there is anything that isn't just Lo or loop and make sure the enabled networking is checked.  (i dont meant to insult your intelligence but let's get the simplest things out of the way first).

for the right resolution for wide screens, in my experience i change the xorg.conf file manually.  type in
sudo gedit /etc/X11/xorg.conf
and find the resolution section in the bottom and type in the correct one first on all the resolution lines and it will use that on next reboot.

---

### Post by Maqz447 on 2007-08-26
thanks for your suggestions! When I click on the little computer on the top right, my only option is "manual configuration". I choose that, then get to the network settings box (same as system - network or wherever it was). There's no option for "wired connection" there, only for modem connection.

I tried **sudo lshw -C network**, it identified the card as made by Intel, but said "network UNCLAIMED". 

As for gparted, I couldn't find it, can it only be accessed through the terminal?

I edited xorg.conf like you said, I'll boot into Ubuntu again and see how it went...

---

### Post by p_quarles on 2007-08-26
Support for most NICs (and definitely Intel's) is built right into the Linux kernel, so you don't need a driver. Obviously, the CD-ROM drive is another problem, but one thing at a time.

Can you post the output of the following command:
```
ifconfig -a
```

---

### Post by Maqz447 on 2007-08-26
Nope, that didn't work. It's still 1280x1024. I can't select a higher resolution manually either. I checked the xorg.conf file again, it now has "1680x1050" as the first resolution in each line, but that doesn't help. I'm guessing I need the driver?

---

### Post by mysticmatrix on 2007-08-26
> **Maqz447 said:**
> Nope, that didn't work. It's still 1280x1024. I can't select a higher resolution manually either. I checked the xorg.conf file again, it now has "1680x1050" as the first resolution in each line, but that doesn't help. I'm guessing I need the driver?
If you have an Intel IGP, you would need 915resolution package AFAIK. Thats a limitation of intel graphics drivers.

---

### Post by Maqz447 on 2007-08-26
So I typed in **ifconfig -a**, this is what I got (I had to write it down by hand as my printer doesn't work with Ubuntu either, but this should be exactly what it said):

lo               Link encap: Local Loopback
                  inet addr: 127.0.0.1   Mask: 255.0.0.0
                  inet 6 addr:  ::1/128   Scope:Host
                  UP LOOPBACK MTU:16436  Metric:1
                  RX packets:2 errors:0 dropped:0 overruns:0 frame:0
                  TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
                  collisions:0 txqueuelen:0
                  RX bytes:100 (100.0b)   TX bytes:100 (100.0b) 




My graphics card is ATI Radeon X1300 Pro.

---

### Post by p_quarles on 2007-08-26
Hmm. It's failing to recognize your NIC at all. I'll look into possible fixes and get back to you.

Meanwhile, here's a guide for installing ATI cards:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by p_quarles on 2007-08-26
Okay, are you *sure *that your system doesn't have an integrated ethernet NIC? According to Dell, this is the default option for the computer you bought:
[http://www.dell.com/content/products/productdetails.aspx/inspndt_53x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/products/productdetails.aspx/inspndt_53x?c=us&cs=19&l=en&s=dhs)

After some searching, I was able to find a thread where it looks like the integrated NIC problem was solved.:
[http://ubuntuforums.org/showthread.php?t=524981](http://ubuntuforums.org/showthread.php?t=524981)

The good stuff is on page 2 of that thread. Let us know how it goes.

---

### Post by Maqz447 on 2007-08-26
Yes, it's an integrated Intel NIC. I tried the suggestions in that thread with regard to the Wake on LAN feature in Vista, but that changed nothing. I was a bit confused about whether I should enable or disable "Wake on LAN" though. So I tried both enabling all the boxes and disabling WoL completely. Neither made a difference. I disconnected the power for half a minute between reboots. 

The LED on my ethernet card is lit, I don't know if that tells anyone anything. It seems that it often isn't when people have similar problems. 

From reading other threads, it seems that this problem is connected with a Windows driver update in some mysterious way (why am I surprised). Others have mentioned "rolling back" the driver in windows - what does that mean and how does one do that? My Windows Vista copy is in Norwegian and I don't know what the proper translation of "roll back" is. I can "deactivate" the driver, but that probably isn't quite the same? I'm guessing this would make Vista go offline. 

"Rolling back"  the Realtek driver has helped others get Ubuntu online, though no one seems to know why...

This is someone's tentative explanation, cut and pasted from this thread:
[http://ubuntuforums.org/showthread.php?t=519864&page=4](http://ubuntuforums.org/showthread.php?t=519864&page=4)

"The problem, I think is that M$ rolled a custom made firmware designed to make the card XP-only and it didn't came down until now. When you updated it made it's thing and rendered your nic useless on *NIX (both Canonical's and Apple's variants) and Vista, it got fixed b/c when you rolled it back you restored the nic to it's original OS-agnostic mode. "

Wouldn't surprise me... this seems to only concern Realtek NICs, though. Mine is Intel.

Edit: and mine works flawlessly with Vista.

---

### Post by p_quarles on 2007-08-26
I could be wrong, but I read the "unplug" part of the thread I linked to as "unplug the ethernet cable." NICs are often designed to do things automatically when a cable is plugged in. Worth a shot, at least.

Some other suggestions:
1) Try going into your BIOS and checking for networking-related options there. It might be a setting that's in there.

2) A perfectly good PCI NIC will set you back all of US$15. It's very likely that you can get the integrated card working after some tweaking, but if you want the easy solution, buying a new card will do the trick.

---

### Post by Maqz447 on 2007-08-27
I took the Ethernet card from my IBM and put it in the Dell, worked right away :) 

How weird that the integrated Intel NIC wasn't even detected, but I'm happy things are working now! (I'm willing to bet this was caused by dual-booting with Vista... I'm only hoping Vista won't screw things up again, I haven't booted it since I inserted the card).

1 down, 2 to go. Now  I need to figure out how to get a 1680 x 1050 resolution. Will try the proprietary ATI driver and report back.

---

### Post by p_quarles on 2007-08-27
I wouldn't worry. I've never heard of anyone having any problems with a PCI NIC. I dual-boot with Vista, as well, and it doesn't cause any problems.From my understanding, the problem you encountered wasn't caused by dual-booting, but by the fact that the integrated network adapter is identified and controlled by some part of the Windows OEM package. If you had tried to install Windows from a store-bought disk, it's possible you would have had the same problem.

---

### Post by Maqz447 on 2007-08-27
Downloaded the driver by clicking System - Administration - Restricted Drivers Manager, rebooted, and now I have 1680 x 1050! That was TOO easy!

Gnome looked kinda ugly before, now it looks much better!  :)

Now I just have to figure out how to get my DVD RW to mount...

(If I could get my printer to work too, I'd format my Vista partition and go Ubuntu only. But it's a Dell Photo 926, and apparently it doesn't work with Linux at all. Maybe Dell will make a driver eventually).

---

### Post by p_quarles on 2007-08-27
A good start would be to make sure it's aware of the hardware. Try the following two commands:
```
ls /dev
```
and look for a line that says "dvdrw@"
```
ls /media
```
There, you should see "cdrom@" "cdrom0" and probably your Vista partition.

---

### Post by Maqz447 on 2007-08-27
I typed ls /dev, found this line:

dvdrw      ptye1  ptytb  ptyz5       tty36  ttyd8  ttyse  ttyy8

ls /media produces:

cdrom  cdrom0

No @ - does that mean anything?

---

### Post by p_quarles on 2007-08-27
No, the missing "@" doesn't mean anything. I just forget that not everyone aliases "ls" to "ls -F." :)

Try this:
```
sudo lshw
```This will list all the hardware recognized by your system.

EDIT: Also, does this happen to be an external USB-based drive?

---

### Post by Maqz447 on 2007-08-27
sudo lshw found this:

 *-cdrom
                description: DVD writer
                product: DVD+-RW TS-H653A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D500
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom

So at least Ubuntu knows it's there.

---

### Post by p_quarles on 2007-08-27
Hmm. Try this:
```
mount /dev/cdrom
```
If that fails to mount the drive (there has to be a disk in it, of course), then please post the output of
```
cat /etc/fstab
```

---

### Post by Maqz447 on 2007-08-27
Looks like the "mount" command fixed it! I just inserted a blank dvd, burned the "experience ubuntu" ogg file to it, and am now playing it from the dvd. What are you, some kind of wizard? Can you make my printer work too? :)

By the way, a new problem has emerged: after downloading the ATI driver, the colours are all wrong when I play the ogg file.  Nelson Mandela's face is blue... Is this a known problem with ATI drivers (I understand they are generally not very good)?

My three initial problems are solved though. Many thanks for your help! It's pretty amazing that I can get this kind of support for an operating system I downloaded for free, by people who aren't paid to help me. The things they say about the Ubuntu community seem to be true.

---

### Post by p_quarles on 2007-08-27
I've never tried to get an ATI card working, so I don't know what to say about the color issue. I, too, have heard that the Linux ATI drivers are sub-optimal. 

About the printer, I have no idea. All I know is that HP printers are very well supported (by HP, no less), and everything else is kinda spotty. 

Glad I could help.

---

### Post by tahitiwibble on 2007-08-27
[QUOTE=The things they say about the Ubuntu community seem to be true.[/QUOTE]

Incredible but **true!** Doesn't it just warm the cockles of your heart. :lolflag:

---

