---
title: "How to get rid of Grub on external hard drive (sdb)"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-05-17
Greetings:

I installed 7.04 tonight on an external hard drive (sdb) and I have Vista on my internal hard drive (sda).  I kept getting Grub error 17 or 21.  Grub is installed on sdb.  Now I want to just give up and put Ubuntu on its own dedicated box.  Basically, I want to get this system back to the way it was with JUST Vista on sda.  So how do I get rid of grub so my system just loads right into Vista like it used to?

To get back to Vista took me HOURS of just messing around once I got Grub to load through the boot menu.  I had to manually edit the part that looks like (hd0,0) and I just kept trying random things until it worked.  It loaded Vista so I'm scared to reboot and not be able to get back here.

Please help me get grub off my system so I can install Ubuntu on its own machine and keep this one safe and sound!

Any help would be GREATLY appreciated!

---

### Post by esoterica on 2007-05-17
If I'm understanding your question right what your wanting to do requires manually editing your Master Boot Record on the hard drive, your not going to be able to access it in Windows, that's impossible, it requires booting to special and dangerous to use utilities that can be used for editing such portions of your drive. There once was a day when you could boot into MS DOS and run the "FDSIK /MBR" command that might of at least made it seem like things were back to normal even though the actual data in the boot record would still really be in there. I'm not sure what luck you'll have though trying that with XP or Vista.

My suggestion for you would be to obtain your Windows installation Disk if you don't have it, then follow the directions as I posted them in this thread to zero fill the hard drive and get you a clean slate to reinstall Windows on...

[http://ubuntuforums.org/showthread.php?t=443400](http://ubuntuforums.org/showthread.php?t=443400)

This is the only way you will ever truly get everything cleaned up off that hard drive and back to a future of hopefully no problems to come back and haunt you if you don't clean up the Master Boot Record on that drive.

Dual and multi booting does work perfectly providing you at least partially know what your doing and follow instructions well. I've done it with no problems for years, I stopped doing it though after an attempt to dual boot with OpenBSD one time went horribly wrong. Now I either use Virtual Machines or physically swap out hard drives to run multiple OS's, each one just dedicated to that one specific OS. Life is so much easier for me now, and stable since I've adopted that policy.

Installing an Operating System is only fun for about the first couple times you do it, trust me, after that it gets very mundane and dreadful to even consider. People tend to forget that the install may be easy and mostly automated these days, but hunting down all your software you like to run again and getting it installed and everything configured just the way you like it again, these things can take months and weeks to finish, and after repeatedly doing it over and over again over the years you learn, once you have it installed, configured and working you don't go screwing with it by trying to get some other OS to multi boot with it.

---

### Post by esoterica on 2007-05-17
P.S.
I forgot to add, in your thinking it is probably wrong, you may have Linux installed on that other hard drive, but the actual boot loader is probably on the primary hard drive that Windows is installed on. You'll be able to tell by unplugging that external hard drive and rebooting, my guess is your still going to see the Linux boot loader turn up even with that Linux drive removed from the system.

I know the commands to try repairing the Master Boot Record in both Windows and lilo, but I am not familiar enough with the boot loader Ubuntu uses to tell you the commands to run the equivalent to fix MBR in it. Maybe someone here knows and it's worth a try before you end up just wiping everything clean anyhow and following my advice in that other thread I gave you the link to.

I know with XP at least in the system restore control panel thing they highly caution you against running FDISK /MBR to repair the master boot record (MBR) for Windows XP (haven't caused myself problems in Vista bad enough to try it there yet myself), but if the thing is hosed already anyhow, like it sounds like yours is, then no harm from trying.

You'll know easy enough by just unplugging that external drive and booting up with out it. There's a chance that if you set your BIOS first to boot to that drive that you installed the boot loader on it instead. In which case you can just set your BIOS back to boot to the other drive now instead and be fine. Follow my advice still to properly get that other drive cleaned up if that's what you want to do. Once you have that external drive zero filled you can then use Windows to format it by using your Windows Command Prompt to send it the FDSIK and FORMAT commands (this part is easy, do a google search for the specific step by step instructions on running these commands in Windows). Note though, FDISK or FORMAT is not going to clean that boot loader off the other drive if you managed to get it over there instead of on the primary drive (which I doubt you did based on what your asking), this is why I'm telling you you'll need to zero fill the disk like in my other instructions.

---

### Post by Ted Nancy on 2007-06-07
I had a similar problem. An OEM vista disc from HP, no restore partition to work with, and no desire to just restore factory default.

Here is what worked for me:

Download MbrFix.exe from [www.sysint.no](www.sysint.no) (click the downloads link, and read over the readme link beside the download link to the file.)

Then do from Vista:

>Start >Accessories and right-click "command prompt" and then choose "run as administrator"

Then type (without quotes):

"MbrFix /drive 0 fixmbr /vista"

And reboot. Grub should be gone and Vista should boot normally. If not, you'll have to review the documentation. It could be that drive should not = 0.

Once Vista boots normally, go to control panel and use the disk management utility to delete the non-windows partitions. Reboot again. Then use the same utility to expand the Vista partiiton to full size of hard disk.

Best,

---

