---
title: "installing on an eMac w/broken Superdrive"
date: 2010-05-19
forum: Apple Hardware Users
---

### Post by loupgarou on 2010-05-19
Hello,

I've done a bit of Googling, looking for answers, but I'm hoping some kind and knowledgeable soul here can help provide a shortcut to knowing ..

1Ghz G4 eMac, 640 megs of RAM, broken Superdrive. Last night, I downloaded the Ubuntu alternative 10.4 ISO image, and attempted unsuccessfully to 'mount' it using Apple's Disk utility.

Google led me to a thread where someone was having a similar problem with an 8.x version of Ubuntu for PPC,  and one of the replies suggested using Toast, which I don't have ..

So, back in Disk Utility, in the left pane, I highlighted the ISO, and instead of trying to mount it, I clicked ''Burn', and, it burned, and verified. Put the resulting CD in an external LaCie CD/DVD burner, attached it to the eMac via firewire, and .. no joy. 

Earlier I had formatted the eMac's HD, thinking that would allow me to use a 'trick' to install Mac OS X 10.5 with a drop-in upgrade DVD, but that didn't work, either, so when I tried to boot from the Ubuntu ISO, I was greeting with that flashing '?' the Apple firmware shows you when it can't find something to boot from.

Main questions - Did I burn the ISO properly? Can it be done with Disk Utility? Can the eMac be booted from the ISO via an external, non-Apple, CD ROM?

Am I missing some important questions?

Thanks in advance. If you come to Austin, I owe you a taco.

Beau B.

---

### Post by loupgarou on 2010-05-19
Would the Live CD ISO be different, in terms of being more likely to boot the eMac externally?

---

### Post by linuxopjemac on 2010-05-19
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You also might like to try USB, you will find info on mac.linux.be

---

### Post by loupgarou on 2010-05-19
Thank you - that link verifies that the disc was burned properly; that, and the fact that if I turn on the Mac with the option key pressed in and the external cd ROM attached, I see a firewire icon and a penguin on a cd icon - but no booting - 

Maybe it can't be booted/installed from an external ROM?

Oh, and PPC Macs can't be booted from USB as far as I know

---

### Post by oswaldkelso on 2010-05-19
> **loupgarou said:**
> 

Oh, and PPC Macs can't be booted from USB as far as I know

That only applies to usb one Macs. Usb2 can boot on Macs.

---

### Post by loupgarou on 2010-05-19
> **oswaldkelso said:**
> That only applies to usb one Macs. Usb2 can boot on Macs.

Were there PPC Macs with USB 2.x?

This one has three 1.1 USB ports, and 2 firewire 400

---

### Post by oswaldkelso on 2010-05-19
Later emacs (after 1ghz) were usb2. G5's also

---

### Post by loupgarou on 2010-05-20
Can the installer CD be booted from an external firewire drive?

---

### Post by linuxopjemac on 2010-05-20
That's certainly not true. You can install from USB, also 1.1. Just dd an iso to the USB and boot from it. I did it on a Pismo with USB 1.1.

The following link is for Linux Mint PPC, but it equally applies to any other PPC Linux distribution:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc#1](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc#1)

---

### Post by oswaldkelso on 2010-05-20
> **linuxopjemac said:**
> That's certainly not true. You can install from USB, also 1.1. Just dd an iso to the USB and boot from it. I did it on a Pismo with USB 1.1.

The following link is for Linux Mint PPC, but it equally applies to any other PPC Linux distribution:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc#1](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc#1)

I stand corrected. I've never done it as all my PPC machines are USB.1 I'll give it a go now cheers.

---

### Post by loupgarou on 2010-05-20
Not knowing any better, why would it (this G4 eMac) be more likely to boot Ubuntu via USB 1.1 than Firewire?

It won't boot the Mac OS via USB 1.1 .. as far as I know

---

### Post by linuxopjemac on 2010-05-20
they are both working, although firewire should always work. But really, try to dd the iso onto a USB drive and you will be astonished.

---

### Post by tgalati4 on 2010-05-20
It is my understanding that the Superdrives only take older 650 MB CD-R disks.  Most of today's CD-R's are 700 MB and for some reason the Superdrive fails to read them.  So unless you can find some unused 650 MB CD-R's at a garage sale, you are going to have to get much more creative.

---

### Post by loupgarou on 2010-05-20
I guess I'm not being clear in my writing.

The EXternal DVD/CD ROM drive I'm using (remember, previous poster, that the internal Superdrive in this thread is broken) has both Firewire and USB ports.

Trying to boot the eMac from either flavor of port, with the Ubuntu 10 for PPC alternate iso burned CD inserted, is not working.

I _can_ boot the eMac, connected to that same external DVD ROM, via Firewire, using an OS X 10.5 drop-in, upgrade DVD that came with a newer iMac, and would have installed that, except for a couple of reasons, like, the internal hard drive is blank, and the DVD is expecting to see Mac OS X 10.4 installed, AND that the 'trick' I found to get around that problem doesn't work with an external storage device attached.

Is the suggestion to 'dd' the ISO image to an external hard drive?

---

### Post by linuxopjemac on 2010-05-21
I have no experience with external DVD drives. My experience with DVD drives on a G3 Pismo is that it can't read Linux at all (it can read OSX though). I had to put in a CDROM drive to be able to start from a Linux CD. The drivers are probably read from the CD/DVD OSX installation disc.

Just take a USB stick and do as I said, it will work.

---

### Post by loupgarou on 2010-05-21
I'm probably just too stupid to be able to do this. For one, I don't get why this Mac would boot Ubuntu via USB 1.1 when it can't boot it's own, native OS that way.

For another thing, I don't get why it would make a difference putting the ISO on a USB stick versus having it on a CD.

---

### Post by linuxopjemac on 2010-05-21
> For another thing, I don't get why it would make a difference putting the ISO on a USB stick versus having it on a CD. 

firmware maybe ?

---

### Post by B_Free on 2010-05-21
Go to disk utility. or pop a cd in your drive you are going to burn it with, open with disc utility. At the top of disc utility it says images. In the drop-down, select burn. Find the ISO image you downloaded, and select it. Burn at no more than 8X. Let it verify. 

You can't just burn the ISO. That would be just copying the ISO. 

Hope that was the problem.

---

### Post by loupgarou on 2010-05-21
> **B_Free said:**
> Go to disk utility. or pop a cd in your drive you are going to burn it with, open with disc utility. At the top of disc utility it says images. In the drop-down, select burn. Find the ISO image you downloaded, and select it. Burn at no more than 8X. Let it verify. 

You can't just burn the ISO. That would be just copying the ISO. 

Hope that was the problem.

This may well be the/a problem; Disk Utility wouldn't 'mount' the ISO (it says "no mountable filesystems"), but it would burn it.

Before I posted here, I Googled around and saw a thread where someone, somewhere, said that they couldn't mount Ubuntu 9.x w/Disk Utility, and the helpful reply there was to use Toast, which I don't have - think this was in my first post here..

---

### Post by linuxopjemac on 2010-05-22
for burning isos you may follow the [Ubuntu wiki]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by B_Free on 2010-05-22
I was totally confused when I first started. There are several places you can burn a file. If you downloaded the ISO to your downloads folder or your desktop, open disc utility and go to _images_ at the very top of the screen (not the burn within the window), and select burn. Find the ISO where ever it is and select it. I promise this will get you a bootable copy. In fact, once you finish, put the CD back in your CD drive. The ISO will have changed to whatever version Ubuntu you downloaded. Promise!

---

### Post by loupgarou on 2010-05-23
> **B_Free said:**
> I was totally confused when I first started. There are several places you can burn a file. If you downloaded the ISO to your downloads folder or your desktop, open disc utility and go to _images_ at the very top of the screen (not the burn within the window), and select burn. Find the ISO where ever it is and select it. I promise this will get you a bootable copy. In fact, once you finish, put the CD back in your CD drive. The ISO will have changed to whatever version Ubuntu you downloaded. Promise!

Not to be repetitive, but to try to avoid burning another coaster, let me describe again what happened.

I dl'ed the 10.x PPC alternative ISO. Disk Utility wouldn't 'mount' it, complaining about the lack of a file system. In the left pane of Disk Utility, the icon that appeared for the dl is the generic disk image icon; a vertically oriented white rectangular shape with the upper right corner turned down, that contains a smaller, grey rec.

OK. Couldn't mount it, but if I just highlighted it with a single click, and hit burn, it burned and verified successfully. When I attempted to boot from it via external firewire connected DVD/CD burner, the eMac firmware showed me an icon with a penguin for a boot device, but wouldn't boot.

Now, I've dl'ed the desktop ISO. After 'barking', Disk Utility WILL mount this image, and so, in the left pane, I have that disk image icon, and a second icon, the white, mounted, virtual disk icon.

You're saying I should be burning the image of the mounted disk, correct?

---

### Post by B_Free on 2010-05-25
NO. I just put together a PDF for you.
I am not sure how to attach it to this post.
I'll figure something.

---

### Post by loupgarou on 2010-05-25
> **B_Free said:**
> NO. I just put together a PDF for you.
I am not sure how to attach it to this post.
I'll figure something.

Try this.

[http://docs.google.com/fileview?id=0B43iPSRv0tOyODYxYzk5ZDItODU2OS00MDZmLTlhZTktMmVlYmQzYmE1YTI3&hl=en](http://docs.google.com/fileview?id=0B43iPSRv0tOyODYxYzk5ZDItODU2OS00MDZmLTlhZTktMmVlYmQzYmE1YTI3&hl=en)

Thanks for doing what you did, but I was not able to access the document.

You say, "NO", but there's only 2 possible different icons for me to choose from to burn in the Disk Utility pane, and I've already burned one, and just asked if I should burn the other ...

The one that burned, the unmounted 10.x alternative ISO, did show up via the eMac's booting firmware as a penguin icon on a CD. In this thread, I've been told that I burned this improperly.

Now, you're saying to choose the icon of the mounted 10.x desktop iSO to burn would be wrong as well.

---

### Post by B_Free on 2010-05-25
I know it is confusing. When I started out it took 3 months before I figured it out. But what I showed you in the PDF is the actual steps I took this morning to burn yet another copy of Ubuntu. Ignore everything so far. Let's go back to the beginning. You went to the releases site for Ubuntu PPC. You download the ISO. This is where you follow the instructions in the PDF. So, what ever file you downloaded (the very first one) you follow the PDF instructions. Don't even look at anything else. No other burnt files, or what other things you have on your desktop. Just the first file you downloaded.

This will get you a bootable copy. We will deal with the Superdrive later.

---

