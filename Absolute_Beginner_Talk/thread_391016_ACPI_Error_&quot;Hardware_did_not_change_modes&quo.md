---
title: "ACPI Error &quot;Hardware did not change modes&quot; and more..."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Milo82 on 2007-03-22
I have been using Ubuntu forums extensively over the past few months setting up my old desktop as a "dapper" server and my laptop as a dual-boot computer. Before messing with my laptop(a Toshiba M40 purchased over a year ago, with I believe nVidia display adapters), I was already having problems booting into XP, getting a blue screen error upon which the system would stop or simply reboot. I then successfully setup the computer as a dual boot, though neither ubuntu "edgy" nor xp ever worked perfectly. I still often got error messages about my BIOS not being fully ACPI compliant. A few days ago I made a mistake after which I decided to do a full reload of both operating systems. Now, I simply have Edgy installed, and it worked fine for a period of time last night, but today reboots just a split second after the Ubuntu load screen appears. It will continue to attempt to boot, then reboot, for as long as I let it.

According to the Toshiba support website my BIOS version appears to be the latest one for my model. 

Here are a few off the error messages I received...I would have more exact error messages but the pause button seems to not work.

After installing Edgy..."Sending SIGKILL to all processes...Please stand by while rebooting the system.
...
ACPI Error(hwacpi-0179): Hardware did not change modes [20060707]

ACPI Error (evxfevnt-0129): Could not exit ACPI mode to enter legacy mode[20060707]"

Now on bootup, as I always have with Linux, I get an error that starts out "Unable to allocate resources..."

It used to be that if that was the only one I saw before the screen changed everything would be fine, now if I only get that I will occasionally be able to boot up the OS, but then it usually freezes. If I recieve more than that, errors which include errors about PnPBIOS my mouse and keyboard wont work. 


In Windows blue screen "BIOS not fully ACPI compliant. Visit http:[www.hardware-update.com](www.hardware-update.com) or contact your vendor for an updated BIOS.  If the new version is not ACPI compliant you can turn off ACPI mode during text mode press f7"(Not exact, but doing a search for this error didn't turn up anything useful"

If someone knows how I can take more accurate notes on the error messages please let me know. Any help you guys are able to give will be greatly appreciated, as I've been working on this for days and days non stop with no success. I have a lot of work I need to do and this is holding me back. Thanks.

---

### Post by thingy on 2007-03-22
Hi!

Ouch! That laptop sounds like its a nightmare.

Ok...in linux, you can easily disable the ACPI functionality by passing a boot time parameter called **noacpi**. Or you can turn off some of the ACPI functionality by passing **acpi=noirq**

To get an idea on how to change the grub configuration file to permanently pass the noacpi or acpi=noirq parameter to the kernel, see this:

[http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/)

See the line where it says:

> 

kernel		/boot/vmlinuz-2.6.BLAH-BLAH-BLAH root=/dev/BLAH ro quiet

needs to be changed to:

kernel		/boot/vmlinuz-2.6.BLAH-BLAH-BLAH root=/dev/BLAH ro quiet noacpi

or

kernel		/boot/vmlinuz-2.6.BLAH-BLAH-BLAH root=/dev/BLAH ro quiet acpi=noirq

etc.



If you want to continue using Windows on the laptop and want to stop Windows from using ACPI, then see the following:


In windows, if the OS is not installed you can:

> 
If the OS isnt installed, and you're installing it, as soon as you enter into the 
setup, it will say at the bottom of the blue screen, "Press F6 to install Raid or 
Scsi" or something like that, when it says that press F5. It will continue to load 
all those devices but when done it will ask you the type of computer you want. It 
only shows a list of two, but there are more in the list, all you need to do is arrow 
your way up or down to find Standard PC then select it and go on like normal. That 
will disable ACPI from the beginning. ACPI will still have its own IRQ, but it wont 
be automatically assigning IRQ's to everything. it will sort of be just there and 
not do anything.


and if the OS is already installed and you can boot into desktop mode:


> 
One way is if you already have the OS installed, go to your device manager and Expand 
Computer. It should say Advanced Configuration And Power Interface (ACPI) PC. Right 
click that, and Properties. Under driver tab, click update driver, next, click display 
a list yada yada, next, Click show all hardware in this class, Under standard computer 
mfg's choose standard PC, next, then yes yes whatever. 


My source for the windows advice is this url: (worth reading the thread) 

[http://www.annoyances.org/exec/forum/winxp/t1014234292](http://www.annoyances.org/exec/forum/winxp/t1014234292)

Good luck!

---

### Post by Milo82 on 2007-03-22
Thanks for your reply. Yes, the laptop is a nightmare right now. 

I'm trying out some of the things you have suggested, but its going to take more than a few attempts. My first two have been unsuccessful. As for windows, Toshiba gave me a recovery cd that is basically useless for my needs, as I am not given the option of hitting F7 or F5, it just runs straight through until it freezes using Symantic Ghost. I tried using an old XP Home upgrade cd I had, but that recovery failed after it was unable to find some files it needed...I don't know why.

I'm going to keep trying out a few things with the leads you gave me. Thanks again.

---

### Post by thingy on 2007-03-22
Hi Milo

Well, this toshiba recovery CD sounds like it will use GHOST to image your hard disk on the laptop. This is a destructive process which will WIPE any data on it. Just be forewarned in case you weren't told this.

Ok...secondly if the laptop freezes during Symantec Ghost, you have more than just ACPI issues. Ghost is a DOS program and hence will not use any ACPI stuff. I would suspect the problem could be memory/system board/maybe hard drive.

To rule things out, download a copy of [Knoppix]("http://www.knoppix.org/")

Burn it and boot from the CD. When the boot prompt comes up, make sure you check out the help pages by pressing the various F? keys it mentions.

What you need to do is:

1. Boot knoppix without doing anything. See if the machine boots up at all or not. I suspect it will kernel panic as Ubuntu is doing so.

2. In which case, boot the Knoppix CD and pass the noacpi flag to the boot parameter and see if that has a positive effect or not.

3. You can also choose during the boot up of the CD to run the memory test utlity which will test you system memory. Again youll need to look at the help screens to figure out what the cmd line is to specify at the boot prompt. I don't remember it off hand and my knoppix cd is at work.


Let us know what you've tried in as much detail as possible.

---

### Post by Milo82 on 2007-03-22
Thanks for the new reply. I'll try your new suggestions. For a mem-test, how many times should I allow it to go through before I am satisfied that it was successful. I've run them before and if I remember it just kept on going. 

Below are detailed results to the different things I have tried since my last post. 

__________________________________________________

After the previous post I began playing with the grub commands, pressing &#8220;e&#8221; at the grub menu on the &#8220;Ubuntu, kernel 2.6.17.11-generic&#8221; option then &#8220;e&#8221; again to edit the &#8220;kernel /boot/vmlinuz-2.6.17-11-generic root=/dv/sda2 ro quiet splash&#8221; line. I always removed &#8220;splash&#8221; from the line because I found it gave me a chance to take notes on any errors that appeared. When I say that I enable or disable Legacy Emulation I mean in the BIOS setup screen, this was an attempt to get rid of the PnPBIOS errors. It doesn&#8217;t seem to have any affect. My computer did also freeze in the BIOS setup once, before grub did anything, so that makes me worry about how deep these problems are going.

FIRST ATTEMPT: I didn&#8217;t take great notes but I think I entered &#8220;noacpi&#8221;
ACPI: unable to enable ACPI
PNPBIOS fault&#8230;attempting recovery.
PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
PnPBIOS: You may need to reboot with the &#8220;pnpbios=&#8221;off&#8221; option to operate stably
PnPBIOS: Check with your vendor for an updated BIOS
PnPBIOS: Unable to get node info. Aborting.
PCI: Cannot allocate resources region 0 of device 0000:06:06.0
Usb-2: device not accepting address 2, error -71
Ata1: command 0xc8 timeout, stat 0x50 host_stat 0x20
hw_random: cannot enable RNG, aborting


SECOND ATTEMPT: After disabling Legacy Emulation for USB KB/Mouse and USB-FDD on the BIOS and adding noacpi to the kernel line in grub&#8230;
All errors were the same except the following&#8230;
PnPBIOS: dev_node info. Aborting
/sbin/init: relocation error: /sbin/init: symbol readdir, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
Kernel panic &#8211; not syncing: attempted to kill init!
(then it hung)

THIRD ATTEMPT: After enabling Legacy Emulation in the BIOS Setup and adding &#8220;acpi=noirq&#8221; and &#8220;pnpbios=off&#8221; to the kernel line in grub&#8230;
ACPI: Getting cpu index for acpiid  0x1
Hw_random: cannot enable RNG, aborting

After entering password and attempting to log in it appeared to be working&#8230;then I was sent back to the login screen.
At login screen the date kept switching&#8230;
I reentered my password and managed to get as far as my Google homepage&#8230;then a few seconds later I was back at my login screen.
Switched to &#8220;failsafe session&#8221;
I tried shutting down so that I could see the errors from login again, but it froze.

FOURTH ATTEMPT: Only added &#8220;pnpbios=off&#8221;
No new errors, but there were none about PnPBIOS
PCI: Cannot allocate resources region 0 of device 0000:06:06.0
ACPI Getting cpuindex for acpiid 0x1
usb 1-2: device not accepting address 2, error -71
hw_random: cannot enable RNG, aborting


I attempted a console login and it froze.
__________________________________________

Also, I was aware that Ghost would wipe my harddrive and backed everything I cared about up to my server before using it. My computer doesn't normally freeze while Ghost is doing what it does, more often it is after Ghost finishes and the computer reboots that the computer freezes. But, I'm not ruling out anything as the problems seem to go pretty deep.

Thanks again.

---

### Post by Milo82 on 2007-03-22
I'm currently successfully running the Knoppix cd. First try, without the acpi=off option it acted pretty much identical to Edgy, rebooting during boot. Then I passed the acpi=off option and was up until just about 3 seconds ago running a memory test, the laptop just shutdown completely while I was typing this. I'm at a loss for what to try next. Thanks for any help.

---

### Post by thingy on 2007-03-23
Hi Milo,

I've read through your results and this sounds like the laptop hardware(or the ACPI/FLASH BIOS) is faulty and not something that is a software issue and can be circumvented.

Ok, youve got a couple of things you could try
.

1. Can we know the full model of your laptop. It's a Toshiba Satellite M40-XXXXXX something
2. Goto the toshiba tech support site and download the current version of the ACPI Flash bios. Use this to flash the bios in the laptop to rule out corrupt bios code as the issue
3. Reset the CMOS information to factory defaults. This is usually an option in the BIOS or sometimes a button you can push on the system board. Or sometimes, you can simply take out the cmos battery and let the charge drain. Depends.

I dont expect the above to be fruitful but they do need to be ruled out.

Your last option is to take the laptop in for repair. I believe Toshiba will simply swap out the system board as these days they don't actually repair the existing boards.

If the cost of the repair is not economically viable, then get a brand new laptop or a 2nd hand one from e-bay (cheap!)

Sorry we couldn't help more.

good luck


Oh.. a couple of passed on the memory test utility are usually enough. So say, 3 passes of all the tests.

---

### Post by Milo82 on 2007-03-23
It's a Toshiba M40 PSM42U-0NJ00U. I won't bother trying to have Toshiba fix it, since I believe its no longer under warranty. I've already tried downloading the latest BIOS. I have no idea how to deal with the CMOS, but I can do a quick search online to figure it out. I'm also probably going to bring it in to a repair shop today. If all else fails the shop looked like it had some decent cheap computers, so I might just pick one of those up load up Linux and get back to developing my website. I really appreciate your efforts in trying to help me with this issue. Thanks.

---

### Post by Milo82 on 2007-03-25
I'm writing this on the doomed laptop. I booted using Knoppix. Booting into Edgy has been slightly better the today, but I'm not real sure why. I flashed the BIOS again, but other than that no new changes. The computer has ran for a decent amount of time on a few occations, but I still experience freezing and a refusal to make it past the splash screen on boot. 

The guy at the repair shop didn't seem know have any new ideas on how to fix it. Before I go forward and buy a new computer I want to make sure that there is really no way to get this laptop running reliably again. I was told that after flashing the BIOS there isn't any point in resetting the CMOS since flashing the BIOS has the same affect. Is that true? Is there anything else I might be able to try before purchasing a new or used computer?

---

### Post by thingy on 2007-03-25
Flashing the BIOS might clear the CMOS as well. I don't know for sure.

umm I can't think of anything else that can be tried. I did a search for spare parts for your laptop and came across this:

[http://www.sparepartswarehouse.com/Toshiba,Satellite,M40-80,PSM42U-0NJ00U,Laptop,Parts.aspx](http://www.sparepartswarehouse.com/Toshiba,Satellite,M40-80,PSM42U-0NJ00U,Laptop,Parts.aspx)

All the parts are pretty pricey but if you really want to keep using the unit, then these people also have a toshiba laptop repair service.

[http://www.sparepartswarehouse.com/laptop-repair.aspx](http://www.sparepartswarehouse.com/laptop-repair.aspx)

The laptop has a good screen + HDD and if you don't want to repair it, those two items can prob. be sold off on e-bay to recoup some money. The memory too if youve confirmed its not at fault.

---

### Post by Milo82 on 2007-03-25
Alright. I guess its time to give up. Thanks again for all your help.

---

