---
title: "Using Bootcamp for dual boot, now want to triple boot with Ubuntu."
date: 2011-04-30
forum: Apple Hardware Users
---

### Post by isotonic_uk on 2011-04-30
Hi
 
I  am using Bootcamp with a dual boot function with Mac OSX Snow Leopard  and Windows 7. I now want to introduce a 30gb partition for the latest  Ubuntu Distro.
 
I  really want to be careful to ensure I dont break anything as it works  perfectly at the moment. I have used Rfix and Bootpicker to manage the  dual boot processes as well as using the option key in Bootcamp to boot  into each OS. 
 
Does anyone have any advice how I could create a new partiton for me to use for Linux. I want to make a 30gb partion. 
 
Any  step by step instructions would be fantastic. I really want to improve  my Linux skills and want to run it natively rather than thru a virtual  machine using VMware or Parallels. 

Thanks

---

### Post by nandaiyo on 2011-04-30
Isotonic, have you tried wubi?

---

### Post by isotonic_uk on 2011-04-30
The issue for me is I want to run it natively. 

For some reason I would prefer to run it this way, so I can choose which OS to boot up to when turning the machine on. Dont ask me why I just prefer it that way as I know I have full resources for the OS and its not shared with anything else...

---

### Post by mikeydangerous on 2011-05-03
I have a triple-boot system set up. Basically, I just used the Disk Utility in OSX to section off some free space, use rEFIt to boot to the Ubuntu install disc, format and install, then use rEFIt to boot between systems. If rEFIt doesn't work (it may hang on OS icons when booting), just uninstall and reinstall.

---

### Post by handy on 2011-05-03
The previous post tells you what you need to know. Though I'll add a caveat. If you add a /swap for Ubuntu put it after the partition that has GRUB on it or you won't be able to boot Ubuntu.

The reason being that the GPT/EFI system that Apple uses only allows booting from the first 4 partitions. There is a small EFI partition, followed by that of your OS X, then Windows, which gives you 3 partitions. So you must have GRUB on your next partition. 

After that you could have multiple partitions with BSD, other distros & any other systems that you can boot from GRUB.

The first part of the wiki article I wrote some time back goes into the details of this stuff for anyone who is interested:

[https://wiki.archlinux.org/index.php/IMac_Aluminium](https://wiki.archlinux.org/index.php/IMac_Aluminium)

---

### Post by srs5694 on 2011-05-03
> **handy said:**
> The previous post tells you what you need to know. Though I'll add a caveat. If you add a /swap for Ubuntu put it after the partition that has GRUB on it or you won't be able to boot Ubuntu.

The reason being that the GPT/EFI system that Apple uses only allows booting from the first 4 partitions.

This is incorrect. The GUID Partition Table (GPT) has a limit of 128 partitions by default, although that limit can be changed, and GPT itself imposes no limits on which ones may be booted. Likewise, AFAIK there are no limits in the Extensible Firmware Interface (EFI) concerning bootable partitions, except that EFI requires an EFI System Partition (ESP) to hold boot loaders and EFI drivers for hardware. My own Mac Mini is partitioned like this:

```
$ **sudo gdisk -l /dev/sda**
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5A27C85B-AA76-41E5-8D46-59C989B3E1AA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 8-sector boundaries
Total free space is 791189 sectors (386.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640        78534639   37.3 GiB    AF00  OS X 10.4
   3        78796784       176453039   46.6 GiB    AF00  OS X 10.6
   4       176715184       469526527   139.6 GiB   AF00  Apple HFS/HFS+
   5       469788672       470177791   190.0 MiB   0700  Ubuntu /boot
   6       470177792       470568959   191.0 MiB   0700  Unused /boot
   7       470568960       509630463   18.6 GiB    0700  Unused
   8       509630464       548691967   18.6 GiB    0700  Ubuntu root (/)
   9       548691968       551622655   1.4 GiB     8200  Linux swap
  10       551622656       625137663   35.1 GiB    0700  Linux /home

```

I can boot Ubuntu just fine from /dev/sda5, using rEFIt as my primary boot loader. Although in this particular case OS X can't read anything beyond /dev/sda4, that's because of filesystem limitations. To be 100% sure of my claims, I just created a GPT-based 8-partition USB flash drive, and OS X can read all eight of those partitions. Thus, there is no 4-partition limit in OS X, in GPT, or in Linux. I'm less positive of rEFIt's precise capabilities. It doesn't boot Linux directly -- it relies on GRUB to do that -- and in my case rEFIt loads GRUB from the ESP, since I'm [using native EFI-mode booting.](http://www.rodsbooks.com/ubuntu-efi/index.html) It's conceivable that rEFIt has limitations similar to those of Windows (see below), but I doubt it.

I suspect that you're getting confused because of the fact that Apple uses a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) in order to boot Windows. A hybrid MBR is an ugly and dangerous hack that involves creating duplicates of up to three GPT partitions in the Master Boot Record (MBR) partition table as a way to enable GPT-unfriendly OSes to use a GPT disk. A fourth MBR "partition" is a shortened version of a standard GPT feature, the "protective partition," which normally exists to keep GPT-unaware utilities from messing with the disk. In any event, to somebody who looks at the MBR and GPT data side-by-side, it often appears as if the first four GPT partitions have been copied to the MBR. This is because the protective partition normally comes first and most tools that create hybrid MBRs skip the GPT's ESP and then copy over the next three partitions, so it appears as if the first four GPT partitions are duplicated in the MBR. This isn't quite correct, though, and it need not be done that way -- you can select *any* three GPT partitions, assuming they fall within the MBR's 2 TiB size limit, to go in a hybrid MBR, *if* the tool you use to create the hybrid MBR is more flexible. (GPT fdisk and some versions of gptsync can do this.)

Because Windows can't boot from GPT disks on BIOS-based computers, and because Apple relies on BIOS emulation to boot Windows, and because Windows favors the MBR side on hybrid MBR disks, Windows must reside in a hybrid MBR partition when booted on a Mac. If you use the most common tools, this means that Windows (and any partitions you want Windows to see) must reside in the first four partitions; but none of this applies to either Linux or OS X. Both of these OSes favor the GPT data over the MBR data in a hybrid MBR.

---

### Post by handy on 2011-05-03
Too many words srs5694 !

If GRUB is installed on & working on a partition beyond the 4th then Apple have changed the way they are using the GPT/EFI since I investigated it early in 2008.

Under such circumstances what I say holds true on older Mactel machines if it is not valid on the more recent releases.

---

### Post by srs5694 on 2011-05-03
You're mistaken, handy. My Mac Mini is from ~2007 (it's the first-generation Intel machine), and as I say, I'm booting Linux from /dev/sda5 on it. It's conceivable that there are or were limitations in rEFIt, but I've never before heard of or encountered a 4-partition limit in Apple's EFI implementation or in OS X, aside from the issues when dealing with hybrid MBRs -- and those relate to Windows running on Macs. (I've just checked the 8-partition USB flash drive I created under my OS X 10.4.11 installation, and it's fine there, so there doesn't seem to have been any sort of "fix" between 10.4 and 10.6, unless it was implemented in one of the updates that just about everybody should have by now.)

If you could provide references to whatever made you think there was such a limit, perhaps I can explain what was meant (or where the writer went wrong).

---

### Post by handy on 2011-05-03
Because your older, or similarly aged Apple hardware behaves in a certain fashion, that doesn't mean that other Apple hardware of a similar vintage behaves the same way. :)

There were references on the link I posted previously.

---

### Post by handy on 2011-05-04
OK, I've had a "bit" of a look around, & I couldn't find any info' to support the 4 bootable partition OS X, limit. (I only Scroogled.)

It would seem that a combination of both Apple firmware upgrades in combination with the tiny number of people who exceeded the previous 4 partition OS X, limit with/without knowing what they were doing, have caused this info' to be buried. 

These days, any data on the subject is obviously buried far deeper than I'm prepared to spend the time digging up to prove its validity. :)

So, I'll edit my Arch wiki page appropriately.

Thanks for bringing it to my attention that this limitation in OS X, has been removed.

---

### Post by srs5694 on 2011-05-04
I followed every reference I saw on that page and I found no corroborating evidence. The link that, by context, I would expect to hold such evidence did not. Specifically:

[quote=ArchLinux wiki][[3]]("http://developer.apple.com/technotes/tn2006/tn2166.html")  allows OS X to only see 4 partitions, so be sure to install your boot  loader i.e. GRUB/Lilo, & any other partition that you may want OS X  to see (like a shared FAT32 data drive) on sda3 & sda4, Windows must  also be on sda3 or sda4.  Partitions beyond Apple's imposed limit of 4  can still be created & used, e.g. Linux Swap, & other  partitions, but they won't be accessible by OS X or directly bootable[/quote]

In case it doesn't come through, the "[3]" reference on that page is a link to [Apple's Technical Note 2166,](http://developer.apple.com/library/mac/#technotes/tn2166/_index.html) with which I'm quite familiar. It mentions no 4-partition limit. As I've said, I've tested OS X's ability to handle more partitions myself, and at the very least, the wiki's claim that OS X can't see more than four partitions is incorrect for 10.4.11 and 10.6.7. Your claim that some other machine or OS version is so limited could in principle be correct, but given the evidence to date, I'd say the burden of proof rests with you. What specific OS X, firmware, or hardware versions are so limited? What evidence do you have to support this claim?

You stated earlier that you researched this issue in 2008. Was this "research" in the sense of "reading things written by others" or in the sense of "personal experimentation?" If the former, references are required to verify your claims, and you haven't presented any. (In fairness, of course, you might not have references -- but that also makes your conclusions open to criticism because you may have misinterpreted or misremembered something, which is what I suspect happened.) If you did experiments to determine the limits, please describe them.

In short, you've provided no evidence to support your claims. If you have such evidence, please provide it.

---

### Post by srs5694 on 2011-05-04
I began my previous post (#11) before your latest one (#10) appeared, handy, so it's in response to your earlier posts. I still think this issue never existed in quite the way you say; I think you were confusing the limits of Boot Camp and hybrid MBRs with the limits of GPT and EFI. There's a *lot* of confusion out there about hybrid MBRs. Such confusion is not a crime, but it does cause problems, so I hope you'll understand when I say that I suspect you got mixed up over these issues and drew incorrect conclusions. (FWIW, I blame Apple; they shouldn't have decided to use such a flaky and dangerous hack to get Windows working on their hardware.)

---

### Post by handy on 2011-05-04
You may be right. Though I certainly do spend a great deal of time investigating a subject, particularly before I go to the trouble & take on the responsibility of writing a how-to wiki.

So, my stance is that Apple or rEFIt, though I think it was Apple, have changed the situation from what it was 3 years ago.

I've modified my wiki article, & when I'm presented with the documentation that confirms the possibility of a boot loader being installed beyond the 4th partition I will modify it further.

If this is indeed so, it is great that Apple have finally removed this limitation.

As far as your argument involving Boot Camp, it doesn't float with me. I'm well over 5 years of being in any way concerned with the MS OS's. Back in the earlier days of that period (closer to when the wiki article was written) I was still feeling the repulsion generated by having spent so many years solving other people's MS OS based problems, so I have, & I think I can safely say that it is incredibly highly unlikely that I ever will have anything to do with Boot Camp.

---

### Post by srs5694 on 2011-05-04
> **handy said:**
> I've modified my wiki article, & when I'm presented with the documentation that confirms the possibility of a boot loader being installed beyond the 4th partition I will modify it further.

See the screen shot I've attached. I installed OS X 10.5.1 in my spare partition (/dev/sda7, aka /dev/disk0s7 in OS X), booted it with my existing rEFIt, installed rEFIt in the OS X 10.5 partition, reconfigured that rEFIt to use text mode so I was sure I was using it and not the one in my 10.6 partition, and rebooted. Everything worked fine, with the first-generation Mac Mini booting from both a rEFIt boot loader and an OS X kernel in the seventh partition. Note in the screen shot that OS X 10.5 has a root (/) filesystem defined in /dev/disk0s7 -- it booted from beyond your alleged 4-partition limit.

> So, my stance is that Apple or rEFIt, though I think it was Apple, have changed the situation from what it was 3 years ago.

You've presented no evidence that such a limitation ever existed.

> As far as your argument involving Boot Camp, it doesn't float with me. 
...
I can safely say that it is incredibly highly unlikely that I ever will have anything to do with Boot Camp.

You've not said what gave you the idea that there was a 4-partition limit in the first place, except an implication that you've heard of problem reports in the past. If your belief was derived from such problem reports, it could well be that *they* used Boot Camp, or perhaps they experimented with it and then deleted it (leaving behind a hybrid MBR that might have affected things). Thus, your thinking could be influenced by Boot Camp limitations even if you never used it yourself.

---

### Post by handy on 2011-05-04
> **srs5694 said:**
> 
See the screen shot I've attached. I installed OS X 10.5.1 in my spare partition (/dev/sda7, aka /dev/disk0s7 in OS X), booted it with my existing rEFIt, installed rEFIt in the OS X 10.5 partition, reconfigured that rEFIt to use text mode so I was sure I was using it and not the one in my 10.6 partition, and rebooted. Everything worked fine, with the first-generation Mac Mini booting from both a rEFIt boot loader and an OS X kernel in the seventh partition. Note in the screen shot that OS X 10.5 has a root (/) filesystem defined in /dev/disk0s7 -- it booted from beyond your alleged 4-partition limit. 

Could you try booting a distro via GRUB installed on a partition beyond #4?

> **srs5694 said:**
> 
You've presented no evidence that such a limitation ever existed. 

I had a bit of a search & couldn't find any evidence. That doesn't mean it doesn't exist. I'm years away from dealing with this stuff. I wrote the wiki article after installing Arch on the iMac. It carries (less than it used to) all of the information required (plus some explanations as to why) for a successful installation of Arch on such a machine.

As I've said previously, I did extensive research at the time & that wiki was the result of same.

So you can believe that I got confused by something else if you like. I don't believe that that is the case.  :)

---

### Post by srs5694 on 2011-05-05
> **handy said:**
> Could you try booting a distro via GRUB installed on a partition beyond #4?

See [post #6 in this thread.](http://ubuntuforums.org/showpost.php?p=10762895&postcount=6)

> I had a bit of a search & couldn't find any evidence. That doesn't mean it doesn't exist.

You can search for a teacup in orbit around Jupiter and not find it. That doesn't mean it doesn't exist.

OTOH, without evidence, it's irrational to believe that it does exist.

I'm tired of arguing this point, and I bet others are tired of it too. I won't respond further unless you can provide actual evidence to back up your claims. In the meantime, if you care to believe in orbiting teacups, go right ahead.

---

### Post by handy on 2011-05-05
I'm glad you are tired of arguing. :)

Because I've not been.

It was how it was, & now it is different.

I have no problems with that, & I thank you for bringing me up to date on the topic.

---

