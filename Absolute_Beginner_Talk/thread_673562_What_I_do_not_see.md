---
title: "What I do not see"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by rtrdom on 2008-01-20
I have ntfs-3g so I can open the external usb disk. I can see pictures and files. I think I see them because of Ubuntu's capabilities rather than ntfs-3g because before I installed ntfs3g I could see exactly what I see now.However
I cannot operate/use windows XP.  Should I be able to get something like the Windows
desktop?  If not, how do I use Ubuntu to see information in programs installed in the
usb disk?  (FYI the usb disk is the original disk from a laptop, connected via usb cable
to this Ubuntu computer)  ntfs-3g config is set to allow write to both internal and
external disks. Sure would appreciate some help.
Thanks in advance for any help given.

---

### Post by cecure on 2008-01-20
> I cannot operate/use windows XP

do you mean that you dual boot with XP and it isnt booting anymore, or are you asking how to run windows programs in ubuntu?

if you are trying to use windows programs in ubuntu try [wine]("www.winehq.org").

---

### Post by rtrdom on 2008-01-20
I do not wish to dual boot.  I think I know how that is done because I have it on another
computer.  Perhaps this will explain:  I have a harddrive from a laptop that is connected
to this Ubuntu computer by way of a USB cable. I wish to use some of the programs and
access files (to modify them)  that are on that harddrive. I also have wine installed but
havenot been able to make either of wine or ntfs-3g let me modify the files.
Thank you for responding.

---

### Post by cecure on 2008-01-20
Alright, the best way to deal with windows programs is to find the installer and install them onto Ubuntu using wine.  Check this to make sure you configured ntfs-3g correctly [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")
it is a little old but most of the information is probably still ok


Good Luck

---

### Post by rtrdom on 2008-01-20
Thanks for trying.  I did all that about 4 hours ago. Will keep trying though. Thanks
again.

---

### Post by Curtisc on 2008-01-20
What are the programs you are trying to run?  Wine is unfortunately not able to run all of them.  Check out the list at [http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php) and see if you can find your software.

NTFS-3G simply allows read/write access to NTFS formatted hard drives.  It does not allow Ubuntu to run Windows programs (that's Wine's job).  However, many file types for Windows programs can be edited by Linux programs (i.e. if you've got a Word document, you can edit it with OpenOffice).  Take a look at the file types that you are trying to modify and see if there is a Linux program that will edit them.

---

### Post by rtrdom on 2008-02-20
curtisc thanks for the response.  What I want to do is install a template from scanned
in forms then fill out the forms and save them in another program. So far I have not
found a Linux/UNIX based program that will let me do that.  The program "Paperport"
combined with PDF create" lets me do it but then I have to keep updating them. I have
successfully built a form for indexing a table by using OOo-base.  I think I will try
building a form for the others in base and maybe it will work.
Thank you for taking the time to be interested.

---

