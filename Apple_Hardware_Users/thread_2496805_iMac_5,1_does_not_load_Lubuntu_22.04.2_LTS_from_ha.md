---
title: "iMac 5,1 does not load Lubuntu 22.04.2 LTS from hard disk"
date: 2024-04-13
forum: Apple Hardware Users
---

### Post by d018398 on 2024-04-13
Hi,

I try to revitalize my iMac 5,1 (Late 2006 version, Model A1207, Order No. MA589xx, Intel Core 2 Duo) with Lubuntu 22.04.2 LTS. 
I can start Lubuntu from USB, when adding "noefi nosplash nomodeset" to GRUB vie the "edit" function. 
This way, I managed to instal Lubuntu on the harddisk of the iMac.

When starting Lubuntu from the harddisk, the start-up hangs at the command "loading initial ramdisk":
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293606&stc=1[/IMG]

The following shows GRUB starting OK from USB:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293607&stc=1[/IMG]

When starting the iMac from the hard disk, I edited GRUB in the same way (as via USB) - but after that, the installation stalls:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293608&stc=1[/IMG]

Do you have an idea, what I am doing wrong here? 
What should be entered in the GRUB menu to get the start-up from Harddisk run through without issues?

I am adding some hardware information about the CPU, if it helps. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293609&stc=1[/IMG]

Let me know, what else you need to analyse this issue.
I can extract data from the system, after booting via USB.

Thx in advance and best regards, 
Jochen

---

### Post by MAFoElffen on 2024-04-13
Why not a current installer version of 22.04.4?

Note: On my 2007 MAC MacBook, it has 32bit EFI, but 64bit Intel Core Duo. Even though it installed 64bit EFI file for Ubuntu, they do not work. I had to hack it to install Grub2 as 32bit. Research it to see if yours is that same.

Google it. I have some life priorities at the moment that prevent me from looking up what I did (I have limited time before I have to get back to that), but that's how I found the answer for mine...

---

### Post by guiverc on 2024-04-14
I'll suggest you follow advice from MAFoElffen

The original post though has me confused.. 

- there is mention of 22.04.2; the 5.19 kernel matches that (*first image*,* third & fourth too*)
- *second* image however shows grub 2.02~beta2 which reads like *xenial* or 16.04???  I'm lost at this point as how does that relate (`grub2 | 2.02~beta2-36ubuntu3.32 | xenial-updates/universe` is from 2016)

I see no mention of 16.04; I'm lost with how that second picture relates.

Personally, when I have strange older hardware, I opt for a GA kernel stack ISO, ie. a 22.04 or 22.04.1 which use the older 5.15 kernel...   not an *older* HWE kernel (as per 22.04.2)

Did you verify the ISO as per Ubuntu or [Lubuntu documentation]("https://manual.lubuntu.me/lts/1/1.1/retrieving_the_image.html"), and as for testing the write of ISO to media I'd just use another box & ensure the *media validation* completed successfully.   (*if you're unsure of what I'm talking about here; [this link may help]("https://askubuntu.com/questions/993407/is-verifying-isos-downloaded-from-the-official-website-worthwhile/993409#993409") but scroll down to a non-upvoted answer I added to it where I talk about Media Checks*)

---

### Post by QIII on 2024-04-14
Moved to Apple Hardware Users as a more appropriate location.

---

### Post by MAFoElffen on 2024-04-14
Confirmed... Your iMAC 5,1 has 32bit EFI:
```

64-bit Macs that use a 32-bit EFI. These tend to be all of the Core2Duo models from late 2006. More specifically:
    iMac 5,1 &#8211; iMac 5,2 &#8211; iMac 6,1 [COLOR=#ff0000]<-- Yours is here[/COLOR]
    Macbook 2,1 [COLOR=#ff0000]<-- This one is mine.[/COLOR]
    MacBook Pro 2,1 &#8211; MacBook Pro 2,2
    Mac Pro 1,1
    Xserve 1,1 

```
RE: 
[https://mattgadient.com/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/) [COLOR=#ff0000]<-- This site has patched Linux ISO's w/ 32bit EFI files. Includes patched ISO for Lubuntu 22.04.[/COLOR]
[https://github.com/jmstriegel/linux_2006_imac_5.1](https://github.com/jmstriegel/linux_2006_imac_5.1)
[https://github.com/faalbers/EFI_32_BIT](https://github.com/faalbers/EFI_32_BIT) [COLOR=#ff0000]<--- THIS IS WHAT I USED...[/COLOR]

This also works for 32bit EFI:
[https://sourceforge.net/projects/refind/](https://sourceforge.net/projects/refind/)

---

### Post by d018398 on 2024-04-15
Hi MAFoElffen,

thank you very much for your comprehensive write-up. I was following mattgadient when creating the USB stick.

The solution approach that worked for you, did not work for me - unfortunately. After booting from hard disc, the screen remains black - without starting GRUB. 
Maybe this did not work out, because I was not able to execute step 2. in your [recommendation]("https://github.com/faalbers/EFI_32_BIT") "2. Copy content of this repository into that installer USB".
My USB is "read only" and I am not sure, how to copy files to it.

...if you think, that is an issue, please give me a hint, how I can modify my boot USB.

I found another user with the exact same issue as myself > Ubuntu 18.04 installation on old MacBook  2006 from USB worked fine. However, after installation, I had to remove  the EFI32 GRUB files written by the installer. Reason: my Mac wanted  only to boot the kernel using the EFI32 GRUB file given in the article  above (GRUB 2.02beta2). So, if your Mac does not boot the kernel you  might have to fix this! :-)

...I am not sure, in which directory to find the EFI31 GRUB for deletion. I do not know, if & how I can "replace" that file with the "GRUB 2.02beta2". I asked my question in the comments section [here]("https://mesom.de/efi32boot/index.html") - not sure, if I will get a reply.

I will stay on the topic - thx in advance, in case you have some ideas to share.

---

### Post by d018398 on 2024-04-29
Hello again, 

with the great help of Stefan I was able to start my iMac with Lubuntu 16.04. 
It runs stable. This old release is enough for me, since I use the iMac as music player.
If you are interested in more detail, check out Stefan's [site]("https://mesom.de/efi32boot/index.html") or read my specific solution below.
Have a great time.

The followinig steps worked for me:

[LIST=1]
[*]after installation on your harddrive, start a GRUB Shell (GRUB-CLI - Command Line Interface) and review your drives + partitions with "ls" command 
[*]boot into a live system and get the efi file from github
```
wget https://github.com/jfwells/linux-asus-t100ta/raw/master/boot/bootia32.efi
``` 
[*]prepare your grub.cfg file (below is an example, that worked in my case with Lubuntu 16.04)
```
set GRUB_TIMEOUT=3

menuentry 'Standard vmlinuz with delay experiment' --id with-delay {
  set root=(hd0,gpt2)
  echo    'Load kernel ...'
  linux /vmlinuz root=/dev/sda2 nomodeset nosplash
  echo    'Sleep ...'
  sleep 5
  echo    'Load inital ramdisk ...'
  initrd /initrd.img
  echo    'Sleep ...'
  sleep 5
  echo    'BOOOOOOOOOT ...'
  boot
}

menuentry 'Standard vmlinuz without delays NO BOOT' --id without-delay {
  set root=(hd0,gpt2)
  linux /vmlinuz root=/dev/sda2 nomodeset nosplash
  initrd /initrd.img
}

``` 
[*]put both files on your lubuntu desktop so the copy command works 
[*]Execute the following commands in a terminal, to copy the files to your boot partition
```
sudo mkdir /tmp/sda1
sudo mount -o rw /dev/sda1 /tmp/sda1
sudo cp /home/lubuntu/Desktop/grub.cfg /tmp/sda1/boot/grub/grub.cfg
sudo cp /home/lubuntu/Desktop/bootia32.efi /tmp/sda1/efi/boot/
sudo tree /tmp/sda1
sudo sync
sudo umount /tmp/sda1

``` 
[*]restart > and the grub menu should show 
[/LIST]

---

