---
title: "Macpro 4,1 Quad core Intel Xeon"
date: 2009-12-08
forum: Apple Hardware Users
---

### Post by johan-hake on 2009-12-08
Hello!

I am a long time (K)Ubuntu user who just got on of the latest MacPro from my boss. I would very much like to run (K)Ubuntu on it, but I am stucked.

I have installed rEFIt, which detects any live cd and I am able to boot from it. However both Ubuntu and Kubuntu live cd just give me the black screen after a while (say 1 minute)

Using bootcamp I have dedicated a partition on the hard drive to install (K)Ubuntu on it, but when I try this from the Ubuntu cd I ran into the black screen as described above.

I have tried to look into forum posts but I have not seen this particular problem, especialy with a new Macpro

I would be glad for any pointers!

Johan

---

### Post by linuxopjemac on 2009-12-08
Some people had luck with passing the kernel argument acpi=off at boot time. Search the forum. You can try that option.

---

### Post by johan-hake on 2009-12-08
Yeah, I saw some of those posts, and I did try to set that option with no luck...

Thanks anyway!

Johan

---

### Post by johan-hake on 2009-12-08
Minor update:
* I have now tried both 32 and 64 bits versions, still with no luck. 
* I have verified that the images are burned correctly.
* I have acpi=off _and_ nolapic

with the last options I get the message:

  "Unable to find a medium containing a live file system"

and I come into a BusyBox, (initramfs) shell, with limited functionality. If I only hook off for acpi=off and not the nolapic option or any other combination of options I do not get the BusyBox shell, but rather a black screen.

Any suggestions?

Johan

---

### Post by linuxopjemac on 2009-12-09
Maybe you can try a non-graphical installation with the alternate CD and work your way up from there by manually setting X.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by johan-hake on 2009-12-09
Ok, the alternate CD installer got me further! Thanks for the pointer!

It seems that the actual problem was connected to some CD driver that was not detected. I was not able to get into a usable shell to issue the command modprobe ide-scsi. Probably me not knowing how Ctr+Alt+ F2 did not work. But when I choose the expert install on the alternate CD I got past the step where he complained about the drivers.

So I'll report any progress, beyond this point later.

Johan

---

### Post by linuxopjemac on 2009-12-10
I am very interested to hear from you soon.

---

### Post by johan-hake on 2009-12-11
Well, it didn't go too well after all.

When I got through the first bump with the cd drive, I actually got to the point where I could repartion my harddrive. However it was too late so I thought I proceed another day. 

When I tried again, he couldn't detect my cd drive. I googled, and tried different things, like modprobe ide-scsi but no luck. I got a bit further by using an external cd rom, but after this he couldn't detect my hard drive! So something fishy is going on.

I could not figure out why I managed to come further the previous time.

Any suggestions are really appreciated...

Johan

---

### Post by linuxopjemac on 2009-12-11
interesting link:
[http://wiki.debian.org/DebianOnIntelMacPro](http://wiki.debian.org/DebianOnIntelMacPro)

---

### Post by linuxopjemac on 2009-12-13
[http://ubuntuforums.org/showthread.php?t=1352933](http://ubuntuforums.org/showthread.php?t=1352933)

---

### Post by johan-hake on 2009-12-16
Thanks for all the hints!

Unfortunately I just had to abandon the project, as the amount of time I can spend on this is limited. I just couldn't get my MacPro to recognize either the CD drive or the hard drive. Using external CD drives I came a but further but I cannot do anything when my hard drive or hard drive driver, are not detected.

So for now I go with fink and other tweaks to make my MacPro usable for science!

Johan

---

### Post by linuxopjemac on 2009-12-16
maybe this guy did it:
[http://blog.christophersmart.com/2009/11/27/linux-on-mac-pro-with-multiple-drives/](http://blog.christophersmart.com/2009/11/27/linux-on-mac-pro-with-multiple-drives/)

did you try this link I gave you earlier?
[http://wiki.debian.org/DebianOnIntelMacPro](http://wiki.debian.org/DebianOnIntelMacPro)

---

### Post by johan-hake on 2009-12-16
> **linuxopjemac said:**
> maybe this guy did it:
[http://blog.christophersmart.com/2009/11/27/linux-on-mac-pro-with-multiple-drives/](http://blog.christophersmart.com/2009/11/27/linux-on-mac-pro-with-multiple-drives/)

did you try this link I gave you earlier?
[http://wiki.debian.org/DebianOnIntelMacPro](http://wiki.debian.org/DebianOnIntelMacPro)

the first one deals with multiple hard drives and fedora. It seems that the Linux installation program actually recogninzed his hardrives during installation. When he then booted he got problems with rEFIt. I cannot finish installation because my harddrive is not recognized during the installation.

The second one was quite old, using a kernel from some years ago. I could probably upgrade this after the installation, or just use a newer one, but I really wanted to get (K)ubuntu on it. Not a plain debian.

But thanks anyway!

Johan

---

