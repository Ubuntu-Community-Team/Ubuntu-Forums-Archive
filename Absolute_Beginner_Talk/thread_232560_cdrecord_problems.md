---
title: "cdrecord problems"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by braddcadd on 2006-08-08
I can't figure out my CLI burning problems.  "Burn" and "cdrecord" aren't working for me.  See the cdrecord output below:

braddcadd@ubuntu:~$ sudo cdrecord -v speed=2 dev=0,4,0 ubuntu*.iso
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '0,4,0'
scsibus: 0 target: 4 lun: 0
cdrecord: No such file or directory. Cannot open '/dev/pg4'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by braddcadd on 2006-09-03
Can anyone help with this one?  I can't burn with anything CLI, k3b, gnomebaker, . . .

When trying to burn an iso gnomebaker freezes at the same place "calculating data disk image size" with 3 seconds left.

This is the output of gnomebaker when trying to burn a data cd:
```

INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
Using PPC_4_14_06000.PDF;1 for  /PPC_4_14_06.pdf (PPC_4_14_06.pdf)
mkisofs: Error: '/home/braddcadd/Desktop/Data/Stock Research/PPC_4_14_06.pdf' and '/home/braddcadd/Desktop/Data/Stock Research/PPC_4_14_06.pdf' have the same Rock Ridge name 'PPC_4_14_06.pdf'.
mkisofs: Unable to sort directory 

```

---

### Post by ispmarin on 2006-09-03
What is the device that the cdrecorder is attached? You is trying to use the pgc4, with the dev=0,4,0 line. Try chaging this dev with the id of you drive. If it IS you drive, then... 

Second: The filename is the same. Are you trying to copy two files with the same name to the same place?

Hope it helps.

---

### Post by braddcadd on 2006-09-03
> **ispmarin said:**
> What is the device that the cdrecorder is attached? You is trying to use the pgc4, with the dev=0,4,0 line. Try chaging this dev with the id of you drive. If it IS you drive, then... 

Second: The filename is the same. Are you trying to copy two files with the same name to the same place?

Hope it helps.

How do I find out the id of the dev?

---

### Post by braddcadd on 2006-09-03
Here is some more information to help diagnose.  These errors pop up when I use the command line to start gnomebaker (sudo and regular).

```

braddcadd@UbuntuTop:~$ sudo gnomebaker
Password:

(gnomebaker:14322): Gtk-WARNING **: gtkwidget.c:4221: widget not within a GtkWin dow

** (gnomebaker:14322): WARNING **: Stat of file [/root/socket-UbuntuTop] failed

** (gnomebaker:14322): WARNING **: Stat of file [/root/tmp-UbuntuTop] failed

** (gnomebaker:14322): WARNING **: Stat of file [/root/socket-UbuntuTop] failed

** (gnomebaker:14322): WARNING **: Stat of file [/root/tmp-UbuntuTop] failed

braddcadd@UbuntuTop:~$ gnomebaker

(gnomebaker:14341): Gtk-WARNING **: gtkwidget.c:4221: widget not within a GtkWindow


```

---

### Post by ispmarin on 2006-09-03
bug?

---

### Post by braddcadd on 2006-09-03
I have searched the net a while and the leading theory on this error is that it is a firmware problem.  But, I haven't found a place to get the firmware yet.  Furthermore, I may need Windoze to install it, once found.  

Can I just buy another CDROM/DVD for my IBM Thinkpad T30 and stick it in?  Or will the "bad" firmware still be a problem?

---

### Post by braddcadd on 2006-09-16
Still fighting this one.  Any help would be appreciated!

I have waited through gnomebaker's pause.  It asks me to insert a CD (although I already have).  I open the CD tray then close it again.  Once the (non) burning is finished I get an error.  My cdrom is unsupported?  Below is the output:
```

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'DVD-ROM SR-8177 '
Revision       : 'NB21'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0000
Profile: 0x0010
Profile: 0x0008  

```

I have heard some people talking about setting the cdrom up as a SCSI.  Is mine setup different from that?  
```

braddcadd@UbuntuTop:~$ ls /dev/hdc -l
brw-rw---- 1 root cdrom 22, 0 2006-09-16 22:02 /dev/hdc
braddcadd@UbuntuTop:~$ ls /dev/cdrom -l
lrwxrwxrwx 1 root root 3 2006-09-16 22:02 /dev/cdrom -> hdc

```

---

