---
title: "Post-install lilo help on triple-boot"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by mattsen on 2006-02-01
I suppose this *may* be more appropriate for the install help forum, but since I'm an *absolute* beginner when it comes to ubuntu, and am absolutely dirt-stupid when it comes to things like mounting, lilo, etc., thought I'd try here first, hoping that I could get some help that was sufficiently dumbed-down enough, even for me.  :-)

Here's the deal.  I've had a laptop with a dual-boot XP Pro/Mandriva install for the past 1-1/2 years.  I really have wanted to migrate to ubuntu (eventually scrapping Mandriva, but having to keep XP for work purposes), so finally got up the gumption to do the install to an empty partition on my single drive.  The plan was to do the install, *not* install either grub or lilo as part of the install process, and to then edit my existing lilo from within Mandriva to allow the now triple-boot XP/ubuntu/Mdv setup.

Now (again, being lilo-stupid), I find myself stuck.  Both my XP and Mdv installs are fine and operational, no problem.  But, I am at a loss as to exactly what is needed to finish off the triple-boot setup, adding ubuntu.

XP is on hda1, ubuntu is now (theoretically :-) hda3 with swap hda8, and Mdv remains on hda5 through hda7.  In my feeble attempt to add the ubuntu section, I get this as a result:
********[root@localhost chuck]# lilo
********Added windows
********Added mandriva *
********Fatal: open /boot/vmlinuz-2.6.12-9-386ubuntu: No such file or directory
********[root@localhost chuck]#

(is this because that partition isn't mounted?  stupid in that area, too)

My lilo (with the errant section) is below; any pointer as to what stupid thing I'm doing? *(Again, I know squat, so please keep laughter to a dull roar, if possible :0)....
==================
default="mandriva"
boot=/dev/hda
map=/boot/map
keytable=/boot/us.klt
menu-scheme=wb:bw:wb:bw
prompt
nowarn
timeout=100
message=/boot/message
other=/dev/hda1
********label="windows"
********table=/dev/hda
image=/boot/vmlinuz-2.6.12-13mdk-i686-up-4GB
********label="mandriva"
********root=/dev/hda5
********initrd=/boot/initrd.img
********append="nolapic resume=/dev/hda6 splash=verbose"
********vga=791
image=/boot/vmlinuz-2.6.12-9-386ubuntu
* * * * label="ubuntu"
* * * * root=/dev/hda3
* * * * initrd=/boot/initrd.img-2.6.12-9-386ubuntu
* * * * append="nolapic resume=/dev/hda8 splash=verbose"
        vga=791

TIA for any pointers, help, etc.

---

### Post by mattsen on 2006-02-01
Mea culpa; it would seem I'm *not* a beginner here, strictly speaking, dense as I can be at times, so I *did* move the thread to the install forum (if anyone cares to follow and respond there). Thanks. [http://ubuntuforums.org/showthread.php?t=124427](http://ubuntuforums.org/showthread.php?t=124427)

---

