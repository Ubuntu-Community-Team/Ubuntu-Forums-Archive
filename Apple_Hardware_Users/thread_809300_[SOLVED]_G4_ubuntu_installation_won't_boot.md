---
title: "[SOLVED] G4 ubuntu installation won't boot"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by davereynoldz on 2008-05-27
Hi guys, I have an old G4 which I've set up as a little home file server since the P3 I had for this seems to have died. I put ubuntu on it but now it won't boot up, I just get the little flashing question mark. I've downloaded and installed the powerpc ubuntu server edition on my G4 and everything went fine, the installation completed with no errors. I used an automatic partition setup for the main partition so it did all the boot stuff by itself. It just won't boot. 

I have a 500 gig sata hard drive attached via a pci sata card but it is not a boot drive, although I don't know how the G4 knows this as theres no settings that I can find to specify the boot sequence?

Would be really nice if anyone could point me in the right direction? I'd really like to get this little machine up and running as a file server, don't want to have to go out and buy some new bits.

---

### Post by lisati on 2008-05-27
Edit: I asked a dumb question from not reading the original post properly. Please ignore this post.

---

### Post by davereynoldz on 2008-05-27
Forgot to mention I've tried two different hard drives so I don't think its a problem with the drive. Yaboot boots fine off the cd so I don't think theres a problem with that either. The hard drive is jumpered cable select, on the end of its strap.

---

### Post by mfox on 2008-05-27
I had the same problem when I tried to make a dual boot Ubuntu on a G3 beige tower.  If your's is an "old world Mac" like my beige, they allow use of only 128gb on the drive and the startup files have to be present on the first 8gb of the drive. If you have one of these Macs and you upgraded to a larger drive than it came with, you would be advised to partition a large drive so that the first partition (startup volume) is within the first 8 GB of disk space. This is a limitation of the old IDE hardware. The second partition can be up to a total of 128 GB for both partitions.  I don't know that the boot partition within the first 8gb would normally be a problem, but if you are making a dual boot system and you have one of these macs, the files that enable Linux might be put in a place on the disk where the hardware wouldn't detect them at startup.  If this applies to you, the solution would be to reformat the drive with the first Mac partition being 7.5gb in capacity and installing the System on it. 

Having said all this about the old world Mac limitations, I never really found out if this was the only problem or it was something else additional, but I couldn't successfully install 7.10 and get it to boot.  Following advice from another Mac person, I installed 6.06LTS and this worked.  One of the differences upon installation is the default partitioning - 7.10 made separate partitions for /, /home and scratch, whereas 6.06 combined the / and /home in one partition.  I don't know if the latter scheme worked because it dealt with the 8gb issue or if it was something else, so I've mentioned all of these things in my post.  I hope it helps.

---

### Post by stream303 on 2008-05-27
> **davereynoldz said:**
> I have a 500 gig sata hard drive attached via a pci sata card but it is not a boot drive, although I don't know how the G4 knows this as theres no settings that I can find to specify the boot sequence?

Have you tried holding down the alt/option key shortly after powering up, clicking on the icon for the drive you want to boot from, and then clicking on the right-arrow icon?

Which machine do you have?  This will help determine if you even run across this problem:
[http://www.everymac.com/](http://www.everymac.com/)

Mfox is right about the partitioning limitations - the early new-world G3's sometimes had the 8gb limitation (partition to no more than say 7gb to be conservative), and some later machines had 128gb limitations (partition to 125gb or less to be conservative), but you may not have this problem depending on your machine.

---

### Post by davereynoldz on 2008-05-27
The mac is one of these: [http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450.html)   A power mac G4 450. The drive is only 120 gig and I have used the entire drive for the ubuntu installation. I have also installed this system on a spare 20 gig drive using the full drive with a full format and get the same problem.

When I hold down the alt key it detects no bootable drives and gives no options, despite there being a bootable ubuntu drive plugged in. 

My hunch is that the power mac is attempting to boot from the sata drive on the raid card and/or simply ignoring the ide drive containing the installation. This 500 gig drive is my 'dump' area for my filesystem which I want to keep as a basic ext3 filesystem with no boot sector or os, for easy swapping from system to system. I have a second 300 gig sata drive which I was going to attempt to use as the primary os drive but it is in another computer and needs some (large quantities of) data saved somewhere else temporarily.

If this were an intel system I would be inspecting the boot sequence in the bios and bootability of this drive, ie master/slave situation. I believe I have it jumpered and cabled correctly, I have even tried unplugging the cd drive and sata drive to no avail. The system is quite happy to boot straight off a cd without holding the 'c' key so my assumption (as an intel user who knows nothing about macs) is that it is set to boot from cd only in its... 'bios'?

---

### Post by davereynoldz on 2008-05-27
Oh, and I can boot into open firmware by holding cmd+opt+O+F, which according to thie website: [http://homepages.gold.ac.uk/suzanne/startup.html](http://homepages.gold.ac.uk/suzanne/startup.html) indicates it is a 'ne world' mac.

I am trying to use open firmware to work out what the system is detecting but I'm not sure how right now.

---

### Post by stream303 on 2008-05-27
eeks - those dual-driver Macs can be troublesome.  I've got a hunch that the device line in your /etc/yaboot.conf isn't correct or nearly blank, even though yaboot said it installed.

You may have to go in with the live cd, and run

```
blkid
```

to get a better idea of what the device line needs and follow up with a ybin.  There have been a few threads on this here and in the archives - I'd have to dig through them again..

So let's see if your yaboot.conf has an openfirmware path listed in the device line first...

---

### Post by davereynoldz on 2008-05-27
Ok: a development! In open firmware I have instructed the mac to boot yaboot specifically with this command: boot hd:0,\yaboot it then reports the following:

DISK-LABEL: LOAD (noninterposed) not supportedload-size=0 adler32=1

LOAD-SIZE is too small

So there you go... now what? yaboot settings? I have tried inspecting this stuff by booting up the cd with the rescue option and dropping into a shell (this is an ubuntu server disc mind), but despite saying it will mount filesystem drives it does not. I can't seem to mount them manually either, so can't really inspect whats going on. 

Do I need some different install settings perhaps?

*edit: didnt see your response there stream, seems you were on to it, I gather at least. This mac stuff might as well be in russian for all the sense it makes to me, but I am learning. I'll have a bit more of a poke around with the live cd.

---

### Post by davereynoldz on 2008-05-27
blkid output:
```
#blkid
/dev/hda1: TYPE="hfs"
/dev/hda5: UUID="3119d273-e9bf-4330-91de-0d84f96712a9" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda6 TYPE="swap" UUID="another large hex code"
/dev/sda1: UUID="and another hex code" SEC_TYPE="ext2" TYPE="ext3"
```

Sorry I couldn't copy/paste it so I omitted what I figured wasn't relevant rather than typing out massive hex codes :)

yaboot.conf:
```
boot=/dev/hda1
device=/pci@f2000000/pci-bridge@d/mac-io@7/ata-4@1f000/disk@0
partition=5
root=dev/hda5
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
    label=Linux
    read-only
    initrd=/boot/initrd.img
    append="quiet splash"

image=/boot/vmlinux.old
    label=old
    read-only
    initrd=/boot/initrd.img.old
    append="quiet splash"
(END)
```

So there it is... what needs to be changed to what?

One thing I can see there is it says "partition=5" although I'm not sure what this is referring to but it looks like it is referring to hda1? should this be something like partition=0 or partition=1? hda5 certainly contains my root file system I've confirmed that, and hda1-4 seem to be the various mac boot partitions (why so many?)

---

### Post by stream303 on 2008-05-27
Oops.  While it was good to see your /etc/yaboot.conf, I think I really meant to take a look at the /etc/fstab

and see if it corresponds to the blkid

(Btw, a default partitioning of an Apple box will result in at least 4 partitions: 1) Apple partition map, 2) apple bootstrap, 3) Your / root and everything else if kept to just one partition, and 4) swap.) although in this case we're more interested in the filesystem table.

This /etc/fstab has been known to have incorrect values when dual-hd drives are in use at times...

According to yaboot.conf, it looks like it is setup to boot the system from the smaller /dev/hda device, rather than your /dev/sda.

Also check /etc/fstab to make sure that the blkid's match the drives in use.

Real easy for me to say rather than do, I know... :)

---

### Post by davereynoldz on 2008-05-27
Ok, sorry I'm not gonna write it all out but the drives in the blkid output match exactly what is in /etc/fstab.

I want this system set up to boot from the smaller drive, I don't want my big drive booting as I'd like to to be easily swapped into other computers if need be.

It appears that I have 6 partitions, the first 4 seem to be the mac boot stuff (can't mount them with the rescue disc) while the 5th is my root filesystem and the 6th is swap.

*edit: one thing I noticed when I did the install, the autoconfig of the mac partitions resulted in the root partition (hda5) being flagged not bootable while the hfs partition (hda1) is the bootable one. Is this right? I assume it is but I'm just so stumped right now...

---

### Post by stream303 on 2008-05-28
I'm puzzled too but have to cover all the bases - have you tried resetting your pram / nvram?  Urban legend has it that when changing any hardware around, the pram can get confused sometimes, and is not just for dead batteries:

[http://support.apple.com/kb/HT1379](http://support.apple.com/kb/HT1379)

---

### Post by davereynoldz on 2008-05-28
Yep, done the pram thing. One question though, what if the cmos battery is dead? This mac sat around for a long time before I set this server up... tried, that is. Does the pram/nvram rely on the battery to remain non-volatile? as in, would it "forget" the yaboot settings upon reboot?

Its a shame, the mac hardware seems pretty solid for what I want to do. I'm really hoping I don't have to go buy a second hand motherboard. Even been thinking of buying the cheapest mobo/ram/psu combo available new and "upgrading" (read: gutting) the old P3 tower.

Haven't given upon the mac yet though.

---

### Post by davereynoldz on 2008-05-29
SOLVED! So, I popped the battery and tested it, seems fine plenty of juice - that wasn't the problem.

So I found some threads where users had trouble with yaboot when doing a manual partition table. Hmm I thought... I noticed that the ubuntu installer only gave me the option to do a guided partition  on the sata drive, not the ide drive. So I thought ok linux, how bout we try this without the sata drive? I unplugged the sata drive and booted up the installer then did a guided install on the ide drive which was now the only option... few minutes later and viola! It booted up! So then all I had to do was set up my sata drive manually and now everything is working.

So, for anyone who has a G4 and is using a pci raid card with sata drives, and happens to want to use an ide drive for the boot partition, you might need to unplug that sata drive for the install process and set it up manually later. 

Thank you stream for all the help, you are a legend even though I figured it out myself, you showed me a bunch of stuff.

The Ubuntu community rocks!

---

### Post by stream303 on 2008-05-29
> **davereynoldz said:**
> SOLVED! So, I popped the battery and tested it, seems fine plenty of juice - that wasn't the problem.

Good deal - I think that battery is a 3.6v Lithium by Tadiran.  I've seen them in Radio Shacks as well as online.  For future ref just in case...

I'm so glad you hung in there and got that thing up and running!

> Thank you stream for all the help, you are a legend even though I figured it out myself, you showed me a bunch of stuff.

Thank you, although you did all the hard work really.  Legend belongs to all of the users here, yourself included!

I wish I could have been a fly on the wall for the first reboot. :)

When you got the second drive up and running, you might want to take a look at /etc/fstab again, and see if you want to add the *relatime* parameter to it, unless you need time-stamps on every read for your server purposes.

---

### Post by davereynoldz on 2008-05-29
> **stream303 said:**
> When you got the second drive up and running, you might want to take a look at /etc/fstab again, and see if you want to add the *relatime* parameter to it, unless you need time-stamps on every read for your server purposes.
I just set it to defaults, I think I set something like: /dev/sda1 /dump defaults 0 0 dunno what that sets but I found it in some how to. I'm not entirely a linux guru or anything, but I wouldn't class myself as a noob :)

The server is just a place for all my media, software, backups, music, photos, anything really. I just got sick of having two computers and two laptops each with two hard drives and multiple instances of the same directory with different files in each (ie: 4 'downloads' directories and 4 'tv' directories). Hard drives are so cheap these days, plenty of room in the mac case for more too, however the psu does seem limited but hey who needs optical media. 

The mac runs a lot faster than the old P3 I had, with lower specs, dunno how the old powerpc chips compare to old intel stuff? Were talking a 450mhz ppc vs a 933mhz p3 here.

---

### Post by stream303 on 2008-05-29
I'm not sure if it applies to G4's, but the rough analogy for ppc was to consider the ppc at twice the speed as compared to Intel, ie a 450 mhz ppc box would be roughly equivalent to a 900 mhz intel.  I know it doesn't apply to G5's, but it does to G3's and I *think* to G4's...

---

