---
title: "G3 PowerMac wont boot"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by metroidnemesis13 on 2008-05-19
I installed Ubuntu 6.10 on a hard drive that had previously had no operating system on it, and the installation went well.  After it installed the software and base, it asked to restart, and ejected the disc.  After it restarted, it came to the Apple logo with a folder on it, and I couldn't get any further with it.  Please help.   I like Linux a lot!

---

### Post by stream303 on 2008-05-19
Which powermac do you have?
[http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html](http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html)

Possible things to check:

How big is that new hard drive?  You may be limited to 128gb partition (make it 125gb to be safe) unless someone has upgraded the firmware.  (You can always use the extra space as a data partition for other partitioning options, but boot and root have to exist under 125 gb...)

When the new drive was installed, did you use "cable select" or "master" for the jumper pins?  Most macs use cable-select for the primary, but I have heard of weird cases where they used master instead.

6.10 is kind of old - I'd suggest at least Feisty 7.04 with the "alternate" installer:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by Gondor81 on 2008-05-19
I too am running on a Powermac G3 (Blue and White), but I found it best if I installed off the Hardy Alternative disc.  Make sure you install from a CD-R.  The best thing I found was to let the system use the entire disk and format the entire disk.  It installed fine once I had that figured out.  Stream303 helped me out during the install make sure you keep us up to date as to your progress so we can help where needed and maybe steer you away from some of the pitfalls.  ;)

---

### Post by avtolle on 2008-05-20
> **Gondor81 said:**
> I too am running on a Powermac G3 (Blue and White), but I found it best if I installed off the Hardy Alternative disc.  Make sure you install from a CD-R.  The best thing I found was to let the system use the entire disk and format the entire disk.  It installed fine once I had that figured out.  Stream303 helped me out during the install make sure you keep us up to date as to your progress so we can help where needed and maybe steer you away from some of the pitfalls.  ;)
+1, with this additional piece of information: when burning the CD-R, be sure to burn at a low speed (4x works best for me), and use a "name brand" CD-R. Some suggest that a "music CD-R" be used, but I've not found that to be necessary, so long as I'm using good quality media.

---

### Post by metroidnemesis13 on 2008-05-21
Wait... on the download section of Ubuntu's website, doesn't it say that they no longer support PowerPCs, and that the latest version that works is v. 6?

"Note to PowerPC (PPC) users: The PowerPC platform of computers is not supported by the newest versions of Ubuntu. However Ubuntu 6.06 is still supported and available for your machine. Please use the link above to view the complete list of download locations to choose a location near you."

(at the bottom of [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) )

---

### Post by frog_pilot on 2008-05-21
[download hardy here]("http://cdimages.ubuntu.com/ports/releases/hardy/release/") and ignore this hoax from the download section.

---

### Post by metroidnemesis13 on 2008-05-21
I've already started downloading it... but seriously, someone should change that... its misleading and pointless...

---

### Post by avtolle on 2008-05-21
I believe that "no longer supports" language refers to official Canonical commercial support. Yes, ppc versions are still being prepared and released, but it is up to us in the community to help each other. It would be great if there was "official support", but strictly from a business perspective, the ppc numbers are not growing, and thus there is a static and likely diminishing pool of users who might be willing to pay for commercial support.

Rant over. 

I hope and trust that you are downloading the alternative iso, as it seems to work best for our hardware. Good luck.

---

### Post by metroidnemesis13 on 2008-05-31
All right guys,

I went ahead and downloaded the Alternate CD of Ubuntu 8.04 for PowerPC users, and it still gives me the same problem.  I changed the hard drive's jumper to master (it was a slave) and it still gives me the Mac logo and a question mark.  I figure this is something really simple and I'm overlooking it.  I'm almost 100% sure that its not the install, and there's something that's not booting.  Help me :o...

Thanks.

---

### Post by avtolle on 2008-05-31
Did you change the jumper before or after the installation? May be a dumb question, but I just had to ask. :-) If it was after the installation, yaboot might be looking in the wrong place for the bootable partition. Just a wild guess on my part...

Edit: take a look at /etc/yaboot.conf to ascertain where yaboot is expecting the boot partition to be. Just to clarify to what I was referring earlier.

---

### Post by metroidnemesis13 on 2008-05-31
Well, I tried to boot it first as a slave, and then as a master, so it really wouldn't matter I don't think because neither one booted properly.  I'm not a Mac user and I'm new to Macs.  Is there a way to access the bios with a combo of keys or something?  Maybe I could change some settings.

---

### Post by hpp3 on 2008-05-31
Reboot and hold down the keys Option-Apple-P-R until you hear the startup noise twice to clear the firmware RAM. 
That should let you boot to your Mac disk normally.
Now, if you have installed Linux correctly, open the firmware terminal by holding down the keys Option-Apple-O-F as it boots. 
From there, type 
```
boot linux
```

Hope this helps.

---

### Post by metroidnemesis13 on 2008-05-31
Ok, I cleared the firmware RAM and booted to the terminal, but it would not recognize the word linux.

---

### Post by metroidnemesis13 on 2008-05-31
Would this make a difference??  The computer hard drive is from an IBM.  It shouldn't though, right?  Because it let me install linux on it and partitioned it, saw the drivespace, etc.

---

### Post by hpp3 on 2008-06-01
It should take pretty much any IDE drive you shove in there. I put an old 13Gig Western Digital in mine (a G4 with MacOS 9.1), set for slave, works fine. I read somewhere that Macs actually don't like the 'Cable Select' setting.

Does it boot to the MacOS ok now? If it does, then we move on...

Reboot and use the Option-Apple-O-F combo again. Once you're at the firmware terminal, type:
```
devalias
```
That will get you a screenful of info about all the devices in your box.
'hd' is the Apple default drive. Look at the path address next to that entry and look for a similar address but one number up with a different entry label.
I found my second drive at 'ultra1'. The same address was listed for 'hd' and 'ultra0' and so I figured 'ultra1' was what I needed.
It should be the same on your box, so type:
```
boot ultra1:2,yaboot
```
If not, substitute 'ultra1' with whatever you discover.

If that doesn't work, read the Yaboot page under "Recovering from misconfiguration" (which is where I found all this info...) here:
[http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html#s9.1](http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html#s9.1)

Once it does work, read the yaboot and yaboot.conf manpages to setup true dual-booting.
It's a heavy subject, and may require another thread to sort out...

Crossing my fingers...

---

### Post by hpp3 on 2008-06-01
More info:
Since you're on a G3, you wouldn't be able to hold Option at boot to get the Startup Manager, but in this thread:
[http://ubuntuforums.org/showthread.php?t=70329](http://ubuntuforums.org/showthread.php?t=70329)
you'll find simple instructions for how to edit yaboot.conf for dual-boot.

---

### Post by stream303 on 2008-06-01
> **metroidnemesis13 said:**
> Would this make a difference??  The computer hard drive is from an IBM.  It shouldn't though, right?  Because it let me install linux on it and partitioned it, saw the drivespace, etc.

How big is that hard drive?  Is it larger than 128gb?

---

### Post by metroidnemesis13 on 2008-06-01
Okay, so I think the drive I want is ultra1, right?  But if I put say, boot ultra1:x, x being 1, 2, 3, or whatever, it gives me a message

cant open, hd:,\\:tbxi

By the way, my drive I'm using is a Western Digital 10.3 GB set on master.  There is no Mac operating system on it at all, and I'm single booting.

Also, if this helps, I got the Mac from a research lab, its a Blue and White G3, the hard drive was moved for confidentiality reasons, and so I put my own in and installed linux.  The internal battery also only worked for a short while before I had to replace it.  Maybe the firmware got messed up because the internal battery died?  I don't really know.

Thanks again.

---

### Post by hpp3 on 2008-06-02
OK, that clears things up a bit. Not having dual boot makes things a little more straightforward...

1-A dead battery shouldn't have done anything to the firmware, it's hard-coded like a PC bios, but there's a lot more to it.
2-When the firmware says it can't find tbxi, that means it is looking for a Mac disk. We're hopefully going to change that...
3-With a single-disk setup, 'ultra1' is not what you want. That is the label for a second hard drive.

What you want is to tell it to use the first (and only) hard drive and you have to tell it to look for yaboot. 
Yaboot is the ppc linux boot program like grub or lilo, but for the powerpc architecture. It talks nicely to the firmware so your Linux disk isn't ignored.
Try at the firmware prompt:
```

boot hd:2,yaboot

```
or
```

boot ultra0:2,yaboot

```
---explanation---
'Ultra0' and 'hd' are both labels for the master disk in a Mac system. The zero in 'ultra0' is because computers count starting at 0 not 1, like people do.
'2' is the partition number because partition 1 contains the partition table. Ubuntu should have set up partition 2 as an Apple bootstrap partition, which would keep the firmware happy, with partitions 3 and beyond being your Linux and swap partitions.
'yaboot' is the bootloader program you're telling it to look for, which should be on partition 2. If it's not there, you need to re-install.

If that dumps you into yaboot which then proceeds to start your Ubuntu system, then your yaboot is working and your yaboot.conf is set up correctly. After you're logged in, open a terminal and type:
```

sudo ybin -v

```
You should then see 'ybin' give the firmware a stern talking-to about what system is to be running things.

But... if you get a yaboot prompt that doesn't go anywhere, then your /etc/yaboot.conf file needs fixing.
But hopefully, you're up and running and we won't need to go into that...

Let us know what happens...

---

### Post by metroidnemesis13 on 2008-06-02
Yeah, it just says "ultra0:2, can't open" and I've tried multiple numbers for different partitions but none of them work.

---

### Post by hpp3 on 2008-06-03
Sorry for the delay. I was busy and then ubuntuforums went down for maintenance earlier.

Does it give the same message when you go "boot hd:2,yaboot"?

If so, then something went wrong with your partitioning and the Mac firmware is not recognizing your disk as a valid Apple partition.
You are probably going to have to re-partition and/or re-install.
There are other methods available to rescue your installation, but many of them are complex or messy.

Try a re-install or a rescue (type 'rescue' when you boot up the install CD) first and see if that works. If that doesn't get you anywhere, here's what I did to properly partition the drive to make it recognizable by the firmware:

Get and boot a desktop CD (I couldn't figure out how to get a command-line environment from the alternate CD...) and open a terminal. Then type:
```

sudo mac-fdisk /dev/sda

```
You should see a prompt like this:
```

Command (? for help):

```
type "p" and see what comes up.
if you see a list that looks like this:
```

/dev/sda
        #                    type name                length   base    (size )  system
/dev/sda1     Apple_partition_map Apple                   63 @ 1       (31.5k)  Partition map
/dev/sda2         Apple_Bootstrap bootstrap             1600 @ 1216    (800.0k) Unknown
/dev/sda3         Apple_UNIX_SVR2 /                   xxxxxx @ xxxx    (xxxM)   Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                xxxxxx @ xxxx    (xxxM)   Linux swap

```
then your partitions are fine, and something else is up.
If any of these are missing, (this is a BASIC setup, no separate partitions for /home or anything fancy...) then you need to read on for how I re-partitioned:

At the mac-fdisk prompt type 'i' to initalize the disk. Confirm you really want to do this and just hit 'Enter' when it asks for size.
Type 'b' to make the required 800k Mac bootstrap partition.
When it asks for the "First block" type '2P'
Type 'p' to see how much room you have left; it's probably around 9.7 Gigs or so.
Type 'c' to make a root partition.
For First block, type '3P'
For Length, take note of how much disk space is listed under "Apple_Free Extra" and subtract around 250-500 Megs for a swap, then type it in like 'xx.xG' where the 'x's represent the size you calculated.
When it asks for a Name, type '/'
Now for the final step; a swap partition.
Type 'C' (notice it is a capital C...)
For First block, type '4P'
For Length, type '4P' (this will use up the rest of the disk)
For Name of partition, type 'swap'
For Type of partition, type 'swap'
Now type 'w' and confirm (y) to write the table to disk, then reboot and re-install.

Hopefully you won't have to go through all that, but it worked for me...

---

