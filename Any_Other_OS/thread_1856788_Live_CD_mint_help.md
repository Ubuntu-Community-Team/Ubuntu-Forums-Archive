---
title: "Live CD mint help"
date: 2011-10-09
forum: Any Other OS
---

### Post by tehcavil on 2011-10-09
OK I realize this should probably go on the mint forums, but I wanted to try out a live CD of mint right? I know the cd works (it's the 64 bit with no restricted codecs one), because i used it as a live on my laptop, however, I cant seem to use this (or any) live cd of any system on my computer.

No matter how i change the boot order in the bios (even disabling the hard drive option altogether), it ALWAYS boots from the hard drive into my installed ubuntu). I can't use any live CD's... help!

---

### Post by hansdown on 2011-10-09
Hi tehcavil.

Which version are you using?

Also, which hardware are you using?

---

### Post by tehcavil on 2011-10-09
> **hansdown said:**
> Hi tehcavil.

Which version are you using?

Also, which hardware are you using?

Linux Mint 11 64 bit no codec

EDIT: my installed ubuntu is 11.04

Hardware:

GIGABYTE GA-990FXA-UD5 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard

AMD Phenom II X6 1100T Black Edition Thuban 3.3GHz, 3.7GHz Turbo 6 x 512KB L2 Cache 6MB L3 Cache Socket AM3 125W Six-Core Desktop Processor HDE00ZFBGRBOX

HITACHI Deskstar 7K3000 HDS723015BLA642 (0F12114) 1.5TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive

G.SKILL Ripjaws Series 16GB (4 x 4GB) 240-Pin DDR3 SDRAM DDR3 1066 (PC3 8500) Desktop Memory Model F3-8500CL7Q-16GBRL

LITE-ON 24X DVD Writer 24X DVD+R 8X DVD+RW 12X DVD+R DL 24X DVD-R 6X DVD-RW 16X DVD-ROM 48X CD-R 32X CD-RW 48X CD-ROM Black SATA Model iHAS424-98 LightScribe Support

those are copypasta from my order where i bought them

---

### Post by tehcavil on 2011-10-09
bump

---

### Post by Perfect Storm on 2011-10-09
Moved to Other OS/Distro Talk.

---

### Post by hansdown on 2011-10-09
That is an awesome setup, tehcavil.

Can you post the bios version?

---

### Post by tehcavil on 2011-10-09
> **hansdown said:**
> That is an awesome setup, tehcavil.

Can you post the bios version?

How do you check the Bios version?

---

### Post by hansdown on 2011-10-09
> **tehcavil said:**
> How do you check the Bios version?

restart the computer and hold the delete key  while the computer is autodetecting the hard drives. The BIOS configuration screen will show the brand and version.

Or copy and paste this in a terminal....

```
sudo dd if=/dev/mem bs=32768 skip=31 count=1 | strings -n 10 | grep -i bios
```

Mine is below.

---

### Post by tehcavil on 2011-10-10
on ubuntu installed i got


1+0 records in
1+0 records out
32768 bytes (33 kB) copied, 0.00052095 s, 62.9 MB/s
IBM COMPATIBLE 486 BIOS COPYRIGHT Award Software Inc.
Award Modular BIOS v6.00PG

---

### Post by Johnb0y on 2011-10-10
tried re-burning the ISO? might be an issue with your drive not picking it up.

---

### Post by tehcavil on 2011-10-10
> **Johnb0y said:**
> tried re-burning the ISO? might be an issue with your drive not picking it up.

I already used it to install mint on my laptop so i think the CD's good.

---

### Post by varunendra on 2011-10-11
> **tehcavil said:**
> I can't use [COLOR=Red]**any**[/COLOR] live CD's... help!
Have you tried 'many' CDs? If so, then the only things to doubt are:

[LIST]
[*]BIOS settings for booting from CD
[*]Optical Drive's connection
[*]Optical drive itself (although your specs are impressive and LiteOn itself is a good brand)
[/LIST]
Additionally, make sure the CDs you are trying are written at minimum possible speed. Also, try writing it using a different drive if all of them were written using the same drive (your laptop's? Their writing capabilities are often weak). I once had a samsung dvd writer which could read CDs & DVDs written on other drives or on itself, but the DVDs written by it were detected as 'blank' on all other drives (while they were readable on itself).

If your target is booting the system anyhow, rather than booting 'from that particular drive', then a Live USB is a goot option.

If this doesn't help, try toggling the SATA 'modes' in your BIOS (often they are 'enhanced', 'compatible', etc.). If possible, a few screenshots of your BIOS' relevant screens may help us understand it better, because a guide I found about your BIOS version ([here]("http://www.answersthatwork.com/Download_Area/ATW_Library/Hardware_Maint/HW___6-Award_6.00PG_BIOS_setup_guidelines.pdf")) doesn't even list SATA as an option ;).

---

### Post by k357k9 on 2011-10-11
> I already used it to install mint on my laptop so i think the CD's good.
May I suggest that you burn a brand new fresh copy at 4X or less just to be sure? I have been "burned" more than once thinking I had a good copy and found out the hard way that I didn't.

---

### Post by tehcavil on 2011-10-19
Well an update: I really need to fix my comp now as the update to 11.10 nuked my computer (get a blank or fuzzy screen when i try to boot up). 

I tried setting the bios options to boot from usb but It said "boot error" when I made a live usb and tried to boot from it (mint). On a side note, the power cable connecting the power supply to the CD drive was burned out (seriously melted) so that may have been the cause of not being able to boot from CD.

I'm on my way to the computer store to get a replacement cable for the power supply and then try to boot from CD again.

(although this doesn't explain why I can't boot from a live usb either).

---

### Post by tehcavil on 2011-10-21
OK I went to the store and bought another cable to connect my power supply to cd drive, still cant boot from cd but now i can from hard drive into some sort of command line prompt:
says:

> Busybox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for list of built-in-commands.

(initramfs)

i dont know what that means.

---

### Post by varunendra on 2011-10-22
It means grub is unable to find or load boot files or partition. The reasons may be any of: corrupt partition, corrupt installation, corrupt fstab file, ....even a faulty IDE cable.

To start zeroing the problem and correct it if possible, you will need to boot from either a cd or a USB in live mode. So unless you sort out the problem with booting off Live CD/USB first, I'm afraid the current hdd-booting issue is not going  to be solved either.

---

