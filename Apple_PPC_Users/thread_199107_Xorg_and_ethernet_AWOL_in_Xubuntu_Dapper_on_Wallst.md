---
title: "Xorg and ethernet AWOL in Xubuntu Dapper on Wallstreet"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by RoadTripDK on 2006-06-18
I just completed a successful install of Xubuntu Dapper (thanks to everyone that went before and took time to post info) on my Wally. During install, the ethernet failed to load properly, but I marched on and completed the install. I was expecting to get the ethernet sorted when I booted into Dapper, but much to my surprise, I could not boot into a GUI, but only text. There were no errors with xorg durring install. I am still a relative newbie to Linux, so this is about the time I need to yell "help". 

My BootX is set as follows:

root=/dev/hda9 video=atyfb:vmode:14,cmode:8,mclk:71

Cheers

---

### Post by nkbj on 2006-06-19
To get ethernet working try adding these two lines to the top of /etc/modules```
genrtc
bmac
```

You can try to reconfigure your GUI by running 'sudo dpkg-reconfigure xserver-xorg' in a text console.

Update: [https://wiki.ubuntu.com/Installation/OldWorldMacs](https://wiki.ubuntu.com/Installation/OldWorldMacs) has an entry about the Wallstreet.

---

### Post by RoadTripDK on 2006-06-19
What command line text program is used in Xubuntu? I tried 'sudo nano /etc/modules', 'sudo nano /etc/fstab' and just 'sudo nano' but no luck. I have visited the Xubuntu site, but I can't find any documentation of what cl text program is used there. Only GUI text programs were mentioned.

---

### Post by nkbj on 2006-06-19
Probably vi.

---

### Post by RoadTripDK on 2006-06-19
OK, Vim was installed, so I used that. I added the two lines to /etc/modules rebooted and then tried an 'apt-get update', but all I got was errors, so I don't think the ethernet is working yet.

---

### Post by RoadTripDK on 2006-06-19
BTW, anyone out there that has the necessary specs on the Wallstreet (II), otherwise known as the PDQ? I would like to run 'sudo dpkg-reconfigure xserver-xorg', but I only have the specs from the Mactracker program (OS X). I am told that my Wally has (I purchased it last week) 266 MHz processor, a 14.1" active matrix screen and an ATI Rage LT or Rage Pro LT graphics card. I know that 'sudo dpkg-reconfigure xserver-xorg' will ask questions about the screen, keyboard, etc., but I am not sure what to reply (except the obvious, like that I have a US keyboard). Not even sure about the modem, ethernet or SCSI specs.

---

### Post by Rob_Frohne on 2006-07-09
I had similar experiences when installing Dapper on my Wallstreet.  It thought I had firewire ethernet, and I don't have firewire at all on that powerbook.  It didn't detect the bmac ethernet.  It was extremely slow installing, though it sped up when I removed the Wavelan Silver wireless card.  It took basically all night to do, because something was timing out or something.  Breezy installed in an hour or two originally.  

I was reinstalling because I had hosed my previous upgrade of Breezy, which worked much better than Dapper intstalled fresh.  I had not changed the kernel from the one I used with Breezy, but when I tried to use the kernel for Dapper, it crashed.  Now I am about to go back to Breezy and upgrade from that again.   The Breezy upgrade had wireless and bmac ethernet support working, and felt pretty decent.  I didn't even realize that I wasn't running the "correct" kernel until I had used it for about a month. 

Another problem I noted was that with the install I got from the Dapper Alternate Install CD, the mount command didn't know about hfs or hfsplus, so I couldn't easily copy the vmlinux and ramdisk over the the OS 9 partition for BootX.  

I keep reading things about Dapper not supporting "OldWorld" machines.  I suspect this means we may need to start supporting this ourselves, by recompiling the kernel with the correct options again.  I guess I need to do this if I'm going to run MacOnLinux anyway.

I recommend the Breezy install and then upgrade route.  It was much much better than the direct installation of Dapper.

Rob

---

