---
title: "Updating BIOS on a ASUS M5A97 Mobo"
date: 2012-08-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by w201 on 2012-08-11
Can't say that I've ever updated BIOS on a linux system. According to my mobo manual, my option is to use the EZ Flash 2 utility by using a USB stick with the BIOS update. They don't even have a recommended update for a system that's not windows based.

So I just need some pointers, is this EZ Flash method generally a good way to go?

Thanks in advance!

---

### Post by mrgotea on 2012-08-15
I have the same question. Did you go for the EZ Flash?

Tips for ASUS Motherboard BIOS updates welcome.

ASUS M3A78-CM
Release 12.04 (precise) 32-bit

---

### Post by venky96 on 2012-08-15
Honestly I have never trie EZ Flash on My ASUS. I'm dualbooting with Windows so I just downloaded the utility from their website and it flashed my bios in a couple of minutes and I didnt have to use any command line. Hope that helps.

---

### Post by w201 on 2012-08-15
> **mrgotea said:**
> I have the same question. Did you go for the EZ Flash?

Tips for ASUS Motherboard BIOS updates welcome.

ASUS M3A78-CM
Release 12.04 (precise) 32-bit

I haven't tried yet. I was hoping to get a few more replies before trying anything out. 

Venky, can you post instructions on that utility you used? Thanks

---

### Post by venky96 on 2012-08-15
Windows BIOS flash Utility. You can download the BIOS file from ASUS website and use that software and then the software flashes the BIOS. Easy Peasy. But I looked up your mobo [http://in.asus.com/Motherboards/AMD_AM3Plus/M5A97/#download]("http://in.asus.com/Motherboards/AMD_AM3Plus/M5A97/#download")and it doesn't provide you a download for BIOS flash Utility instead asks you to use AMI Flash DOS utility. Cant help with that since i just downloaded the BIOS file and flashed it with Windows BIOS flash Utility.

---

### Post by mrgotea on 2012-08-16
> **w201 said:**
> Can't say that I've ever updated BIOS on a linux system. According to my mobo manual, my option is to use the EZ Flash 2 utility by using a USB stick with the BIOS update. They don't even have a recommended update for a system that's not windows based.

So I just need some pointers, is this EZ Flash method generally a good way to go?

Thanks in advance!

w201 - Are you running dual boot with Windows?

---

### Post by w201 on 2012-08-19
Hi- no, just Ubuntu. Why do you ask?

---

### Post by Lloydb39 on 2012-08-24
Hey, I just built a computer using this motherboard. I'm running 12.04 64 bit on it, pretty successfully so far. Are you guys saying I might have a problem with the BIOS on this thing? Might make me rethink Windows...

---

### Post by mrgotea on 2012-08-26
> **w201 said:**
> Hi- no, just Ubuntu. Why do you ask?

I had a problem running 64 bit Windows on the ASUS M3A78.

I'm not having any problems with 32 bit 12.04, and no dual boot on this machine.

---

### Post by pgmer6809 on 2012-08-26
I would not use EZ Flash.
I have had a very bad experience with it.

If you get into EZ Flash (by say hitting CTL-f12 during POST) and it starts running, it will immediately check whatever is in your drive (floppy, DVD, USB) and if it finds a 'bios' file it will immediately start to flash your BIOS.

There are NO checks -- it does not ask you for confirmation, it does not check if what is on the media is newer than what you have in your BIOS already,   nothing.

Just wide open, hope for the best. What a CRAPPY design for a program that attempts a critical and fragile operation. 
Contrast that with Q-Flash (the Gigabyte equivalent). A world of difference.

Also EZ Flash can fail. I tried it out on one of my ASUS boards, and of course it got the bit in its teeth and went gung-ho and ..... FAILED>
Now I have a hosed MOBO.

You could try using their utility AFUDOS.exe. That seems to work. But it means you have to boot your computer into MSDOS, easy if you have a floppy, if you don't I guess you need to make a bootable USB from FREEDOS or something.

pgmer6809

---

