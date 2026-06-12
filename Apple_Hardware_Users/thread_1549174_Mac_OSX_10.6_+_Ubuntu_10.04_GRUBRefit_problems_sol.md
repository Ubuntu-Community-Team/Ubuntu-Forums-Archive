---
title: "Mac OSX 10.6 + Ubuntu 10.04 GRUB/Refit problems solved"
date: 2010-08-09
forum: Apple Hardware Users
---

### Post by I8chowder on 2010-08-09
I spent hours reading this forum and the web about how to install Ubuntu 10.04 server alongside Mac OS 10.6 in hopes of getting my Mac Pro 4,1 set to go. Using nearly any of the instructions available, I was able to successfully 'install' ubuntu; the issue was always loading the system.  When I selected the ubuntu icon from refit, I was always presented with one of:

  - a blinking cursor that would never go away
  - a message from grub about the operating system being missing

 I never actually got to a grub boot screen. I tried many variants on the install theme including:

  - creating a dedicated grub boot partition on which to install grub
  - removing the grub boot partition so my disk was formatted as:
     (partition 1: efi boot partition; 2: mac OSX; 3: ext 4 ubuntu root) 
     this eventually worked after the tweaks below...
   - installing grub on /dev/sda3 (the ubuntu partition)
   - and installing grub on /dev/sda (the MBR)

 of course each of these variants was preceeded with a lot of time consuming clean up in between.

 What finally worked was the following (hopefully this will spare someone a few days of hair pulling):

  1) Begin with clean OSX install
  2) Resize OSX partition and add a new partition for ubuntu using OSX disk utility:
    (hard disk now containing 3 partitions: 1: EFI; 2: Mac OSX; 3: temporary to be ubuntu)
  3) Reboot with Ubuntu CD, installing ubuntu onto /dev/sda3. You'll need to 
      select the manual partition option, make /dev/sda3 ext4 and set it to the 
      mount point '/'. I'll use a swap file, so there is no swap partition.
  4) Install grub onto /dev/sda (the MBR)
  5) Reboot/shutdown.  You should now be able to boot into Mac OSX, but at this point
       I could *not* boot into ubuntu -- my machine would always hang before getting to a 
       grub 2 screen...
  6) Boot from Ubuntu CD and select 'rescue a broken system'
  7) continue through setup and get a shell in the installer environment:
  8) now, chroot into the existing (unbootable) system
      # /mkdir /mnt/r
      # mount /dev/sda3 /mnt/r
      # mount --bind /dev /mnt/r/dev
      # mount --bind /proc /mnt/r/proc
      # chroot /mnt/r

  9) ** Downgrade grub **. I never expected this to work, but it seems to have done
      the trick
      # apt-get purge grub-common grub-pc
      at the same time, move the /boot/grub folder somewhere else as backup
      then install grub legacy:
      # apt-get install grub
      # update-grub
        (do a sanity check that the menu.lst looks like its pointing to the correct place)
      # grub-install /dev/sda 
        (onto the MBR)

  10) reboot.  Now grub loads, and boots into ubuntu 10.04 server; mac os x boots 
       as normal and refit shows two icons as desired!

  
  Note that after my first working install, I got a bit greedy and tried going back into Mac OSX and adding a FAT32 partition between the OSX partition and the unbutu partition.  This ended up making the ubnutu partition /dev/sda4, so I knew that I would need to run update-grub again and reinstall.  However, I was surprised to find that this didn't work. At grub-install, the installer would complain about a broken stage 1.  It appears that for some reason, grub was not happy with ubuntu being on the 4th partition... happily, I was able to go back into Mac OSX, remove the fat 32 partition and get back to where I started.

Hopefully this post will help someone else out!

---

### Post by OpenOS on 2010-08-09
That is awesome could this be done on an iMac 11,2 ??

---

### Post by sircram on 2010-11-27
When you create the Ubuntu partition in Disk Utility, what do you format it as? And can you please elaborate on the process for step 3? Thank you!

---

### Post by vuarnet on 2011-01-09
Thanks for this!

I installed ubuntu 10.04 64-bit when I was running OS X 10.5 on my 4.1 MacBook, and then I upgraded to Snow Leopard (10.6)... Everything worked fine until I recently tried to switch my 10.04 64-bit to 10.10 32-bit. So I formatted my 10.04 64-bit installation partition and tried installing the 10.10 32-bit ubuntu from "scratch". Even re-installed rEFIt. I get the same problem -- a white cursor that hands indefinitely and no grub.

I've tried almost everything, and no dice. I'll give this a shot and see if it works for 10.10 too and report back.

Thanks again!

@sircram: You format it in Mac Disk Utility as FAT32 (Windows). When you boot from the ubuntu live cd, just open System>Administration>GParted Partition Editor, delete the FAT32 (windows) partition you just created and create a new one for swapspace first (place at the "beginning"), at a size of about 5% larger than your virtual memory (RAM). Then you can create your primary ubuntu partition...just format to EXT4 with a mount point of / and place at the "beginning" as well.

In regards to "more detail for step 3," you need to boot using the ubuntu live cd (burn from Mac Disk Utility). Burn the disc at the slowest speed possible to increase reliability. If you have rEFIt properly installed, an option to "Boot Linux from CD" should show up. When ubuntu finally starts (it takes FOREVER to boot from the cd, but rest assured it takes a "whopping" 10-seconds to boot once installed!)
Here is a *general* walkthrough that can provide a good level of detail for you: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")

---

### Post by vuarnet on 2011-03-21
l8tchowder... you are my hero.

thank you so much for this tut. worked PERFECTLY for me. i was struggling with all kinds of steps, and nothing would work. i'm writing this, appropriately, from my fresh install of Ubuntu 10.10 64-bit ... gah i missed ubuntu.

thanks again!

---

### Post by skullmunky on 2011-03-21
I'm curious - the community documentation says to install grub onto the partition, not MBR.  Why is this?   And if that's the case how come your method works?

---

### Post by vuarnet on 2011-03-21
> **skullmunky said:**
> I'm curious - the community documentation says to install grub onto the partition, not MBR.  Why is this?   And if that's the case how come your method works?

i'm not exactly sure, but i think it has something to do with the difference between Mac OS 10.6 and 10.5. i never had a problem with grub not loading when i originally installed it on sda3 (the ubuntu partition) with 10.5, but when I tried to upgrade from 32-bit 10.04 to 64-bit 10.10, i had to format my ubuntu partition and pretty much start from scratch. and when i tried the exact same thing on 10.6 that worked for 10.5, it wouldn't load. if i had to guess, i'd say that the 10.6 firmware update doesn't allow any bootloaders that are not on MBR to stop you from loading an unauthorized OS, such as Ubuntu.

EDIT: and fwiw i only used the part toward the end (chroot unbootable system & downgrade grub). everything else i installed per the community documentation and it went fine. installed ubuntu desktop 10.10 64-bit on sda3 and my swap partition on sda4. everything with the install went fine, except for grub not loading and chroot-ing the ubuntu installation and downgrading grub did the trick. all i did was boot using the same live cd (Ubuntu 10.10 desktop 64-bit in my case) and opened up terminal and went through those last couple of steps (chroot ubuntu partition and downgrade grub).

also, after `# update-grub` i was prompted with a menu.lst did not exist, and asked if i wanted to create, one, and i selected YES and it worked well for me.

---

### Post by skullmunky on 2011-03-22
Thanks, this solved my problem too.  In my case I didn't need to switch from Grub 2 to Grub 1.  I had a working system with Ubuntu 10.10 on /dev/sda3, grub  installed on /dev/sda3 during installation, and Windows XP on /dev/sda4 with the Windows bootloader installed to the MBR.  

I booted to the Live CD (Note: I discovered it's important to match the architecture - I had 10.10 x64 installed, so had to boot a x64 live CD)

then followed this part of your steps:
```

sudo /mkdir /mnt/r
sudo mount /dev/sda3 /mnt/r
sudo mount --bind /dev /mnt/r/dev
sudo mount --bind /proc /mnt/r/proc
sudo chroot /mnt/r

```

then just installed grub

```

sudo grub-install /dev/sda

```

all fixed!  thanks!  chroot always scared me before but now I start to see it's magnificence.  :KS

---

### Post by dubmartian on 2011-03-23
At step #4 you can choose to have grub installed on /dev/sda3.

-B can be used instead of --bind. I always bound /dev/pts and /sys when chrooting to a system to fix grub, but obviously not needed now. Was it ever?

Since Ive also spent a lot of time with grub problems and waiting for the live cd boot, I'm surprised the "Super Grub Disk" isn't mentioned more. I tried the Parted Magic utility recently and was shocked how convenient Super Grub Disk is. With a broken grub or NO grub, just Boot the CD and have Super Grub Disk 2 scan for any OS. You'll get a list similar to your grub.cfg to choose from. It takes seconds and It's really that simple.

Edit: for convenience you can chroot with one line: sudo mount /dev/sda3 /mnt && sudo mount -B /dev /mnt/dev && sudo mount -B /proc /mnt/proc && sudo chhroot /mnt
(creating /r is optional of course. If your /mnt directory is empty, there's no need for /r)

---

