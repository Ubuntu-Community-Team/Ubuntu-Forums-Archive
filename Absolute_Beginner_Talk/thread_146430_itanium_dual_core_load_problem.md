---
title: "itanium dual core load problem"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Andrew5 on 2006-03-18
I loaded ubuntu on a second hard drive.  I am hoping to dual boot.  It seemed to go well until the restart and I got a windows error saying I had to choose how to boot as there was a problem.  Did I want to boot into safe mode, etc.  No matter what I chose It would not continue the boot sequence until I finally disconnedted the hard disk with the Ubuntu loaded and then it booted to windows.

What do I do now to get it to dual boot?

---

### Post by Pragmatist on 2006-03-18
You'd think it would be easy to find instructions for dual-booting with multiple hard drives.  Well it isn't! :)  Actually, when I first started using Linux about 5 years ago, I wanted to dual-boot with 2 drives.  It turns out that this is very uncommon and most people either use seperate computers or, if they dual-boot, put both OSes on the same drive.  However, don't despair...:)  Read this:

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

Here are some basic facts you need to know:
1.) Windows MUST be the first hard drive and be installed on the first partition (I've read some things to the contrary, but unless it really is a bother, I'd put Windows on the first hard drive.)

2.) You must put a **boot partition** (this is named **/boot** for obvious reasons) on the **same drive as windows**.
They explain three options in the above link
a.) shrink windows and put the /boot partition before it
b.) make windows less than about 8.5 GB
c.) Enable LBA in your BIOS and put /boot anywhere on Windows drive.

I'd go with option c.

I think what is happening is that NTLOADER, Windows' boot loader, provides you with the choice and then passes control to GRUB if you choose to boot linux.  In a single-drive dual-boot it is usually the other way around: GRUB passes control to NTLOADER if you choose to boot Windows.  So if you follow these instructions, NTLOADER will pass control to GRUB which is located on the **same drive as windows**  GRUB can then boot the linux kernel which resides on the second drive.

So, read the info in the above link, and let us know if you have more questions.  Good Luck!

---

### Post by OfficeLinebacker on 2006-03-18
I would imagine this would also depend on teh BIOS
 
OR does just about every BIOS just give you "IDE HDD" as the boot method, regardless of how many HDs you have?

---

### Post by Pragmatist on 2006-03-18
> I would imagine this would also depend on teh BIOS
OR does just about every BIOS just give you "IDE HDD" as the boot method, regardless of how many HDs you have?

I'm not sure I understand you.  When the BIOS is ready to look for an OS, it reads its boot order and checks the devices one at a time, in order, until it finds an OS.

I suppose that it is possible to put the Windows drive on the first IDE port and Linux on the second IDE port, but have BIOS boot the Linux drive.  Then, have GRUB chainload to Windows' boot loader.  However, if there is no objection to booting to the Windows drive, then I would do that since all of the instructions I've read follow that method.

The only other issue specific to the BIOS is that LBA be enabled if it is desired to put the /boot partition AFTER ~8.5GB  However, most BIOS today have this feature so it is probably irrelevant.

---

### Post by OfficeLinebacker on 2006-03-18
I guess I am thinking in terms of bios--every time you boot you could change the boot order.
 
Not practical in real use I suppose?
 
I also gather it depends on how often you want to switch OSes.

---

### Post by Pragmatist on 2006-03-18
:) Yes, of course you can do that, but it is a hack, and probably not good for the BIOS

---

### Post by Andrew5 on 2006-03-18
Thanks for the start on this.  Let me ask before I dive in here.  I have a RAID arrangement where I have three drives with the first two as mirror drives and the third with Linux.  I am trying to do what you suggested and partition the first drive (which, because of the RAID arrangement, will actially partition both the first drive and the second as it's mirror, I assume).  When I look at the disk management screen I see the "C" drive as taking up all the space.  The directions for partitioning ask me to right click on "free space."  Well, 
167g is free, on a 200 g drive, yet right clicking everywhere seems to yeild no result.  Humm.

I also went to the Windows help screen and typed in "LBA" and "logical block addressing" and got no response.  So, I am having trouble enabling LBA because I can't find it to enable.

I'm sorry to be so obtuse, but my major in college, lo those many years ago, was philosophy.  Any computer we saw was a mainframe in the computer lab.

---

### Post by Pragmatist on 2006-03-18
Check your **BIOS** for the LBA.  You can get into your BIOS when you first start the computer look for a line that says somthing like "press DEL to access settings" typical keys are DEL, F2, CTRL  Once in BIOS look at the IDE settings and at your hard drives settings, you'll see if LBA is enabled or not.

Regard the RAID array: I'm not very knowledgeable about it, but I will do some reading up and come back.  In the meantime, I'm assuming the "disk management screen" your talking about is in Windows? btw, what version of Windows are you using (XP, 2000, 98??)

---

### Post by Andrew5 on 2006-03-18
Windows xp pro

---

### Post by Andrew5 on 2006-03-18
Went to BIOS, thanks for the help on that.  They are configured:

Drive Configuration:

Use Automatic Mode      <enable>
ATA/IDE Mode              <enhanced>
Configure SATA             <RAID>    (My other choice on this was "IDE")
S.M.A.R.T.                   <enable>

I do wonder if, because my other choice on "Configure SATA" was "IDE," if the RAID configuration is goofing me up.

Does "enhanced" mean I have IDE enabled or do I need to do it under SATA?  In which case I wonder if I will loose my RAID arrangement.  I guess I could just back up a lot more and forget about hard drive failure.

---

### Post by Andrew5 on 2006-03-18
I got the dual boot to work.  In the BIOS I changed "RAID" to "IDE."  I still do not know if this disrupts my RAID disk configuration but at least my computer boots.

Drive Configuration is now:

Use Automatic Mode <enable>
ATA/IDE Mode <enhanced>
Configure SATA <IDE> (My other choice on this was "RAID")
S.M.A.R.T. <enable>
 

Now I will try to figure out how to log onto my wireless network.

---

