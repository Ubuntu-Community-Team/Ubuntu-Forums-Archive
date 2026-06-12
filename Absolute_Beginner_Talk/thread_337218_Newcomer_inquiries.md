---
title: "Newcomer inquiries"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Arcturus on 2007-01-12
I'm growing more tired of windows the more I use it. I've been using Windows for years now and need a break from all the nonsense.

I've watched several very helpful and descriptive video tutorials which show how to install ubuntu. I've downloaded it so I already have it, for when I decide to make the leap.

I've one concern though. When I restarted my computer, after inserting the ubuntu disc in my tray and in the tower and my pc boots up, will I have the option to load the disc or just start with windows? Also, I don't want to remove windows, I just want to install ubuntu on part of my hard disc drive. Once I install ubuntu, when I restart, will I have the option to start with ubuntu or windows?

This is the only real concerns I have right now. I appreciate any help at all. Thanks for viewing, I hope to be a total linux freak after a while.;)

---

### Post by jas0 on 2007-01-12
Does the hard drive which has Windows on it have any free space? If it does, then you're in business. If it's not, the easiest way to get Ubuntu and keep Windows is to just get a second hard drive and install Ubuntu on it.

Let me know which situation you're in and I'll guide you further.

---

### Post by netadptr0719 on 2007-01-12
You will just have to go into your bios or simply hit the button to change you boot device during load up to boot from the CD. Once you install, yes, you will be able to boot to both windows and linux, it will install a boot loader called GRUB that will allow you to chose between which installs you would like to boot

---

### Post by Arcturus on 2007-01-12
The hard disc drive that windows is installed on is 160gb and about 70% of that is free.

Which key do I hit and when do I hit it during a boot up?

Thanks for the quick replies!

---

### Post by netadptr0719 on 2007-01-12
Usualy when your computer boots up there is a tip at the bottom saying stuff like 
hit [del] for set up or hit [**] for boot manager.
If you can not find that one you can go into your bios (set up) and under power/boot you can manually change what order you computer looks for boot devices.

Hope that helps.

---

### Post by bodhi.zazen on 2007-01-12
> **Arcturus said:**
> I'm growing more tired of windows the more I use it. I've been using Windows for years now and need a break from all the nonsense.

Welcome to Ubuntu :)

to install Ubuntu, first defragment your HD (from windows), back up any critical data, and then follow this:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Let's see how deep the rabbit hole is .....

---

### Post by Coop on 2007-01-12
Hello Arcturus

I dont remember what the Ubuntu CD is like because I have the Ubuntu DVD,but if you have the DVD,yes when you insert the disc and reboot your computer you will have the option to boot Windows or load the Ubuntu disc.

And yes,you can install Ubuntu and any other Linux distribution along with Windows on the same computer.
If you have only 1 hard disk,then you need to partition the hard disk and create an emty partition for Ubuntu to install itself on.
If you are familiar with partitioning in Windows then this'll be easy.

Also,to make Ubuntu play most multimedia formats,look at this page:[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Regards Coop

---

### Post by Arcturus on 2007-01-12
Thanks a lot everyone. You all have been more than helpful. On any other forums, I'd have to wait at least a day for a reply. :P Thanks again. I can handle things from here on in. :)

---

### Post by Arcturus on 2007-01-12
Sorry for the double post, but I've ran into a bump in the road.

I edited BIOS to boot from the CDROM and saved, rebooted and I was given the open to start windows normally, choose os option and the rest you all probably know. What did I do wrong, or what should I be doing?

Edit: Never mind. I've realized what I did wrong, I burned it with the windows burning tools. Only burns as data and not the image. *Slaps forehead*

---

### Post by jas0 on 2007-01-12
It seems like you either don't have the ISO burned properly, your CD-Rom doesn't work or that you didn't set the BIOS to boot from the CDROM as the first device.

Make sure that you can read the CD from your Windows installation and double check the priority of the CDROM in the boot process.

---

### Post by Arcturus on 2007-01-12
I've followed exactly what this tutorial tells me to do: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

When I'm using CDBurnerXP Pro, it says the disc I've loaded isn't empty. I've opened another blank cd just to make sure and it says the same thing. Any ideas?

Edit: I know what's wrong now. I downloaded the CD iso isn't of the DVD iso. Does anyone have the dvd iso as a torrent?

---

### Post by jas0 on 2007-01-12
Try going back into your BIOS and disabling booting from anything else but your CD-ROM. This way you'll get a better idea of what may be wrong.

---

