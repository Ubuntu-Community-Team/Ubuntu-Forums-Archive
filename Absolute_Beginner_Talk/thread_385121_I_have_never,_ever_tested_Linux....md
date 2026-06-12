---
title: "I have never, ever tested Linux..."
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by ink3 on 2007-03-15
but I finally thought I´d give it a whirl when I read a quite favourable review of Ubunto a couple of days ago. The idea of the Live CD was what finally won me over, being able to test it without having to install anything.

BUT, it absolutely refuse to work. What happens is this:

I choose "boot in safe mode" and it says "loading Kernel", "loading /casper/vmlinuz" and "loading /casper/initrd.gz" after which the screen becomes black with a white blinking cursor in the upper left corner. And then nothing happens.....at all. I thought the CD i burned might be faulty so I choose "check cd for errors" which results in exactly the same thing. 

The problem is, I don´t know enough about linux to even know if this indicates a faulty disc or not. But I did burn it with verification on, so it should be ok.

So, if anyone has some pointers as to what I could do to finally get the Linux experience after all these years in windows I´d be much obliged:-)

My machine:

Mainboard :	MSI Nash
Chipset :	nVidia nForce 410
Processor :	AMD Athlon 64 X2 4600+ @ 2400 MHz
Physical Memory :	2048 MB (2 x 1024 DDR2-SDRAM )
Video Card :	Nvidia Corp GeForce 7900 GTX
Hard Disk :	ST3250824AS (250 GB)
Hard Disk :	ST3250824AS (250 GB)
Hard Disk :	ST316081 (160 GB)
DVD-Rom Drive :	HL-DT-ST DVDRRW GSA-H20L
DVD-Rom Drive :	IDE-DVD DROM6216
DVD-Rom Drive :	TC3123B FAM525P SCSI CdRom Device
Network Card :	Atheros Communications Inc AR5006 family 802.11abg Wireless NIC

---

### Post by Tipo on 2007-03-15
Okay, this may be a dumb question :P, but do you know which version of the LiveCD you burned?

Your processor is an AMD, and Ubuntu is available in several different architectures, x86, AMD, and PPC. Make sure you burned the AMD version...

---

### Post by lamalex on 2007-03-15
> **Tipo said:**
> Okay, this may be a dumb question :P, but do you know which version of the LiveCD you burned?

Your processor is an AMD, and Ubuntu is available in several different architectures, x86, AMD, and PPC. Make sure you burned the AMD version...

only if he wants to run a 64 bit system which he might not, all AMD processors are not 64 bit architecture. I run a 32bit system, which is standard ubuntu install even though I have an AMD 64 processor. As long as he's not using a powerpc cd, he's good to go.



as for your cd, if the check cd doesn't even run try burning it again at a slower speed. let me know if that helps.

---

### Post by Kobalt on 2007-03-15
And when you burned your CD (which you should burn not more than 4x I advise) then don't forget to check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29").

---

### Post by ink3 on 2007-03-15
I want the 32 bit version so I downloaded (and the md5sum is correct on that one) the following file: ubuntu-6.10-desktop-i386.

I´ll try burning a new version of it later this evening. 

Thanks for the help so far.

---

### Post by ink3 on 2007-03-15
Ok, I burned a new version of it. There is no way for me to set the speed in the burning software, but this one also verified as ok. Is there a way to check the cd from Windows?

The result is exactly the same with this disc, and I´m inclined to believe that the discs are correct, and the problem is somewhere else.

Any ideas?

---

### Post by Kobalt on 2007-03-15
You can try to boot with then 'noapic nolapic' options : boot up normaly with the install CD in your drive ; when you reach the boot menu ("install/start Ubuntu, test CD, etc.") press F6 and simply add > noapic nolapic at the end of the line. Then press Enter...

---

### Post by ink3 on 2007-03-15
Ok, tried with noapic nolapic. Still the same result. Nothing happens. How long should it take to boot from the cd?

Another thought. I have had some problems with the USB on this machine, it seems a bit...fragile? Could this have something to do with it?

What should happen after "loading /caspar/initrd.gz"?

---

### Post by lamalex on 2007-03-15
you should come to a boot splash, perhaps try using different burning software? what software are you using now? Also check your md5sum. heres a tool that works on xp [http://www.download.com/HkSFV/3000-2248_4-10157350.html?tag=lst-0-5](http://www.download.com/HkSFV/3000-2248_4-10157350.html?tag=lst-0-5). there are tons. the md5 sum it should match is here [http://cdimage.ubuntu.com/releases/edgy/release/MD5SUMS](http://cdimage.ubuntu.com/releases/edgy/release/MD5SUMS)

---

### Post by infol on 2007-03-15
do you have any hardware connected to your computer via usb?

if so, try disconnecting everything (except mouse, keyboard and monitor, of course) to see if it boots correctly. 

i used to have issues booting 6.06 when my external hdd was connected, although it detected it fine if i connected after logging on to the system....

Good Luck!

---

