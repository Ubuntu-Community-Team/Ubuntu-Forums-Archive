---
title: "Total installation failure"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by RogerD on 2007-03-04
Hi

I've just had a new PC built. Here's the spec:
Athlon 3200
1048MB DDR2 667MHz
Asus M2NPV-VM mother board
160GB SATA HD

A couple of days ago I tried to intall 6.06 using the liveCD. The liveCD bit worked fine, and I was able to open and use applications like OpenOffice Writer without any problems. Expecting that all would be well, I started the install. About 80% of the way through, I got the message"We're sorry, but the installation has failed" - never had that before. I had another go, but got the same result. I thought, maybe there was a fault on the installation CD, so I tried the DVD that comes with the book "Ubuntu Unleashed". This simply produced the message:

GRUB Loading stage 1.5
GRUB loading, please wait..
Error 15

Checking the device sequence at the boot stage, I found that the HD had priority over my DVD drive. It seemed likely that I'd got a partial installation with a faulty GRUB installation on the HD. I therefore changed the set-up to give my DVD priority over the HD. This meant, at least, that I could reliably start the liveCD.

I've filed a bug report, as requested, and been seeking help via the forum. Following suggestions, I've recently  tried the 6.06 alternative CD, opting to erase the entire disk. The installation seemed to be going 'great guns', but failed at the copying files stage. I  got the message:

'Configuring wvdial Installation step failed'

I then opted for "Finish installation", thinking this was the same as 'abort', and was asked to install GRUB. This didn' work, and I got the message:

"The grub package failed to install into target"

A second attempt produced very similar results

I've also  tried the 6.10 liveCD, but at  'creating user' at the copying files stage, I get another installer crashes message.

It doesn't seem worth reporting this crash, all these installers can't be faulty, can they?
The most likely explanation is that there's something wrong with my new machine. Can someone please give me some ideas, so that I can either fix it myself, or go back the  guys who built my machine (not Linux specialists) and tell them what to do.

Incidently, I haven't got my machine connected to the Internet during these installation attempts, but I can't believe this is the problem.

All help much appreciated.

Best regards

Roger D

---

### Post by Kateikyoushi on 2007-03-04
I would recommend to give the alternate CD a try it installs in text mode and has a higher chance of finishing the install, you could test your memory with the live disc as well.
What is your video adapter ?

---

### Post by jvc26 on 2007-03-04
Have you run the 'disk check' utility on the cd/dvd - it would be odd for both cds to be nonfunctional but its not unheard of so I'd give it a try.
Il

---

### Post by RogerD on 2007-03-04
Hi

You said

I would recommend to give the alternate CD a try it installs in text mode and has a higher chance of finishing the install

I've done this, and it still fails

You could test your memory with the live disc as well.

How do I test my memory?


What is your video adapter ?

My motherboard has a NIVDA GeForce GeForce 6510 graphics processor.

Incidently, I've checked all the installation CD, and they're OK

Best regards

Roger D

---

### Post by confused57 on 2007-03-04
Hello RogerD,
   Here's another thread with someone who's having problems installing grub to their mbr:
[http://www.ubuntuforums.org/showthread.php?t=375467](http://www.ubuntuforums.org/showthread.php?t=375467)

You might be able to get some information from this thread that may help you...for example, you might want to try installing grub to the root partition & using GAG to "attempt" to boot into Ubuntu...this may help determine if there might be a setting in bios that's preventing grub from installing on your mbr.  Theres' also some excellent information from Herman.

---

### Post by RogerD on 2007-03-04
Hi

Oh dear! This all sounds terrrible complicated, and a bit hopeless. There must be some basic reason while the liveCD is OK, but the installation keeps failing part-way through the install. I just don't know what to do next. As I think you know, from my previous post, my attempt to re-install grub using [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) ended in failure, with an "Error 15: File not found" message.

Can you think of anything else I should try, or something helpful I can say to the guys who built my machine?

Roger D

---

### Post by confused57 on 2007-03-04
> **RogerD said:**
> Hi

Oh dear! This all sounds terrrible complicated, and a bit hopeless. There must be some basic reason while the liveCD is OK, but the installation keeps failing part-way through the install. I just don't know what to do next. As I think you know, from my previous post, my attempt to re-install grub using [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) ended in failure, with an "Error 15: File not found" message.

Can you think of anything else I should try, or something helpful I can say to the guys who built my machine?

Roger D
You might want to ask your pc builders if your mobo has the latest bios update:
[http://forums.debian.net/viewtopic.php?t=11453&sid=b9921c4b73d0ac70646691cf793bb066](http://forums.debian.net/viewtopic.php?t=11453&sid=b9921c4b73d0ac70646691cf793bb066)

There might be some boot options you could pass to the kernel, when you boot up the live cd...for example, I think you press "F6" at bootup of the live cd & add something like:
acpi=off, noirq, noapic, etc...I've never had to do this myself, so I can't give you any specific boot parameters, I'll search around in the forum & see if I can find anything.  Yes, it might get a little complicated.  You're able to boot the live cd/dvd ok, just having problems installing, so you can probably forget this suggestion.

I would think that your hard drive was checked for errors or bad sectors, when it was installed...might be another thing to mention.

Might be a setting in bios that could be changed that would help...

---

### Post by RogerD on 2007-03-04
Many thanks. That's a couple of good ideas I can mention to the builders. If you can think of anything else, please let me know

---

### Post by confused57 on 2007-03-04
> **RogerD said:**
> Many thanks. That's a couple of good ideas I can mention to the builders. If you can think of anything else, please let me know

I read back over your other thread & the output of "sudo fdisk -l" showed a 32 mb sdb...is this a USB device...if it is, sometimes USB devices can cause problems, although usually just bootup problems of the live cd...shouldn't really cause installation problems, I don't know.

There could possibly be a faulty piece of hardware, the hard drive, connectors or connections, etc, that the pc builders can check out or something in bios that needs enabled,etc...hard drive manufacturers, such as Seagate, have utilities or floppies to check a new hard drive.
Good Luck.

---

### Post by RogerD on 2007-03-04
Thanks for your interest. The 32 mb sdb is a USB memory stick. I've been using it to collect log files as I've been trying to crack this. It hasn't been in while I've been trying to do the installation.

---

### Post by RogerD on 2007-03-04
I've just noticed something. The motherboard has four DDR2 memory sockets. I specified 1GB. I've just read that with DDR2, you have to install matched RAM modules in pairs, but when I took the side off my PC the other day, I noticed only one memory module. Could this be significant?

---

### Post by confused57 on 2007-03-04
> **RogerD said:**
> I've just noticed something. The motherboard has four DDR2 memory sockets. I specified 1GB. I've just read that with DDR2, you have to install matched RAM modules in pairs, but when I took the side off my PC the other day, I noticed only one memory module. Could this be significant?
I'm not sure, but I believe that just refers to having 2 memory modules set up in dual-channel mode, which is faster than 2 separate modules without it...they have to be matching modules to actually utilize dual-channel, your mobo should have specifications of which slots they'd need to be inserted, for example the 1st & 3rd slots.
I could be wrong though.

---

### Post by RogerD on 2007-03-04
Thanks for all your help. I think my best bet is to take the machine back to the builders and tell them to check the memory and the HD, and update the bios. Who knows?

---

