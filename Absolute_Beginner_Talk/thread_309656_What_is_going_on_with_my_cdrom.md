---
title: "What is going on with my cdrom"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by babooka on 2006-11-29
Does anybody know hat is going on with my PC? This results in a slow boot up (as you can see - 1 minute)



Running Edgy.

```

$ dmesg | grep hdc
[    2.655000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[    3.902000] hdc: _NEC DVD_RW ND-3500AG, ATAPI CD/DVD-ROM drive
[    4.757000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   76.181000] hdc: lost interrupt

```

---

### Post by kvonb on 2006-11-29
What configuration do you have your drives set as?  From that small snippet of info it looks like your boot hard disk is set to slave on the 2nd IDE port!

How many drives do you have on the system, and where are they located on the IDE chain, ie:

primary master:   ? (hda)
primary slave:      ? (hdb)
secondary master: DVD (hdc)
secondary slave:    ? (hdd)

Dmesg shows that your DVD is set as hdc, but there is something at hdd, if that is your boot drive it might be causing the lost interrupt problem.  Some DVD/CD drives have problems when placed on the same cable as hard drives and other CD/DVD drives, this is manufacturer specific.

Try moving the DVD to the other IDE cable.

Regards, KEv :)

---

### Post by babooka on 2006-11-30
Here what I've got:

hda - primary hard drive OS
hdb - storage hard drive

hdc - DVD/CD-RW
hdd - DVD ROM

Both hdc and hdd are set as "cable select".

I think I'll just get rid of dvd-rom. I rarely use it, but still ...

---

### Post by wpshooter on 2006-11-30
Unless it is required for some reason, I would not use cable-select.  Set CD-RW as master and other as slave, if you are going to keep it.  Personally, I don't know why you would need it.

---

### Post by kvonb on 2006-11-30
Disconnect the DVD-ROM and see if it makes a difference.  Just pull the IDE cable out, no need to disconnect the power.

This is of course just an educated guess on my part because of the interrupt error message you got, I could be wrong but at least you tried the easiest thing first.

---

