---
title: "Missing NTLDR"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by penndragonn on 2007-02-24
I have tried Ubuntu, Kunbuntu, pclinusOS, and DreamLinux without being able to Dual boot my pc!!  I have followed all the instruction, that I'm aware of, and still can't get there. I have reinstalled windows on the first hard drive, and Linux on the second hard drive so many times, I've lost count!! What is going on? After reinstalling Linux and then Grub Loader...Pc rebooted...and BAMB!!!   Missing NTLDR...Is there any way to recover from this aside from reinstalling windows all over again...It's EXTREMELY frustrating...Thanks in advance


:confused: :confused: :confused: :confused: :confused:

---

### Post by STREETURCHINE on 2007-02-24
this is the reason i got rid of windows it used to lose it every outher week,

do a google search for ntldr
 .
there are plenty of sites to show you how to fix this.
i have just searched my notes here as i have fixed this numerous times .
but i cant find them right now and i cant remember it all of the top of my head

---

### Post by confused57 on 2007-02-24
> **penndragonn said:**
> I have tried Ubuntu, Kunbuntu, pclinusOS, and DreamLinux without being able to Dual boot my pc!!  I have followed all the instruction, that I'm aware of, and still can't get there. I have reinstalled windows on the first hard drive, and Linux on the second hard drive so many times, I've lost count!! What is going on? After reinstalling Linux and then Grub Loader...Pc rebooted...and BAMB!!!   Missing NTLDR...Is there any way to recover from this aside from reinstalling windows all over again...It's EXTREMELY frustrating...Thanks in advance


:confused: :confused: :confused: :confused: :confused:

You could try restoring your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If fixmbr doesn't work, you might have to also issue the command fixboot, from the Windows install CD recovery console(a Windows recovery cd is not able to restore mbr or ntldr)

The Super Grub Disk can boot Windows or Linux, as well as, restore Windows mbr or Linux grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you can get your Windows booting OK, you might want to try setting your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by STREETURCHINE on 2007-02-24
okay found my notes here is the manual fix.

```
# Manual File Re-Patching

This method attempts to copy and replace the corrupted file from the Windows Installation disc to your hard disk. To start, follow these steps:

   1. Insert the Windows 2000 or Windows XP CD into your computer as default boot up media.

   2. Enter Windows Recovery Console

   3. At the command prompt, assuming drive D refers to your CD Drive, type in the following and hit Enter:

      Press Y when prompted to overwrite any existing file.

          * copy D:\i386\ntldr C:\

          * copy D:\i386\ntdetect.com C:\


   4. Restart the computer

      If the error message still persist, it is likely that your boot.ini file is corrupted. Try to fix your corrupted boot.ini file instead.



```

if you run into trouble  post back.

at the first promt it is   R   hit enter
next promt     1    hit enter
then do step 3

---

### Post by penndragonn on 2007-02-24
:) :) That Super Grub looked quite confusing, remember gents, I'm like Ultra new at Linux...baby steps! LOL I will give the last post a try...thanks. I will get back to you guys...your all very helpfull here, I really appreciate it. Thanks again

Ron:)

---

### Post by penndragonn on 2007-02-24
Street,

That advice you gave me worked perfectly!!  Don't know how you guys come up with this stuff, but us new users are glad you do! Thanks to everyone for their input.. Now all I have to do is figure out how to load Linux my backup 100GB drive, and have Grub Loader work properly so I have dual Boot.


Ron:)

---

### Post by johnlh on 2007-02-24
Hi Ron,
I just went through Ubuntu 6.10 install my self.  I had XP Home on primary master and I installed Ubuntu on my primary slave.
I found on old link in the forum which had the Grub installing to fd0. Details at: [http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)
This failed for me as Windows wouldn't recognize the files on the floppys.  What it do is create a boot floppy w/ Ubuntu or XP options.  I booted into both w/ success - it works, but wants to boot from floppy over and over.  So, I wiped my slave clean and reinstalled Ubuntu and let it write Grub to hd0. It's working great.
The precaution I did take relating directly to the NTLDR, is the same as Street's, but I copied the NTLDR, NTDETECT.COM,  and BOOT.INI to a floppy.  It's just an XP boot should the MBR get corrupted.
John:)

---

### Post by penndragonn on 2007-02-26
Update.

I got it working thanks       to all you  fine gents!! here's the thing though. When Grub Loader                         comes up on screen....and I hit  Load Windows...windows starts, but     first screen reads: 

invalid      boot.ini file
loading  c:\Windows

Anyone know what that is about...? As I stated, all is working fine, so I'm not gonna tough anything!!:)

---

### Post by STREETURCHINE on 2007-02-26
You'll have to use the XP cd. Select the option to repair, but make it go into "Recovery Console mode." From there, you can bring up a help menu by typing help or a question mark (?). You're only interested in two commands in the list called "fixboot" and "fixmbr."

You want to run "fixboot" first, then exiting the Recovery Console and seeing if that fixes your issue. If not, retrace your steps back to the Recovery Console and run "fixmbr." You shouldn't have to run "fixmbr," but there is always a possibility.


Also, run chkdsk /r on the system before running fixboot.

---

### Post by penndragonn on 2007-02-26
Thanks again Street!!   Always know where to go is I have questions...this forum is great, expecially for us  new people

---

### Post by STREETURCHINE on 2007-02-26
glad i could help.:)

---

### Post by heartbeat on 2007-05-17
so you need to copy the ntldr and ntdetect to the C: where Program Files and Document and Settings are? (the windows drive)

---

