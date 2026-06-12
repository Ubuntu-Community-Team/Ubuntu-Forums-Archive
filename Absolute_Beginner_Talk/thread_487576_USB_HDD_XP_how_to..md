---
title: "USB HDD XP how to."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-06-29
Hello again. Another problem probably easily fixed. 
For your info, I have no need for XP at all except to run my accounting package(QuickInvoice) and I loaded XP including the invoicing package onto an old hd(8.4 gig) and put that drive into an external usb caddy. That was done on a different box from the one I'm using now.
Apparently Windows might only run on the motherboard it was installed with..??
XP was formatted NTFS or whatever it is, not FAT. 
I BOISed USB HDD as first boot option, but I still get Ubuntu (6.10) by default.
The external hd shows up on Desktop, and I can open up all sorts of stuff, basically a complete rundown of the XP install, and there's lots of it there!
I simply don't know what to do next...!
I read somewhere that for an external usb hd to work, it has to be bigger than the ide hd in the box.(80 gig ide and 8.4 gig external in my case) Is that true?
I have read a lot of stuff about GRUB recently but it's Chinese to me. 
Basically, without swapping from box to box, it would be nice to boot into XP once a week to do my invoicing off the usb HD. 
As I said, the gadget is recognised and the files are accessible but HOW?
Cheers to all, Mike.
PS. Lots of questions. Sorry.

---

### Post by MichaelSM on 2007-06-29
Um, followed some.links about NTFS 2/3g and now I have no Desktop external HDD icon. My mistake. Can I get it back?
Have a good weekend.
Mike.
PS. By the way, if NTFS is an issue, then I'll simply re-format and reload XP using FAT on the little HD.. Will that help?

---

### Post by phr0ze on 2007-06-29
I've never tried XP on an external harddrive but many of those things you have heard are not true. If you only need one or two things out of XP have you thought of KVM or Qemu? These are virtual computers that let you install XP on them. XP will run slower than a regular install, but there will be no software issues and back-ups are super easy.

---

### Post by MichaelSM on 2007-06-29
Thanks for the reply phrOze. I don't know what KVM or Qemu are, or what they do, but I'll look them up. Maybe it's too hard to do: all the threads I've followed talk about a Windows ide with Ubuntu on the external HDD, but that isn't my case. 
I appreciate your reply.
Michael.
PS. I'm still amazed by the web. 'Columbia MD.' Where's that? Is it like Washington DC? Aha. Maybe Columbia, Maryland.
Don't worry about it.All the best.

---

### Post by Depressed Man on 2007-06-29
It's a county in Howard county I believe. I think I went to the Merriweather Post Pavilion there for a concert. Nice place. Though I'm a Montgomery County guy. ;)

---

### Post by MichaelSM on 2007-06-29
Oh, Howard County? Nice to hear. Check my geography so hi to Montgomery Alabama. What a wonderful world. Betcha you can't find Maldon Australia in your biological RAM. 
Cheers, Mike.

---

### Post by phr0ze on 2007-06-29
Decided to point out some things...

> **MichaelSM said:**
> Apparently Windows might only run on the motherboard it was installed with..??
XP SP2 is better with this. It really depends on how different the motherboards are. But I've seen many cases where there have been no issues. XP may ask you to reactivate if its a legit copy.

> **MichaelSM said:**
> I BOISed USB HDD as first boot option, but I still get Ubuntu (6.10) by default.
Your BIOS may not be detecting the drive, you definitely want to put the drive on main USB connectors. Try other sets as well. Finally, XP itself may not like this if the USB controller chip does not have a proper driver built into XP.


> **MichaelSM said:**
> I read somewhere that for an external usb hd to work, it has to be bigger than the ide hd in the box.(80 gig ide and 8.4 gig external in my case) Is that true?

There is no reason why this should be true.

---

### Post by phr0ze on 2007-06-29
here you go. 
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

---

### Post by vinnn on 2007-06-29
Have you not tried running QuickInvoice with Wine? Wine is a windows API that runs on Linux.
You can run many Windows applications on Linux with Wine.
To install Wine just...```
sudo apt-get install wine
```

On the subject of virtualisation...
If Qemu, KVM or Xen seems a little daunting because it involves command line, try [VirtualBox]("http://www.virtualbox.org/wiki/Downloads"), it's faster than Qemu and easier to install & use. [www.virtualbox.org]("http://www.virtualbox.org/wiki/Downloads")
Here's a shot of the current VMs I have installed in VirtualBox on my Ubuntu desktop...

     [IMG]http://www.nethomehelp.co.uk/TEMP/VirtualBox.png[/IMG]

---

### Post by chamberlain2006 on 2007-06-29
Here's a thought, why not add an entry to GRUB?

---

