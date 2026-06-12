---
title: "upgrading from dapper drake to feisty fawn from disc no internet connection available"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by childofGod on 2007-05-27
I'm trying to upgrade from dapper drake to feisty fawn using a cd because dapper drake would not support my nic.  I don't know if feisty fawn will but I thought it might.  The problem I have now is that even though my bios is setup to boot from cdrom first it won't do it.  Instead it loads dapper drake anyway.  What am I missing?

---

### Post by n8bounds on 2007-05-27
Did you burn the disc yourself?  Are you sure its bootable/burned correctly?  Anyway, there is no direct upgrade path from 6.06 to 7.04.   You have to upgrade 6.06 to 6.10 (edgy) first.  Furthermore, I think you need the alt. install cd or the dvd (not the live cd) to do upgrades.  Lastly, I don't think you even Need to boot from it in the first place. 

Read this:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by n8bounds on 2007-05-27
Yeah, this is it:

Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download and burn the alternate installation CD
   2.

      Insert it into your CD-ROM drive
   3.

      A dialog will be displayed offering you the opportunity to upgrade using that CD
   4.

      Follow the on-screen instructions

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade" 

Note that for Kubuntu the upgrade dialogue will not be displayed and you will need to install gksu before running the above command (it will not work with kdesu).

---

### Post by childofGod on 2007-05-27
As you may have guessed linux is very new to me.  I thought that by burning the cd and booting from it I would have the option of doing a fresh install.  I'm not worried about losing data as I have not really even used dapper since it didn't support my nic.  I have not stored any files yet.  To burn the disc I downloaded the iso to a windows desktop.  Then I mounted the iso in virtual drive and burned from that using nero.  Am I on the right track or out in the weeds?

---

### Post by n8bounds on 2007-06-02
:) You are over complicating it a little.  Nero can burn ISO files directly.  If you do it your way it is not bootable.

---

