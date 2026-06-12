---
title: "Install Canon MF4150 Printer"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by gspaulding on 2008-03-12
I would love to be able to print from my Canon MF4150.  I don't really care about the scanning, etc., just to want to print from Gutsy.  I downloaded the Canon UFR II Printer Driver for Linux v1.60 from the Asia Canon site following a link from openprinting.org.  I extracted all the folders/files and printed the instructions, but I am confused.

Requirements include CUPS 1.1.19 and Ghostscript, including the common API(GlueCode) that is appropriate for the system.  How do I find out if I have those requirements?

Instructions are included for rpm and deb packages.  I assume I use the deb instructions.  If anyone has successfully installed this printer driver, I would appreciate your help.  Where do I go from here?

---

### Post by mikeyphi on 2008-03-12
Open Synaptic - do a search for the packages, a green box confirms that you've got it!!

---

### Post by gspaulding on 2008-03-12
Thanks mikeyphi,

Opening Synaptic shows I have the latest versions of CUPS and GhostScript.  I first looked in the add/remove programs and didn't see them.  I will try to proceed with the instructions.  The instructions say to install the following file in 32-bit Debian systems:
"cndrvcups-common_x.xx-x_i386.deb" : common module for CUPS drivers

The first command is # dpkg -i [file name of common module for CUPS drivers].

I have a folder named cndrvcups-common-1.60 with several folders and files.  Folders include debian, libs, data, and others.  How do I know which file to use in the above code?

---

### Post by gspaulding on 2008-03-12
Please anyone?

Besides the folders, there are files including cndrvcups-common.spec and makefile.  The other files are just text files.  Any idea filename I specify for the dpkg -i code?

---

### Post by MayOne.Net on 2008-04-30
I just installed my MF4150 this morning following the advice from this thread, [http://forums.linux-foundation.org/read.php?25,2583,2825,quote=1](http://forums.linux-foundation.org/read.php?25,2583,2825,quote=1)

I downloaded the files from the Austrailia site, not the Asian one, but I am assuming it is the same file:
Linux Printer Driver (UFR II) Ver.1.60E
UFR_II_PrinterDriver_for_Linux_Driver_v160.tar.gz.

Buried inside the tarball are the debs: /UFR_II_PrinterDriver_for_Linux_Driver_v160/32-bit_driver/debian/

There are actually two .debs (four if you count the 64 bit versions in another folder.) I also looked at the install instructions and got lost, so I just installed the .debs. At first, I only installed one of them and couldn't figure out why the printer wasn't working. But, after installing both packages, the printer works great.

I simply went to the new printer set up in gnome (on Feisty), and selected the Canon MF4100 printer and configured from there.

---

### Post by davidlinux on 2008-05-10
MayOne.Net,
 I would love to check out the thread that you referred to as " http://forums.linux-foundation.org/r...3,2825,quote=1" but all I get is a 404 error (Page not found).  I notice that in some other forums, a mouse over on a link will show the entire URL even if it is abreviated in the text.  It does not expand the abriviated URL here.

It appears that the link is a partial URL.  Could you please post the complete link again?

I have been trying to install the driver for a week now and all I get are errors doing the quick install from the readmes in the tarball.  I also do not find the .deb files anywhere.  

Ubuntu Desktop 8.04 is the third distribution I have tried installing the UFR_II_PrinterDriver_for_Linux_Driver_v160.tar.gz tarball from the Australian site on.  Any help would be much appreciated.

dave

---

### Post by MayOne.Net on 2008-05-12
Hi Dave,

I'm not sure what happened to the original post, but I will fix the link. In any even here it is again: [http://forums.linux-foundation.org/read.php?25,2583,2825,quote=1](http://forums.linux-foundation.org/read.php?25,2583,2825,quote=1)

Shad

---

### Post by davidlinux on 2008-05-12
> **MayOne.Net said:**
> Hi Dave,

I'm not sure what happened to the original post, but I will fix the link. In any even here it is again: [http://forums.linux-foundation.org/read.php?25,2583,2825,quote=1](http://forums.linux-foundation.org/read.php?25,2583,2825,quote=1)

Shad

Thanks Shad,

I had previously downloaded the source tarball and tried to compile the driver from it - that did not work.  I think I had the same trouble that **gspaulding** had.

I finally downloaded the correct tarball that had the .deb files you referred to in it.  All I had to do was double click the correct .deb files for my 32bit intel system and it installed painlessly.  

I now have my Canon MF4270 printing from Ubuntu Desktop 8.04 on the network port.  I have the USB port connected to my Windows Vista machine.

I noticed one problem though: It will only print duplex with binding on the short side of the paper only (even when I have the setting for binding on the long side). 

Did you notice that on your MF4150 when using it fron Linux?  Any one else notice this too?  It works correctly from Windows. 

Also, there are three .ppd files for the MF4150 driver.  Which one(s) did you use to register the printer in the print spooler? (From step 2.5 in the "Canon UFR II/UFR II LT Printer Driver for Linux Online Manual").

Thanks again,
Dave

---

### Post by MayOne.Net on 2008-05-12
Hi Dave,

Now that I'm playing with the printer, my duplexing is stuck on on the short side as well. I'll see if I can't figure out how to fix that, but so far no luck playing with either gnome or the cannon print manager. Let me know if you find something that works.

I am using CNCUPSMF4100ZK.ppd, but honestly, I let gnome select it for me by going through the printer pannel. 

Shad

---

