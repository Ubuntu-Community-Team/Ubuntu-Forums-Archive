---
title: "Can't burn CD/DVD"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by insipiens on 2006-09-06
Hi I have a Sony DDU 1615 DVD-Rom installed (prior to installing 6.06) but it's only reads CDs/DVDs, it doesn't allow me to burn media.

Under Disk manager it shows all the write options as unavailable.

Anyone anyidea what's missing?

Thanks

---

### Post by luv2craftca on 2006-09-06
Sorry, this may be a silly question, but are you sure it's a burner? not just a reader?  Above you said you had a Sony DDU 1615 DVD-Rom installed.  ROM is READ-ONLY memory, if it were a burner I believe it identifies it as DVD-RAM (Random Access Memory).  

I could be completely off track here, since I'm not at home and can't check my own system.  But if it is a burner, perhaps it is being incorrectly recognized?

---

### Post by insipiens on 2006-09-06
Looking at fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Ondoing a mount of the CD rom I get the following:

oem@ubuntu-client:~$ mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

oem@ubuntu-client:~$  dmesg | tail
[17179606.204000] Bluetooth: RFCOMM ver 1.7
[17179708.772000] Warning: /proc/ide/hd?/settings interface is obsolete, and wil l be removed soon!
[17179781.300000] cdrom: This disc doesn't have any tracks I recognize!
[17180348.824000] cdrom: open failed.
[17180348.888000] cdrom: open failed.
[17180441.192000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17180441.192000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17180441.192000] ide: failed opcode was: unknown
[17180441.192000] end_request: I/O error, dev hdc, sector 64
[17180441.204000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block= 16

---

### Post by angkor on 2006-09-06
> **luv2craftca said:**
> Sorry, this may be a silly question, but are you sure it's a burner? not just a reader?  Above you said you had a Sony DDU 1615 DVD-Rom installed.  ROM is READ-ONLY memory, if it were a burner I believe it identifies it as DVD-RAM (Random Access Memory).  

I could be completely off track here, since I'm not at home and can't check my own system.  But if it is a burner, perhaps it is being incorrectly recognized?

I think so too. It says [here]("http://reviews.cnet.com/Sony_DDU_1615_DVD_ROM_drive_IDE/4507-3209_7-31493634.html?tag=sub")
that it's just a DVD drive, not a burner. Are you sure you got the model straight?

---

### Post by insipiens on 2006-09-06
doh! Now I feel more stupid - you're right of course.

Got the machine from a mate, clearly I wasn't paying attention.

A relief anyway.

Thanks guys.

(note to self - check the obvious first)

---

