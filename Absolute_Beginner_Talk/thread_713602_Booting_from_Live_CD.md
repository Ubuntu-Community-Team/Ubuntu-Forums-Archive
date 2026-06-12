---
title: "Booting from Live CD"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by MolotovHearts on 2008-03-02
I have an older live cd for Ubuntu that I downloaded a few months ago and have tried it in a laptop I have found but can't get too far past the original boot screen where I choose to start Ubuntu.

This is what I get:

```

uncompressing Linux... OK, booting the kernal.
[17179569.184000] ACPI: Unable to locate RSDP
[  2423.941014] PnBIOS: Unknown tag '0x82', length '6'
[  2423.949233] PnBIOS: Unknown tag '0x82', length '4'

[  2801.061319] Buffer I/O error on device hdc, logical block 357536
[  3167.528730] Buffer I/O error on device hdc, logical block 128

[  3417.011345] Buffer I/O error on device hdc, logical block 16
```

---

### Post by spiderbatdad on 2008-03-02
Could you post some specs of this machine...like RAM. It may not be suitable for ubuntu, but may be fine for xubuntu or fluxbuntu. You may also need noapic nolapic entered as boot options by pressing F6 at the installation options screen, and deleting quite splash and adding noapic nolapic.

You need MINIMUM 512 RAM for a good Ubuntu 7.10 experience, otherwise I would recommend one of those lighter distros.

Also check your bios for config vga settings...not familiar with those errors, but you may be able to specify analog vga in your bios.

---

### Post by MolotovHearts on 2008-03-02
Dell Inspiron 3000

Phoenix BIOS 4.0 Release 6.0

Computer type: Pentium with MMX

Hard Disk: 3253 MB
Speed: 233 MHz

System Memory: 640 kb
Extended Memory: 64412 kb
Cached RAM: 512 kb

---

### Post by spiderbatdad on 2008-03-02
try noapic nolapic if that fails try irqpoll  you can also try noacpi


Is that a 3.2 GB hard drive?  Too small for Ubuntu installation...must have left off a zero at the end.

---

### Post by MolotovHearts on 2008-03-02
That worked until I get:

ide-cd: cmd 0x28 timed out
hdc: DMA interrupt recovery
hdc: lost interrupt


and then it just repeats over and over.



i'll try irqpoll now

---

### Post by spiderbatdad on 2008-03-02
Has this disk worked on another computer? I've had disks I thought were good, but gave me endless trouble, to the point of thinking the laptop's hardware just wasn't compatible...just went back to an older HP the other day with a newly burned disk, did noapic nolapic, and bang xubuntu up and running great.

---

### Post by MolotovHearts on 2008-03-02
irqpoll ends with:

attempt to access beyond end of device
loop0: rw=0, want=1284378, limit=1274960
SQUASHFS error: sb_bread failed reading block 0x9cc8c
SQUASHFS error: Unable to read cache block [273232ec:1a86]
SQUASHFS error: Unable to read directory block [273232ec:1a86]


and that just repeats too

---

### Post by MolotovHearts on 2008-03-02
> **spiderbatdad said:**
> Has this disk worked on another computer? I've had disks I thought were good, but gave me endless trouble, to the point of thinking the laptop's hardware just wasn't compatible...just went back to an older HP the other day with a newly burned disk, did noapic nolapic, and bang xubuntu up and running great.

I tried it on a computer a few months ago and it worked.

---

### Post by spiderbatdad on 2008-03-02
looks like trouble with the hard disk...is it 32GB or 3.2GB? You could try running memtest...or the livecd may be no good. I'm out of ideas for the moment. But hoping you get it.

---

### Post by MolotovHearts on 2008-03-03
Its just 3.2GB. I did a search on Inspiron 3000 and it seems that the hard disk is usually about that big.

Thanks for the help, I guess I'll have to try a different distro.

---

### Post by spiderbatdad on 2008-03-03
mmm unfortunately I think you need 8 GB, though only 4 is used. I believe on xubuntu you can get away with 1.5.

---

