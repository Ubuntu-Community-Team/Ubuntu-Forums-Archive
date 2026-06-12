---
title: "Kenrel panic - not syncing: VFS: Unable to mount root fs on unknown-block"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Tilulii on 2007-09-14
I'd like to switch a computer to Ubuntu (newest (?) version from ubuntu.com)

Okay, looked this up already, the almost same errormessages, but can't figure it out.

Problem:
Trying to install Ubuntu on a IBM ThinkPad 600X, and the following errors come up every time:
[0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[181.563259] invalid compressed format (err=1)
[181.581722] Kernel panic - not syncing: VFS: Unable to mount roof fs on unknown-block(104,1)
[181.581968]

And it hangs there. Is the problem the BIOS? Too old?

If you look from
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4FYS2U](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4FYS2U)
the newest BIOS is from
1.11  	ITET55WW  	30 Nov 1999  	Current Release
and it is still from 1999 :)

Updating BIOS, great, if I just could figure out how to update it, as this damn computer (or that damn computer, there are a few of the, all working... semi...) doesn't have a disk-station, and just did the BIOS-update-floppy (feels kinda stupid, did quite some work to get my hands on a floppy)...

So if anyone knows what to do, I'd be glad. The other specs on the computer:
Runs a Win XP (soon hopefullo no more :)
HD IBM Travelstar DARA-206000 E182115
Memory * 128 (different speeds) IBM FRU:19K4653 and IBM FRU:19K4653

The computer has a CD-station, if you guys know how to update the BIOS from a CD (or doing the booting-thingie on a CD), I'd be glad to know...

CD: FRU:05K9267

I have a external floppy-drive, that is from my sisters ooold computer, a DELL P/N 66942, but I don't know if it is bootable, as it goes to the com-port... (or the bigger one of the, in the back :)

It's not too easy! The 600X has a 450Mhz PIII, if I remember correcty (the computer is half dissassembled, beside me at the moment :).

If you can do something, please do

Best Regards
Elmo

---

### Post by dwhitney67 on 2007-09-15
I think if you edit the grub default choice with acpi=force, the BIOS issue can be overcome.

When you system is booting, usually there is time ticker and if you press no keys on the keyboard, it boots into the default OS.  You need to take action... press a key!

Then when you see the selection choices available, using the arrow key, highlight the Ubuntu entry.  Then press the 'e' key (to edit it).

A typical menu.lst entry looks like this:

[FONT="Courier New"]title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=db2cab2c-8475-43c2-9862-95b2880a58d1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault[/FONT]


Of course, when you are editing with grub you will not see everything exactly as shown above.  I would ensure that the line containing "root" is correct.  Also for the line containing "kernel", append to the end "acpi=force".

If you only have one HDD, and it contains multiple partitions, say 1, 2, 3, and 4, and your primary linux partiton (for /) is on /dev/hda3 (i.e. the 3rd partition), then your "root" entry should be set to (hd0,2).  The "2" is equal to the Linux partition number minus 1.

Read the grub instructions as printed on your screen.  This is not rocket science.  When you finish editing, press the "enter" key, followed by the "b" key to boot.  Don't forget to add the "acpi=force"!

P.S.  If this should work and you are able to boot into Ubuntu, the first thing I would do is examine your menu.lst file in /boot/grub.  Make sure that you edit it to appear exactly like the information you manually entered so that you will not have to do it again and again each time you reboot.

---

### Post by Tilulii on 2007-09-16
Ok. So is this solution one I can do even if there is no Linux on the machine yet? Everything is formatted to, FAT or NTFS, for now. So if I already need to have Linux on this machine, it will fail!

Anysways, my chica is working onm the laptop at the moment, so can't even try :)

But I'll try later on...

---

### Post by dwhitney67 on 2007-09-16
I guess I do not fully understand your situation.  If you want to install Linux, you are going to need unused space on the HDD.  If you plan to have a dual-boot system (with Windoze being the primary OS), then you need to use some type of "partition manager" to free up space on your HDD so that Linux will have room to live.

It is possible to fit Linux on as little as 8GB, but I would recommend at least 15GB if you plan to save personal work, install "toys", etc.

In conclusion, you cannot install Linux in a partition that is currently holding the Windows OS.  Doing so will cause you to wipe out Windows.

---

### Post by Tilulii on 2007-09-16
Yes, I am aware of that. On this 'big' computer I have installed dual OS, but on the laptop the plan is to re-format the whole (whopping 12,5gb!, retro laptop, that's why we want to keep it, chica has an eye for estethic things :) hd, and run only Linux. And on this computer, you could format during installation, but can not get that far! I can select 'Install/Run Ubuntu', and after that the computer freezes, no formatting, no Linux :(

---

### Post by schorsch on 2007-09-16
I'd guess with only 128 MB RAM you should try xubuntu or any other small distro instead of ubuntu as you need 256 MB RAM to run Ubuntu ...

---

### Post by Tilulii on 2007-09-16
It has two 128, and from somewhere (magic?) threre is 327mb or something when I boot. Don't know from where the extras comes from, but I don't complain :)

---

### Post by dwhitney67 on 2007-09-16
Even if you have only 256MB, I think 'schorsch' is right.  You should consider Xubuntu.  If you are adamant about using Ubuntu, consider booting from the Alternate CD.

P.S.  RAM generally comes in units of 32, 64, 128, 256, 512, and I believe 1024MB.  Let's see, 327 - 256 = 71MB.  Something is wrong... I doubt you have more than 256MB.

---

### Post by Tilulii on 2007-09-16
I can't remember the exact amount of RAM. Have to check it out, just for curiosity, migt be 256 + 64 makes... uh... 320ish.

Anysways, I'll give Ubuntu a try, and then try something else, this is a good way to spend some time, and avoiding to start on your studystuff :)

So, the problem still resides, can I use 67's idea, when there is no Linux installed?

And this Ubuntu just hanged up, two times, a moment ago. No errormessages, no nothing. Everything freezes, and mouse and keyboard stops responding.

Weitrd, I say. But you get used to stuff like that, after all, had a Windows computer forquite some time :)

---

### Post by Tilulii on 2007-09-17
Aaand, hup.

Up we go!

---

### Post by SonicSteve on 2007-09-29
Hi bud,
I have the exact same trouble on a 600E. My only guess is that the hardware beginning to fail. Here's why,
It used to run XP very well.
I was even able to run ubuntu not that long ago. One day a customer needed a hard drive, so I sold them the 20GB that was in the laptop. 
After that no matter what disk I use the laptop either gives stop errors while installing XP or Kernel panics exactly like yours not matter what version of Ubuntu I try. Hmmmmm. 
some part of the hardware must have failed somehow, I can't explain it but I can't load up anything anymore even though I know the disks I've tried are good.

---

### Post by SonicSteve on 2007-09-29
OK so I eat my words,
The live CD of 6.06 is working, I guess the 600 series of laptops don't like the newer kernels?
I still can't explain why I can't install XP anymore.
********EDIT*******
Ubuntu 6.06 is up and running perfectly (minus sound) I'm connecting to the internet and once again ubuntu has done something that windows couldn't. In this case simply install. I do wish that 7.04 would work but I bet that I can 6.06 to look pretty good before long.

---

