---
title: "something is buggy but I'm not sure what (can't even install....)"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by amerin on 2008-02-20
alright so I was given this oldish comp to experiment with Linux on and I was trying to install and I came across several stumbling blocks, the first is The hard drive/s are split up into 3 partitions and I can't figure out if this is one hard drive or two or three, and which combonations of partitions are from which drives if it is less thatn three....

two I's tried multiple burnings of 7.10 at different speeds and none will load past a busybox v1.1.3 screen
I even tried an old free copy of 6.06.1 that I ordered ages ago... but none will function.....

and my last problem is a BIOS problem....
is BIOS a windows thing or a general computer thing?
it says when attempting to load the kernel from the CD that the bios is too old 1998 when it should be newer than 2000.... how do I fix this.....
in the BIOS setup it says at the top "ROM PCI/ISA BIOS (2A69KB0E)
BIOS FEATURES SETUP
AWARD SOFTWARE, INC."

also info about the comp... I can't connect to the internet on it cause the original installation of Windows ME is screwed up....

so I know that some of my questions are not exactly ABOUT Ubuntu but they are about my configuring the newly installed comp the way I want.... can anyone help me please?

---

### Post by tyggna1 on 2008-02-20
your BIOS doesn't support modern boot procedures--specifically CD-ROM booting.  

BIOS is a computer thing--it's outside of the OS.  I'd try finding a BIOS update from the motherboard manufacturer--that would likely include the boot from CD-ROM support that you need.  Those usually come in the form of a down-loadable floppy or executable that you run right after the computer starts up.  Be sure to let that utility do it's thing--don't bother it at all.  If it doesn't complete the BIOS upgrade process, then the whole computer is trashed and there's nothing you can do.

If you can't get that to work, then you have a "boot from floppy" option open to you--guaranteed.  I know there exists a few guides for getting the install started via a floppy.  The problem isn't with the CDs that you have, your motherboard just doesn't know how to start the computer off a CD-rom.

---

### Post by northern lights on 2008-02-20
BIOS stands for "Basic Input/Output System" - it identifies and initiates your hardware, so that other software (including operating systems) can use it.

A BIOS update (check your mobo manufacturer's website) or booting from floppy might work. Another option is to install ubuntu fromthe net via [unetbootin]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411") - fairly easy, not a pain...

--> dl unetbootin from your win os - run the .exe file - reboot - choose "install ubuntu" from bootmeue - install it - done.

P.S. Just read your "non Ubuntu related question":
Windows in general ought to be trashed, but if you need to also have Windows installed (I do for games and Photoshop (don't even start tellin' me about the GIMP - it's not as powerful)), why ME? Why the shittiest (maybe apart from Vista - never used, never will) of 'em all? --> You can trust 98 SE (second edition) or XP SP2 to be stable, that's about it.

---

### Post by amerin on 2008-02-21
okay so I tried the walkthrough here [https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager) and it looks promising except that when I get to the smart boot manager menu the cd-rom dosn't show up even when I rescan it....

at least nothing that is recognizable at a cdrom drive...

theres a Floppy
Harddisk
Fat32 primary 1
Fat32 logical 5
Fat32 Logical 6
and the quit to bios, power off, and reboot options...



also, I didn't choose ME it's just how it came to me.... I actually don't need windows on this machine at all...

---

### Post by plucky on 2008-02-21
amerin,

Can you post the specifications of your hardware,i.e Make and model,Cpu speed,memory size,hard disk size, video card etc.

 > attempting to load the kernel from the CD that the bios is too old 1998 when it should be newer than 2000.. 

Your system is actually able to boot from the CD as it is trying to load the kernel, there might be a problem with the specifications of the computer or the CD isn't burned correctly.

1)Do you have another system to boot the Live CD on just to verify it?

2)Have you installed Ubuntu from this CD before?

---

