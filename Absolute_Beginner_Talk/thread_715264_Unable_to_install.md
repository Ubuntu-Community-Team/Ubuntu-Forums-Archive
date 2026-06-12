---
title: "Unable to install"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Bruv on 2008-03-04
I am totally new to open source OS, and have a collection of plastic beer mats waiting to be installed.

I have tried with a live cd in the current PC but want to install on an older machine.
I have  ubuntu-7.10-alternate-i386.iso burnt to CD that runs live with no problem, on this machine.

I am trying to install, or at least revue it on a PC with the following stats.
With a very basic Win98se installed after a reformatt

Intel Pentium IIIE 600 Mhz
System Memory 384 MB
Intel(R) 810 Chipset graphic
Fat 32 18152 free memory

None of the above mean much to me to be honest.
When I boot with the right boot sequence selected, I get a tumble of script across the screen that stalls and just stays static.

I believed the install should show graphically like on this PC, Im sure somebody has the answer.

Simple instructions please for a new boy....old boy to be honest.

---

### Post by wednesday allfather on 2008-03-04
> **Bruv said:**
> I am totally new to open source OS, and have a collection of plastic beer mats waiting to be installed.

I have tried with a live cd in the current PC but want to install on an older machine.
I have  ubuntu-7.10-alternate-i386.iso burnt to CD that runs live with no problem, on this machine.

I am trying to install, or at least revue it on a PC with the following stats.
With a very basic Win98se installed after a reformatt

Intel Pentium IIIE 600 Mhz
System Memory 384 MB
Intel(R) 810 Chipset graphic
Fat 32 18152 free memory

None of the above mean much to me to be honest.
When I boot with the right boot sequence selected, I get a tumble of script across the screen that stalls and just stays static.

I believed the install should show graphically like on this PC, Im sure somebody has the answer.

Simple instructions please for a new boy....old boy to be honest.

Are you trying to dual boot Win98 and Ubuntu?

What partitions have you made?

Are you using Live CD or alternate text only install disc?

---

### Post by Bruv on 2008-03-04
I was just trying before installing.

I have used the live and the alternate text versions, both do the same.

---

### Post by wednesday allfather on 2008-03-04
> When I boot with the right boot sequence selected, I get a tumble of script across the screen that stalls and just stays static.
What is the "right boot sequence" that you select?  Do you mean booting from a disk?

What do you mean by "script" and could you post it?

---

### Post by Bruv on 2008-03-04
In the BIOS I choose to boot from CD.
The script is a sequence of what is happening as the disk loads.
Script is my choice of words for scrolling words.
I cannot show what it is, because it is the pre loading sequence, and the disk never loads properly.

---

### Post by Moop on 2008-03-04
I think that you're right on the low end of hardware requirements to run Gutsy on that pc. You might try Xubuntu and see if that will work.

---

### Post by NiceGuy on 2008-03-04
Sorry if you've already said this but have you tried the 'normal' cd on your old machine? If so what happened?

You probably know this but just to make sure we are on the same page, the alternative install cd will not boot to a live session like the normal cd but will show you a text based install instead. But anyway, it shouldn't just hang. Can you tell us what is the last line which is displayed.

Oh and as a sort of an aside, you might find normal ubuntu (with gnome as the desktop environment) to run a bit slowly on that machine. If so then you might want to try Xubunu which runs a lighter desktop environment called XFCE.

---

### Post by Bruv on 2008-03-04
I thought I was well in to the scope of Ubuntu, but what do I know, seriously.
I shall take the advice and go for Xubuntu, fingers crossed.
Many thanks

---

### Post by Bruv on 2008-03-06
I have downloaded checked with WinMd5Sum and burnt slowly  Xubuntu.

The same as Ubuntu, it ends with the prompt [DR-DOS] A:/

Thats where I get lost, I have searched for an answer.

---

### Post by rjmoerland on 2008-03-06
Seems to me that something is still not quite right with the boot sequence, that is, I believe the PC doesn't boot from the (X)ubuntu CDs. Dr-DOS and an 'A:\' prompt are signs of another,  DOS like, operating system. Can you see the CD drive being used when the PC boots?

---

### Post by wednesday allfather on 2008-03-06
> **Bruv said:**
> I have downloaded checked with WinMd5Sum and burnt slowly  Xubuntu.

The same as Ubuntu, it ends with the prompt [DR-DOS] A:/

Thats where I get lost, I have searched for an answer.

Try disconnecting the ribbon from your HDD and reconnecting it.  I heard thru the grapevine, that might be an answer to DR-DOS A:/

If you are using a text installer (which I highly recommend, given your specs) you will need a separate partition to install Ubuntu.

---

### Post by Bruv on 2008-03-06
The boot sequence halts when "Seeking" to boot from CD, then continues with a totally different sequence to Windows loading.
It is undoubtedly booting from the Xubuntu disk.

---

### Post by Bruv on 2008-03-06
The penultimate line is
Caldera DR-DOS 7.03 and copyright dates etc.etc. before the final line....[DR-DOS] A:/

I uplugged and re-attached the leads from the drive and the Motherboard, no difference.

---

### Post by rjmoerland on 2008-03-06
I'm curious: what happens if you remove the cable to the hard disk and then boot the PC? (Of course, you won't be able to install linux).

---

### Post by halitech on 2008-03-06
typically when you see something pointing to A:\ it is DOS (or some variation) looking at the floppy drive. Dumb question time, is there a floppy drive connected with a floppy in it by chance?

---

### Post by Bruv on 2008-03-06
> **rjmoerland said:**
> I'm curious: what happens if you remove the cable to the hard disk and then boot the PC? (Of course, you won't be able to install linux).


Are you pulling my chain ?
2 Links On this[ forum]("http://ubuntuforums.org/showthread.php?t=636609")
And Caldera DR-DOS[ Googled]("http://www.google.co.uk/search?q=Caldera+DR-DOS+7.03&hl=en&start=0&sa=N")

---

### Post by wednesday allfather on 2008-03-06
I looked into Dr. DOS for you.  It is actually an operating system.  Looks like an old-school command line interface and the manual references Windows 95 like it just came out.  

Is there anything on the hard drive you care about?

If there is not, try reformatting the drive in another computer if you have the ability.  Kill the good doctor and try again.  If you have an extra hard drive sitting around, try that.  If you have an external case, you could take it to another comp.  Maybe the Doctor has your CD Drive and won't give up control.  Anyway, my next step would be to rid the disk of DrDOS and anything else I didn't need.

Pain in the neck, I know, but we will stick with you until we get this thread marked "SOLVED" :confused:

---

### Post by Bruv on 2008-03-06
I have a floppy drive, but it is empty....I checked again.

---

### Post by rjmoerland on 2008-03-06
> **Bruv said:**
> Are you pulling my chain ?
2 Links On this[ forum]("http://ubuntuforums.org/showthread.php?t=636609")
And Caldera DR-DOS[ Googled]("http://www.google.co.uk/search?q=Caldera+DR-DOS+7.03&hl=en&start=0&sa=N")

Nope... just trying to help. But perhaps this was my exit cue.

---

### Post by Bruv on 2008-03-06
I have a floppy disk with DBan ready to go.

I was only mucking about with Open source on an old PC, now I am intriqued.
Wonder how this Dr DOS came into the equation ?

I shall be away for a while if I DBan, confirm please if that is what I should go for now......

---

### Post by Bruv on 2008-03-06
> **rjmoerland said:**
> Nope... just trying to help. But perhaps this was my exit cue.

Sorry if I sound abrupt, I know nothing about PCs, well virtually nothing.
Your suggestion sounds like plugging a plug into a socket with no apperatus attached.....or am I wrong ?

---

### Post by rjmoerland on 2008-03-06
Well, my knowledge of linux is limited as well, but when someone tells me that they try to boot from a Ubuntu live CD on an old PC and they get Caldera's DOS instead, that's a bit too odd. DR-DOS is old as well, and I can't image why Ubuntu would have anything to do with it. (But again, my knowledge is limited). 

So, to rule out the slightest possibility that in reality it is the hard disk that boots the PC, I asked you what happens if you simply disconnect the hard disk. That way, you're sure it can't boot from it :) Not exactly plugging a plug in a socket, but more like removing the plug from the socket.

---

### Post by Bruv on 2008-03-06
My humblest apologies.

Pri Master HDD Error
Run Setup
Press F1 to Resume

Followed by the same sequence, ending with the same prompt.

I seriously thought the HDD was the heart and soul of a PC, and nothing would happen at all.
You learn a lot on the internet.....dont you.

Where does that leave this problem?
Its beaten me.....obviously

---

### Post by rjmoerland on 2008-03-07
Hmm, not the result I expected :)
I'm not pulling your chain: what happens if you *also* remove the Ubuntu CD? (What's left should be the device DR-DOS boots from - whatever that may be.)

---

### Post by wednesday allfather on 2008-03-07
> **rjmoerland said:**
> Hmm, not the result I expected :)
I'm not pulling your chain: what happens if you *also* remove the Ubuntu CD? (What's left should be the device DR-DOS boots from - whatever that may be.)

That a good idea RJ.  You can embed DRDOS on a romdisk.  It was used for cash registers, way back when, on diskless machines.  It could be stored in RAM, or wherever, really.  It isn't limited to the disk.  

I will look into this further.

---

### Post by Bruv on 2008-03-07
With no Xubuntu disk in drive I am seeing this last screen.

It has various information ie from the left in two rows.

Math processor: Built-in          Base Memory Size : 648 KB
Floppy Drive A: 1.44 MB 3half "
Floppy Drive B : None
Display Type : VGA/EGA
AMBIOS Date : 03/02/00
External Cache: 256KB Enabled
SDRAMS at DIMM(s) :1,2,

(Second list to right)

Base Memory Size:648KB
Ext. Memory Size :391160KB
Serial Port(s) :3F8,2F8
Processor Clock: 600E MHz
Power Management : APM, SMI

(Then a section)
Hard Disk(s)  Cyl   Head Sector Size LBA 32Bit Block PIO UDMA
                                                 Mode     Mode      Mode       Mode
Secondary Master : CDROM                                    4          N/A

(Beneath that)
PCI Devices
Onboard VGA, IRQ9                                   Onboard Communication Device IRQ11
Onboard Multimedia Device, IRQ11           Onboard USB Controller, IRQ10
Onboard IDE, IRQ14,15                             Slot   1     Ethernet IRQ9

(Then)

Searching for Boot Record from CDROM.....Not Found
Searching for Boot Record from Floppy.....Not Found
Searching for Boot Record from SCSI.....Not Found

Drive not ready
Insert BOOT Diskette in A:
Press any Key when Ready.


Should I reconnect HDD and DBan it ?

---

### Post by wednesday allfather on 2008-03-07
Boot and Nuke away.  Prolly a good idea anyway.  I'll keep a couple fingers crossed...

---

### Post by rjmoerland on 2008-03-07
> **wednesday allfather said:**
> Boot and Nuke away.  Prolly a good idea anyway.  I'll keep a couple fingers crossed...

Totally agree. Hope that will take care of your boot problems.

---

