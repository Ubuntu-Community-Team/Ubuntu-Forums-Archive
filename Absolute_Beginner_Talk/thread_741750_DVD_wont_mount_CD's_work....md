---
title: "DVD wont mount? CD's work..."
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-04-01
Hi,

I got a CD-RW/DVD Rom CD's work ...and i just put in a DVD for the first time and it dosen't work?

what can i check/do to get it going?

thanks..

---

### Post by mikeyphi on 2008-04-01
> **hopelessone said:**
> Hi,

I got a CD-RW/DVD Rom CD's work ...and i just put in a DVD for the first time and it dosen't work?

what can i check/do to get it going?

thanks..

Try opening Add/Remove and install 'ubuntu restricted extras'

---

### Post by hopelessone on 2008-04-01
already is...

Weird? do you think the dvd rom is not working? CD's burn no probs...

---

### Post by kevinatkins on 2008-04-01
Hi,

Could be a hardware problem.. Please elaborate -

- Do you mean DVD video doesn't play?

- Do DVD data discs not mount?

- Does / did the drive work with a different OS (eg, other Linux, Windows, etc)?

---

### Post by hopelessone on 2008-04-02
I mean I put in a DVD movie and nothing happins...

CD's mount no probs..

---

### Post by taavikko on 2008-04-02
Does the dvd mount! It just doesnt play, right?

If that's the case you need to install decss library, for encrypted DVDs
```
sudo apt-get install build-essential fakeroot debhelper
```
after that
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by hopelessone on 2008-04-02
No, unfortunately the DVD do not mount...that's the problem...

CD's mount...

Hardware issue?

---

### Post by taavikko on 2008-04-02
Try 
```
sudo mount /dev/cdrom
```
If it fails, paste next here
```
dmesg |tail
```

---

### Post by hopelessone on 2008-04-02
mount: No medium found
firebox@firebox-desktop:~$ dmesg |tail
[   98.516585] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   98.517748] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.01  Wed Sep  5 19:12:23 PDT 2007
[   98.629118] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   98.629589] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   98.630215] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   99.333797] NET: Registered protocol family 17
[  103.589652] NET: Registered protocol family 10
[  103.590510] lo: Disabled Privacy Extensions
[  114.130943] eth0: no IPv6 routers present
[  859.439521] totem[5715]: segfault at c0040007 eip b70e61d8 esp bfb37f40 error 5
firebox@firebox-desktop:~$

---

