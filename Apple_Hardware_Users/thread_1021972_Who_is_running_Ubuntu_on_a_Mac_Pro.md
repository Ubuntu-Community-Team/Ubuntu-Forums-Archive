---
title: "Who is running Ubuntu on a Mac Pro?"
date: 2008-12-26
forum: Apple Hardware Users
---

### Post by Gsundbrunn on 2008-12-26
Hi,

would be very helpful for me to know, who ist running a Ubuntu on a Mac Pro? And which version is the machine? (1.1, 2.1, 3.1?)

And - how many CPU cores are in the machine?

Many thanks!

Stefan

---

### Post by jpugh on 2008-12-26
You can't tell? Lot's
Count me as one.

Macbook Pro v3,1

---

### Post by Gsundbrunn on 2008-12-26
Hi,

ah - not MacBook Pro - Mac Pro ;-) Its definitively a difference ;-)

Regards

Stefan

---

### Post by cyberdork33 on 2008-12-28
not many. and the ones that are don't hang around long.

---

### Post by CalaverX11 on 2009-02-18
3,1 here. Dual-quad Xeon, 6GB RAM, 320GB hard drive, dual-booted with OS 10.5.6.

My only problem: no sound in Ubuntu. I still haven't figured it out, and I've been pulling my hair out trying to find a working solution. Everything else (except the function keys, need to press "FN" unless there's a fix for that) works fine.

---

### Post by cyberdork33 on 2009-02-19
> **CalaverX11 said:**
> ...except the function keys, need to press "FN" unless there's a fix for that
[http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)

---

### Post by CalaverX11 on 2009-02-19
> **cyberdork33 said:**
> [http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)

Aha, thank you.

As for sound, I followed the tutorial here. I got the rear port working finally. Has anyone ever made the front speaker and/or headphone port work?

---

### Post by runexe on 2009-03-20
> **CalaverX11 said:**
> 3,1 here. Dual-quad Xeon, 6GB RAM, 320GB hard drive, dual-booted with OS 10.5.6.


May I ask which version of Ubuntu you are running? I'm struggling with an install of 8.10 Server Edition (x86_64) on mine (sounds like the same configuation: Dual Quad Xeon E5520's, 6GB RAM, 640GB HD, nVidia 9500). Hmmm - just to be sure: 3,1 refers to this years model, correct? Or is that the 2008 Mac Pro?

Just to report where I'm at: I was able to install, but am struggling with the bootloader, and getting the Gig-E interfaces to work. For the bootloader, I have rEFIt working, and it reports the GPT/MBR tables as synced, but selecting the Linux icon leads to an error about no Legacy Boot loader found.

For the ethernet adapter, it appears to me that the e1000e module should work, as ioreg in OS X reports them as Intel 82574L's. However, lspci gives PCI ID's that aren't found anywhere: 8086:10F6 (Intel, Unknown Device). A google search found a Windows .inf floating around, but not much else of use. I'm hoping I can just add the ID to the e1000e module code, and tell it it's another ich10 lan adapter.

Edit:
Looks like the 2009 model is 4,1. I'll report back if I have any luck with the ethernet adapter.

---

### Post by emacspy on 2009-03-24
Mac Pro MA356LL/A here running tripple boot OSX,XP64,Kubuntu 8.10 x64.

---

### Post by CalaverX11 on 2009-03-24
> **runexe said:**
> May I ask which version of Ubuntu you are running? I'm struggling with an install of 8.10 Server Edition (x86_64) on mine (sounds like the same configuation: Dual Quad Xeon E5520's, 6GB RAM, 640GB HD, nVidia 9500). Hmmm - just to be sure: 3,1 refers to this years model, correct? Or is that the 2008 Mac Pro?

Intrepid, 8.10, all updated. Now the only thing I can't seem to do is run Second Life, which up until the recent kernel update, was SCREAMING fast. As for sound, still no luck, but I did manage to get the rear speaker output to work. 3,1 is the 2008 model. It was before the 500GB drive and stock 8GB RAM.

---

### Post by cyberdork33 on 2009-03-24
> **emacspy said:**
> Mac Pro MA356LL/A here running tripple boot OSX,XP64,Kubuntu 8.10 x64.
You should determine your MacProX,X version string. See:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by runexe on 2009-03-27
> **runexe said:**
> 
Looks like the 2009 model is 4,1. I'll report back if I have any luck with the ethernet adapter.

For the ethernet adapters - I've discovered that technically the e1000e driver does support it, but needs a two line patch to recognize it as a 82574-style NIC. The patch is available at:
[http://kerneltrap.org/mailarchive/linux-netdev/2009/3/25/5235664](http://kerneltrap.org/mailarchive/linux-netdev/2009/3/25/5235664)
It will apparently appear in 2.6.30 - I don't know if it'll get backported.

I now have Jaunty running on it nicely, except for the bootloader (I have to boot from CD, then select first hard drive for it to find the grub-pc loader - rEFIt errors out with Legacy Bootloader errors).

---

### Post by CalaverX11 on 2009-03-27
> **runexe said:**
> I now have Jaunty running on it nicely, except for the bootloader (I have to boot from CD, then select first hard drive for it to find the grub-pc loader - rEFIt errors out with Legacy Bootloader errors).

Does Boot Camp not recognize it as a bootable partition? Have you tried holding "alt" while booting to activate Boot Camp drive selection? I stopped using rEFIt after I discovered this.

---

### Post by rshnike on 2009-03-27
> **cyberdork33 said:**
> not many. and the ones that are don't hang around long.

That's interesting. Care to explain the reason for that? I've been waiting to purchase a Mac Pro (been waiting for bluray+cpu's with fused m-a) but I'm planning on dual(triple)-booting from the day I get it.

---

### Post by runexe on 2009-03-27
> **CalaverX11 said:**
> Does Boot Camp not recognize it as a bootable partition? Have you tried holding "alt" while booting to activate Boot Camp drive selection? I stopped using rEFIt after I discovered this.

I'll give that a shot next reboot.

---

### Post by cyberdork33 on 2009-03-27
> **rshnike said:**
> That's interesting. Care to explain the reason for that? I've been waiting to purchase a Mac Pro (been waiting for bluray+cpu's with fused m-a) but I'm planning on dual(triple)-booting from the day I get it.
they figure out how to get it to boot, or fix some problem, then they don't come back. IDK why... Making that big of an investment, I would assume that you will be using OS X for the most part.

---

### Post by CalaverX11 on 2009-03-27
> **cyberdork33 said:**
> they figure out how to get it to boot, or fix some problem, then they don't come back. IDK why... Making that big of an investment, I would assume that you will be using OS X for the most part.

I'm subscribed to this thread, so I get an email every time someone replies. :P I'll help out where I can, though admittedly I'm still "new" to Linux and Ubuntu (only been using them for about six years). And I'm BRAND NEW to Macs...I got this machine five months ago, and have only recently started diving into Ubuntu on it.

---

### Post by bluecitabria on 2009-03-27
i got a nehalem based mac pro and have had very limited success with 5 different distributions (ubuntu, debian5, gentoo, centos5, fedora10). the problems i had were:
1) no ethernet
2) no sound
3) slower than anticipated accellerated 3d graphics. the card (+/- nvidia 9500 or whatever is is called now) performs 3x better under OSX 10.5.?
4) video anomolies at boot. if i didn't load set a mode as a kernel parameter, i got very odd screen output on the console. the video memory would just scroll back repeatedly after entering a command on the console. only entering a command that returned "command not found" would let me reset the terminal.
starting X would give flashes and hic-cups from the nvidia driver as it loaded. (this didn't happen with the vesa driver from the debian) installation.
5) no CD burning.

i see that the ethernet issue has been "solved" herein. i tried one of the sound solutions but it didn't work. booting is not an issue.

i have no interest in running any variant of OSX. i've been running some variant of linux on boxes based on x86, ppc, and sparc for almost 15 years. now i'm old and tired and could use a little help. thanks for any that anyone can provide.

to try to avoid a stream of "why did you get an apple if you didn't want OSX" reply's my, reasons for buying it were:
-i wanted a fast box; 
-it seemed to be well made, quiet and sturdy;
-similar workstations from hewlett packard, boxx systems, and the like were more expensive;
-i didn't want another "home built";
-it seemed that everything was pretty well supported in the open source community. additionally, before i bought it i did a test run on a friend's 5400 based system and everything worked perfectly. i installed ubuntu 8.10 "amd64" and then i did a 'from scratch' installation of gentoo, compiling and testing everything i could think of.

---

### Post by sms0611 on 2009-03-28
Hi Guys,

I'm running a PowerMac G4 with Ubuntu 8.04 (Heron)

I have just got the sound working using the internal Apple sound card (PowerMac Tumbler) via the inbuilt speaker and the headphone jack.

If anyone out there wants to know how feel free to get in touch.

---

### Post by cyberdork33 on 2009-03-28
> **sms0611 said:**
> Hi Guys,

I'm running a PowerMac G4 with Ubuntu 8.04 (Heron)

I have just got the sound working using the internal Apple sound card (PowerMac Tumbler) via the inbuilt speaker and the headphone jack.

If anyone out there wants to know how feel free to get in touch.
This is a thread about Intel-based Mac Pro hardware. It will be quite different.

---

### Post by sms0611 on 2009-03-28
In that case, I'm sorry to have disturbed you. I wish you all the best of luck and hope solving your problems are no where near as complicated as solving ours.

---

### Post by rshnike on 2009-03-28
> **cyberdork33 said:**
> they figure out how to get it to boot, or fix some problem, then they don't come back. IDK why... Making that big of an investment, I would assume that you will be using OS X for the most part.

Yeah. I can see that. I mean truthfully there are two types of people who buy Mac Pros, those who have no idea what they are good for and just buy it because they have way too much money to know what to do with so they buy the most expensive thing in the store (these are the people that Apple makes their $9000 RAM money on) and then there are the people who are the creative professionals and developers and the intelligent types who usually manage on their own to figure out any problems they have.

I think you're right that they're less likely to remain "loyal" posters, but like I said I personally would plan on triple boot OSX Server, Ubuntu and Windows 7 along with a partition for something like LFS. Having so many HD bays just opens up such nice possibilities.

I think in general new users are less likely to stick around the forums because the most likely problems to encounter with a Mac purchase are going to be (in general) universal to the product line, and so they've probably been asked and answered.

---

### Post by runexe on 2009-03-31
> **CalaverX11 said:**
> Does Boot Camp not recognize it as a bootable partition? Have you tried holding "alt" while booting to activate Boot Camp drive selection? I stopped using rEFIt after I discovered this.

It is not recognized as a bootable partition. Parted shows:

```
(parted) print
Model: ATA WDC WD6400AAKS-4 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot
 2      210MB   65.6GB  65.4GB  hfs+         Untitled
 3      65.7GB  636GB   570GB   ext3         linux
 4      636GB   640GB   4026MB  linux-swap   swap
```

Should I be marking the linux (my /) partition as bootable? I seem to recall having issues last time I did that - at least as far as my current solution (booting from the install CD -> selecting boot from 1st hard drive when I need to reboot) goes.

---

### Post by cyberdork33 on 2009-03-31
> **runexe said:**
> Should I be marking the linux (my /) partition as bootable? I seem to recall having issues last time I did that - at least as far as my current solution (booting from the install CD -> selecting boot from 1st hard drive when I need to reboot) goes.
no the EFI partition should be the bootable partition in the GPT table.

If you have multiple hard drives, you might have to reinstall grub with some weird parameters... Apple's firmware does some weird stuff. basically it sees the drive that you boot from as the primary. (even if it is not the primary in the computer.) See:
[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

---

### Post by runexe on 2009-03-31
> **cyberdork33 said:**
> no the EFI partition should be the bootable partition in the GPT table.

If you have multiple hard drives, you might have to reinstall grub with some weird parameters... Apple's firmware does some weird stuff. basically it sees the drive that you boot from as the primary. (even if it is not the primary in the computer.) See:
[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

Ok, thanks. I had pretty much followed the same procedure that worked on my older Macbook Pro (3,1).
Just the one hard drive in the Mac Pro though, so I'm wondering if the new models have some firmware weirdness going on. rEFIt gives me a Legacy Bootloader error when I try to boot the linux partition. Switching to grub2 got a little further, but I got stuck when it wasn't able to find the framebuffer/write to the screen.

---

### Post by cyberdork33 on 2009-03-31
> **runexe said:**
> Ok, thanks. I had pretty much followed the same procedure that worked on my older Macbook Pro (3,1).
Just the one hard drive in the Mac Pro though, so I'm wondering if the new models have some firmware weirdness going on. rEFIt gives me a Legacy Bootloader error when I try to boot the linux partition. Switching to grub2 got a little further, but I got stuck when it wasn't able to find the framebuffer/write to the screen.
if you just have the one drive, then it should be the same.

Can you use rEFIt's partition inspector in /Applications/Utilities and post the output?

---

### Post by runexe on 2009-04-01
> **cyberdork33 said:**
> if you just have the one drive, then it should be the same.

Can you use rEFIt's partition inspector in /Applications/Utilities and post the output?

Here it is:
```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    128073767  Mac OS X HFS+
 3      128337920   1242400419  Basic Data
 4     1242400420   1250263694  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    128073767  af  Mac OS X HFS+
 3 *    128337920   1242400419  83  Linux
 4     1242400420   1250263694  82  Linux swap / Solaris

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 128337920:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 1242400420:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris
```

---

### Post by cyberdork33 on 2009-04-01
Everything looks pretty good. I did notice that you have GRUB in the MBR rather than the Ubuntu partition. That is OK usually, but we usually recommend installing it to the partition since you boot it from rEFIt.

You didn't really ever answer the question before... If you hold ALT on startup, you should have the option to select OSX or "Windows". Does selecting the Windows option boot grub? Does it even show up? Any errors?

---

### Post by pafufta503 on 2009-04-04
running jaunty on a macpro 1,1.  succesfully and happily ;)

---

### Post by runexe on 2009-04-13
> **cyberdork33 said:**
> Everything looks pretty good. I did notice that you have GRUB in the MBR rather than the Ubuntu partition. That is OK usually, but we usually recommend installing it to the partition since you boot it from rEFIt.

You didn't really ever answer the question before... If you hold ALT on startup, you should have the option to select OSX or "Windows". Does selecting the Windows option boot grub? Does it even show up? Any errors?

Ok - since I needed to reboot today - I'm returning to this issue. It looks like rEFIt came up with an update (0.13) to work on the Mac Pro 4,1 - just installed it, and after telling grub to install to the partition, it's working now.

---

