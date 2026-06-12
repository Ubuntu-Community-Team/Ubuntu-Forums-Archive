---
title: "Blank DVD not recognized"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by erdomi on 2008-02-10
When I put in a blank DVD, it spins around and around.  Nothing ever pops up on my screen indicating that a blank DVD has been inserted and if I look for it in my file system, it's just not there.  I don't know where to start.  Any ideas?

Thanks for your help!

---

### Post by nikoPSK on 2008-02-12
> **erdomi said:**
> When I put in a blank DVD, it spins around and around.  Nothing ever pops up on my screen indicating that a blank DVD has been inserted and if I look for it in my file system, it's just not there.  I don't know where to start.  Any ideas?

Thanks for your help!

maybe the drive can't read it? (don't think I'm dumb, just suggesting, like my old laptop can read cd's, but not dvd's or cd-rws.)

---

### Post by oedha on 2008-02-12
mine was also like this...but when i wrote something on it....it can !!
it also happened to blank-cd too.....on mine

---

### Post by nikoPSK on 2008-02-12
> **oedha said:**
> mine was also like this...but when i wrote something on it....it can !!
it also happened to blank-cd too.....on mine

ah, so just try writing to it then. :)

---

### Post by erdomi on 2008-02-13
It's a 48X CD-RW/DVD combo drive...  Hmmm, I bought it with the intention that it would write DVDs, but maybe it only reads DVDs.  That would make me feel foolish.  When I try to write something, it just tells me to put in a disk.

Thanks!

erdomi

---

### Post by kpkeerthi on 2008-02-13
Remove it from the drive. Put it back again. When you hear it spinning for a few seconds, run
```

dmesg | tail -20

```
in a terminal. Might provide some clue.

---

### Post by erdomi on 2008-02-13
This is what I get:

> 
[17886759.800000]   Vendor: NIKON     Model: NIKON DSC E3200   Rev: 1.00
[17886759.800000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17886759.812000] SCSI device sdb: 1999872 512-byte hdwr sectors (1024 MB)
[17886759.820000] sdb: Write Protect is off
[17886759.820000] sdb: Mode Sense: 18 00 00 08
[17886759.820000] sdb: assuming drive cache: write through
[17886759.840000] SCSI device sdb: 1999872 512-byte hdwr sectors (1024 MB)
[17886759.844000] sdb: Write Protect is off
[17886759.844000] sdb: Mode Sense: 18 00 00 08
[17886759.844000] sdb: assuming drive cache: write through
[17886759.844000]  sdb: sdb1
[17886759.860000] sd 6:0:0:0: Attached scsi removable disk sdb
[17886759.860000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[17886759.868000] usb-storage: device scan complete
[17886761.012000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17886958.380000] usb 1-8: USB disconnect, address 14
[17886959.688000]  6:0:0:0: rejecting I/O to dead device
[17980906.780000] b44: eth0: Link is down.
[17980918.780000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17980918.780000] b44: eth0: Flow control is off for TX and off for RX.


---

### Post by kpkeerthi on 2008-02-13
Hmm... nothing unusual I could find from that log. Sorry I couldn't be of much help.

---

### Post by erdomi on 2008-02-13
Thanks anyways!

---

### Post by mc4man on 2008-02-13
```
48X CD-RW/DVD combo drive
```
On the face of it that looks like a cdburner/ dvd reader
If your still unsure go to places>computer, right click on drive and in properties under drive tag will be vendor and model

---

### Post by erdomi on 2008-02-13
Hmmm, I couldn't find the vendor and model in properties.  I am still running dapper.  Could that be why?

Thanks,
erdomi

---

### Post by macogw on 2008-02-13
> **erdomi said:**
> It's a 48X CD-RW/DVD combo drive...  Hmmm, I bought it with the intention that it would write DVDs, but maybe it only reads DVDs.  That would make me feel foolish.  When I try to write something, it just tells me to put in a disk.

Thanks!

erdomi

CD-RW/DVD isn't the same as CD-RW/DVD-R or CD-RW/DVD+R or CD-RW/DVD+/-R (and those with RW instead of R...).  CD-RW/DVD means it can read and write CDs, but it can only read DVDs.

Run ```
sudo lshw
``` It should show info about all your hardware.  The laptop I'm on says ```
           *-cdrom
                description: DVD writer
                product: DVD+-RW ND-6650A

```

---

### Post by Sinkingships7 on 2008-02-13
combo drive means that it can read/burn cd's and only read dvd's. it's not a dvd burner. a dvd burner would be labeled as a superdrive or a multidrive.

---

### Post by erdomi on 2008-02-13
Here's what I get:

        *-cdrom
             description: DVD reader
             product: CDRWDVD CRX310S
             vendor: SONY
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: VDK2
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5
           *-disc
                physical id: 0
                logical name: /dev/cdrom

I guess it doesn't write DVDs after all.  I'll be more careful the next time i buy a computer.  Thanks for you help!

erdomi

---

