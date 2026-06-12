---
title: "2 noob questions - mount cdrom and see mac files"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by MiamiDave on 2007-05-06
iMac 2.16 GHz Intel Core 2 Duo - Feisty installed ok under Parallels Desktop.  When I try to access either the internal DVD drive or an external Pioneer burner, I get an error message: Unable to mount the selected volume...mount: special device /dev/scd0 does not exist.  I have "Default DVD-CD ROM Drive" connected in Parallels.  When I ran gxine, it told me I needed to create a "symbolic link".  

I'd also appreciate help on accessing data (music, photos, and video) on my internal HD and an external FireWire HD.  Both formatted Journaled HFS+.

Again, most humble apologies for these noob problems - I did attempt an archive search, but no joy.

TIA,
Dave

---

### Post by kidders on 2007-05-08
Hi there and welcome,

The first thing to check is whether "special device /dev/scd0 does not exist" is really true. On my box, for instance, my dmesg shows...
```
scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S183A SB02 PQ: 0 ANSI: 5
...
...
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 0:0:0:0: Attached scsi CD-ROM sr0
```

```
$ ls -l /dev/sr0
lrwxrwxrwx 1 root root 4 2007-05-08 12:07 /dev/sr0 -> scd0
```... which is where /dev/scd0 comes from.

```
$ ls -l /dev/scd0
brw-rw---- 1 root cdrom 11, 0 2007-05-08 12:06 /dev/scd0
```

Hopefully, you can do the same sort of thing on *your* box (ie confirm that, not only does /dev/scd0 exist, but that it refers to the right hardware) ... or at least discover what /dev nodes you *should* be using.


To read HFS+ off optical discs, you might want to check...
```
$ grep scd0 /etc/fstab
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```As you can see, mine explicitly prohibits the use of any filesystem other than UDF and ISO9660. Filesystem types are tried in the order specified, which could be irritating if you're using hybrid discs, and want to decide the order on a case-by-case basis, I suppose.

---

### Post by MiamiDave on 2007-05-09
Thanks for the advice, Kidders.  Just for giggles, I burned and booted from the live cd, and everything worked perfectly - some permissions problems with directories on the HD's, but I'm sure a bit of work with CHMOD will fix that.  So it would appear that the problems I'm encountering are due to Parallels Desktop, which I'll address in their forum.

Again, thanks for your reply.
MiamiDave

---

### Post by kidders on 2007-05-09
No problem. :-)

Depending on how familiar they are with your problem, posting the results of some poking around (much as I did) may be helpful. Problems like these can come from just about anywhere!

---

