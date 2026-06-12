---
title: "Made a mess of my UEFI dualboot config"
date: 2014-05-06
forum: Any Other OS
---

### Post by x34460 on 2014-05-06
So, I have been tinkering with installing a very well known OS that has something to do with fruit on an old HP AMD laptop. 
Technically, it worked, but not well. So, I thought I'd see how it worked on my primary laptop which is much newer, more robust and more compatible (Intel)... with the HDD removed, to prevent ANY chance of any kind of data loss on the HDD.
I pulled the HDD out of my primary laptop and used the same flash drive I had been using on the older laptop but it simply would not install. 
So, I put the HDD back in and changed the UEFI config back to what it was prior to my endeavor and now all I get is a minimal Grub CLI prompt at boot.

My guess is that I screwed up the .efi config by pulling out the HDD, trying to install an OS on the USB drive and then pulling that and replacing my HDD with Lin and Win.

UEFI is still new to me and I was unaware it was so easy to run into trouble with.
At boot, my primary laptop is no longer seeing any of the partitions that have been there since I installed Mint along side of Win8 last fall when I bought the laptop and installed LinuxMint alongside Win8.
Up till today, I have not had any problems with dual booting.

Again, the data on my HDD is 100% intact as the drive was physically pulled from the machine before I attempted to install a new OS on a usb drive.

I ran a boot-repair-disk (sourceforge.net/p/boot-repair) I used when installing linux last year as it was part of the instructions I followed. 
Everything worked fine then but today, it gave a warning about UEFI being detected (don't recall that warning from last fall) so I aborted and looked in the UEFI settings manually.

Looking under "Security" in UEFI, there are sub menus.. HDD1-> EFI-> MICROSOFT, BOOT, OEM, UBUNTU, LINUXMINT and GRUB.
The MICROSOFT sub leads to BOOT and then a long list of language preferences with .efi extensions. 
The "OEM" option does the same. 
"BOOT" leads to "bkpbootx64.efi" 
"LINUXMINT" and "GRUB" both lead to grub64.efi and shimx64.efi but "UBUNTU" leads to grub64.efi, shimx64.efi AND MokManager.efi

When an .efi file is selected, I'm prompted to add the file to allowable database.
This is where I'm hung up for the time being, mostly as a precaution so I don't corrupt or lose any data on my HDD.

I'll keep researching but if anyone has any knowledge or experience with this issue, please share what you can.

Thanks.

---

### Post by oldfred on 2014-05-06
UEFI remembers settings in its NVRAM, but I thought it scanned efi partition for new efi files.
So if a file changed in NVRAM but has same name maybe it did not update?

Post link to BootInfo report from a UEFI boot.
It should include this, somewhere in report, but if not also add this to post.
 sudo efibootmgr -v


 Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by x34460 on 2014-05-06
Thank you for replying.
I'll work on this but let me first ask..

What would happen if I selected one of the .efi files?
Maybe, SECURITY-> HDD1-> EFI-> UBUNTU-> grub64.efi
What if I chose that to be a "trusted database"? Would I have my GRUB menu back?

So far, I have NOT selected any of the .efi files because I did not want to commit the change and make matters worse.

Thank you.

---

### Post by oldfred on 2014-05-06
Shim is the signed venison of grub so it is trusted, but grub is not.

Is secure boot on?

---

### Post by x34460 on 2014-05-07
No. Not now but when I swapped the USB drive and out the HDD back in, settings were reset and secure boot was on as were some other features I know had changed prior to this.

So, what if I select grub64.efi as trusted and add to database?
What happens next?
I just dont want my partitions getting fouled up because of a bootloader issue caused by EUFI.

Thanks.

---

### Post by oldfred on 2014-05-07
You cannot select grub64.efi as trusted as it does not have a signed key. Only shim version has the signed key.

Different version but explains some of the requirement for a Microsoft signed key.
 Details on Ubuntu's shim with 12.10
[http://falstaff.agner.ch/2012/12/12/secure-boot-implementation-of-ubuntu-12-10-quantal-quetzal/](http://falstaff.agner.ch/2012/12/12/secure-boot-implementation-of-ubuntu-12-10-quantal-quetzal/)
They land alongside their unsigned variants in /boot with the file suffix &#8220;.efi.signed&#8221;.

---

### Post by x34460 on 2014-05-07
I selected shimx64 and it's number 1 in boot order (secure boot) but does not resolve the issue.
I attempted running the boot repair cd also to no avail.

With this UEFI, I can not boot from a cd unless UEFI is off and legacy bios is enabled.
Using that configuration, I get the boot repair CD running and it even tells me to be sure to enable UEFI when finished but at the end of the repair process, there was an error and in all, have made no progress.

Let me just clarify that secure boot has been off, up until all of this began and when making changes (.efi database or running boot repair) I toggle secure boot to see if one setting or another will work but so far, no success.

I'd like to follow your instruction:
Post link to BootInfo report from a UEFI boot.
It should include this, somewhere in report, but if not also add this to post.
sudo efibootmgr -v

Would this work from the boot-repair disc since I am unable to boot into either my Lin or Win partition?

---

### Post by x34460 on 2014-05-07
I've been working at this for a while and at one point, ran the repair disc but it keeps giving me AMD64 errors when attempting the repair.
I have received AMD64 errors during several attempts.
I find that a bit confusing because this is an Intel board. 

You mentioned that UEFI stores settings from NVRAM. Could something be stuck in UEFI from when I was messing around with the USB flash drive i had just pulled from the AMD64 laptop I used to install OSX86 on and plugged it into my Intel, the one I'm on now, to try to get the installation to work?
Could it have read that USB drive and that's why I am seeing AMD64 errors when I attempt to run the disc repair? Because something from that got copied over to the UEFI on my Intel?
Maybe just trying to install osx86 on this computer caused that?

Anyhow, the last time that I got the error with the boot repair disc, I just aborted when it showed that error again and upon restart, I was able to boot into my Windows partition, which I'm on now. That's a step in the right direction, but only a small step as I don't use this partition for anything. 
Still trying to get the Linux partition up and running.

I also read the link you provided, [https://software.intel.com/en-us/articles/efi-shells-and-scripting/](https://software.intel.com/en-us/articles/efi-shells-and-scripting/), and looked for instructions as to how I can get the information you requested about UEFI boot but I did not see how to get it so I can share it with you.

I may have overlooked it. 
Can you point me in the right direction so I can get that information posted?

Thanks again.

---

### Post by oldfred on 2014-05-07
See post #2

---

### Post by x34460 on 2014-05-08
So, I've been at this for a while now but am still not having any success.
I've studied the links from "post #2" but am having difficulty getting the processes involved to work.
I have Shell.efi on a flash drive, ready to copy into the efi folder of UEFI but I can't open that partition to move it into so it can be executed at boot.

I keep running the boot-repair disc but no mater what options I choose, it just keeps setting up Grub for AMD64.
It's as if the USB HDD I had osx86 installed on and then attempted to reinstall on, on my Intel, contaminated UEFI and now boot-repair keeps trying to reconfigure an AMD64 which is wrong, wrong, wrong.

I am working on an Intel board with Sandy Bridge CPU trying to fix Grub so I can boot into my Linux partition.

---

### Post by x34460 on 2014-05-08
As it stands right now, I have put the file on the USB flash drive and attempted to load that shell at boot but the computer is no longer booting... not even into windows.

All partitions seem to be in tact but booting is hosed.

I originally posted here because I needed assistance having attempted to help myself thru this problem using Google, Youtube, Reddit, etc but still need help.

Thank you.

---

### Post by oldfred on 2014-05-08
Post link to latest BootInfo report from Boot-Repair. Or run just the report.

---

### Post by x34460 on 2014-05-12
I just ran the Mint live/install disc.

I followed your instruction:
[I]Must boot live installer in UEFI mode.
sudo efibootmgr -v[/I]

Result was "file not found"

Anyhow, I ran boot-repair from the live Mint DVD and afterwards, it generated a link to a report.
Since I am unable to generate the report you originally requested (sudo efibootmgr -v) would the output from the report generated when the boot-repair supposedly worked it's magic be of any benefit/assistance to you?

At present, I am still unable to boot into either of my two partitions.

Thank you.

---

### Post by oldfred on 2014-05-12
Moved to Other OS since Mint.

Mint must not be as UEFI capable as the Ubuntu version. Do not know about Mint.

---

