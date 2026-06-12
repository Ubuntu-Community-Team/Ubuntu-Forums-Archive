---
title: "thinkpad won't boot Ubuntu or install CD"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by webmonkees on 2007-02-12
Trying to fix up a old IBM Thinkpad T21. Using Alternate i386, and sometimes it installs.
Right now, there's a functioning ubunto on the main HD, but it never gets there.
Starting Up ...
and a blinky cursor. That's all I'll get. Sometimes when the clouds are just right and I hold my foot up to a certain angle, it'll boot. 
This is not to my standard of reliable computing. Barely.

Problem is, 
the Ubuntu, xubuntu, and other disk images I've downloaded will give me a menu,
but attempting to start them will either give me a blank screen
or, in text/(recovery) mode, end with the last entry about IRQ 11 and hangs at that point.

Something I may have missed somewhere along the line, I think.

Okay, there's a few possibilities for problem causes.
1: Thinkpad DVD doesn't like the CD. CD is a cheap Optimum disk. Even tried a 4x burn.
2: I didn't do anything other than standard 'wipe the HD' when initially installing Ubuntu.
3: Memory is too low. It's the stock amount, but again, Ubuntu, when it decides to actually
boot, does work..

up until I can't put off rebooting anymore. About the third reboot is when
it goes bye-bye and doesn't want to play nice.

Things I'm going to try:
A DVD image of the install disk. Trying to boot something to fdisk it into regular/swap partitions. 

Any help would be appreciated.. like suggested sizes. the HD is 20 Gig, last I recall.

---

### Post by Jussi01 on 2007-02-12
Be helpful if you gave us a few extra bits of info:

- what are the exact specs of the machine?

- What is the exact(verbose) error message you are getting?

- Have you checked th md5 of the cd you are trying to use?

Cheers

Jussi

---

### Post by webmonkees on 2007-02-12
Specs: 128MB 800Mhz Pentium III Bios 1.16 20GB, S3 Savage IX8 Video card, 

Here's what I've tried:

The original install was 6.06. It had been awhile, so I wasn't sure 
about the version until now.
it's the one I initially installed, had the boot problems, got hold of the 6.10 alternate,
installed that, and now neither version will load up Ubuntu.

It (6.06) freezes at 
''Uncompressing Linux.. Ok, booting the kernel''

While 6.10 just give me a blank screen with a blinking cursor, no HDD or CD activitiy.

All of these fail to boot:

*ubuntu-6.06 (alternate).iso (no md5 available)

ubuntu-6.10-alternate-i386.iso 
(md5 for image:549ef19097b10ac9237c08f6dc6084c6)

xubuntu-6.10-alternate-i386.iso
(md5 for image:fd706420fb2c1529707658ba43e9554a)

These match the md5s listed on the host webpage.

ubuntu-6.10 dvd iso -no way to check md5s on this due to lack of DVD drive on this computer..


I'm not sure how to check the CDs for integrity; the testing program in the Ubuntu menu
just goes to a blank screen (well, the 'booting the kernel' screen in 6.06)

 However, I checked random files and they have matching checksum hashes. All of the downloads are straight from the mirrors linked on Ubuntu.


In as far as error messages; when it worked, there was no problem; I updated the kernel, browsed the Synaptic libraries, even rebooted, once or twice. The only error message

I get is the screen blinking and no activity instead of loading. 

The only messages I can get are from the text mode:

It would take awhile to transcript the text, but here's the last six lines it always shows
when attempting text mode boot/install, which look like where it goes downhill:

[17279572.136000] ****SET: Misaligned resource pointer c7e30da2 Type 00 Len 42
[17279572.136000] pnp: Device 0:0b activated.
[17279572.136000] 00:0b: ttyS0 at I/O 0x3f8 (irq=4) is a 16550A
[17279572.136000] ****SET: Misaligned resource pointer c7e30da2 Type 07 Len 0
[17279572.136000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[17279572.136000] ACPI: PCI Interrupt 000:00:03.1[A] -> Link [LNKC] ->GSI 9 (level, low) -> IRQ 9

I set the IRQs to automatic earlier it would give the identical message except IRQ 11.

The only thing I did different from usual was following some instructions specific to T21s:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21)
which was pretty much this line:
# kopt=root/dev/hda1 ro acpi=off apm=on 

From the CD/DVD Ubuntu menu,
pressing f6 and inserting the ro acpi=off apm=on makes no difference in hangups.


At this point I'm thinking of getting something that can let me format and partition the drive as it does little to nothing other than blank out at the loading screen and fails.

It's just odd that it worked and then didn't. Even the installation CD should work, but doesn't. It did before, of course..

Now, I'm experimenting with this T21 because it wasn't reliable using Win2000, and perhaps it has some issues unrelated to Ubuntu; I had burnt the DVD image as I had heard the drive that comes with this model can sometimes have difficulty reading CDs..

---

### Post by webmonkees on 2007-02-13
Further clues: seems there's a chronic problem with the combo ethernet/modem card which generates an IRQ conflict. Ah, the classic tech problem. 
"redundant entry in serial pci_table"

So.. I want ethernet, and it all worked at a time. Seems at some point the modem has been activated, which causes the conflict. Still researching how to re-disable the modem;
it wasn't enabled earlier which allowed booting.

I found more exact information due to trying a different Debian install disk, which gave out a more Google-able error message.

Okay, once again with feeling:
what command option can I use to avoid it running into the IRQ problem?
apci=no didn't do the trick.

---

### Post by webmonkees on 2007-02-13
Yep, it's definitely the ethernet card. Re-installed it, no booting. The verbose (text) boot was giving me a clue, a bit of reverse-engineering let me narrow the IRQ problem
down to the ethernet card.

It would have been nice if the boot process would have  told me something  rather than just sitting there blinking. . Even the text mode error message was unclear, it took another Debian installer to clarify the problem..

- Failure mode needs a bit of notice. Even just a beep would suffice.

---

### Post by nekonoko on 2007-02-14
I'm experiencing the same issue with my Thinkpad T21; it seems like you need to boot it several times before it will finally get past that point. If you do stumble across a solution it would be great to hear!

---

### Post by H9338 on 2007-02-20
Hi, I had similar boot-up problem with Ubuntu 6.06. However, I solved the problem by using an older version Ubuntu 5.10. I then upgrade to 6.06 via the internet. Give it a try.:popcorn:

---

### Post by tgalati4 on 2007-02-21
Installing 6.06 really needs 256MB or 128MB and a decent sized swap disk.  Older distros used less RAM and therefore worked on older hardware.  The thinkpad is a decent machine for Ubuntu, but you do need to upgrade the memory otherwise it is painfully sluggish. 

I had the same problem with an old Dell Inspiron 7500 (Pentium III, 1 GHz) with 128 MB RAM.  Crashed the first time with Live 6.06.1.  Booted with 5.10 disk and set up a 1 GB swap drive then the 6.06.1 Live disk worked.  Install was slow, but complete.  107 upgrades went smoothly.  Put in another 128MB of RAM and now it runs sweetly.

---

### Post by The_Major on 2007-02-24
Same thing happens with a fresh install of Feisty (Herd 4), it takes three attempts to boot up! Any one have any clues how to solve this?

---

### Post by The_Major on 2007-02-24
> **The_Major said:**
> Same thing happens with a fresh install of Feisty (Herd 4), it takes three attempts to boot up! Any one have any clues how to solve this?

After searching around a bit, I found [this page]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21")

Follow Carpulon's instructions for editing /boot/grub/menu.lst and add  acpi=off apm=on save the file and issue the following command. 

sudo update-grub

I have now had four successful boots in a row! :)

---

### Post by harryc on 2007-04-06
> **The_Major said:**
> After searching around a bit, I found [this page]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21")

Follow Carpulon's instructions for editing /boot/grub/menu.lst and add  acpi=off apm=on save the file and issue the following command. 

sudo update-grub

I have now had four successful boots in a row! :)The_Major, Is the machine still booting? I solved the same problem on a T-21 by removing the Mini PCI adapter card per a tip found in another thread.

---

### Post by The_Major on 2007-04-10
> **harryc said:**
> The_Major, Is the machine still booting? I solved the same problem on a T-21 by removing the Mini PCI adapter card per a tip found in another thread.


Yep no problems at all, I have just installed Feisty Beta on it as well!!!

---

