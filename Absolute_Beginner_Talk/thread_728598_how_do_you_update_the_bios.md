---
title: "how do you update the bios?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by ebony_vbac on 2008-03-19
i went to hps website and downloaded the update for my bios, but how do i actually get it into my computer. i dont have an operating system on it. just some basic version of dos that doesnt even seem like real dos. it boots from disk first but this disk i put it on isnt anythign you can bot from

---

### Post by hhhhhx on 2008-03-19
put the disk in your com, then shut the com down completely. and start it up. it may boot to the disk automatically, or may have to start it with a function key, (check your current bios)

---

### Post by ramjet_1953 on 2008-03-19
Why do you need to update your BIOS?

Are you having problems with the current BIOS?
If not there is no need to upgrade.

In fact, unless you have a dual BIOS setup and something goes wrong with the upgrade, you will be left with a totally dead motherboard, that would require either a dealer, or factory fix, at great expense.

What is the old saying? "If it isn't broken, don't try to fix it."

Regards,
Roger 8)

---

### Post by munkyeetr on 2008-03-19
My first question is why are you flashing your BIOS? If it is to gain some functionality that you need that the update supplies, then read the instructions below, but if you are doing it simply because it is available, I would think twice about it. If something goes wrong with the flash process, it can potentially brick your system.

Instructions:
**** I would recommend looking for specific instructions at the download site though, in case they have suggestions**

Generally when you download the BIOS update, you also get a utility to run that flashes it, so you would have 2 files: flash.com and bu45rf.bin 9 (these filenames are nonsense, the ones you get will be different). You would then either put them on a bootable disk, or after you have booted into a DOS like environment you would do the following:

1) Put in the disk that holds your BIOS update

2) Type:
```
cd a:
```

3) Type: ```
dir
```
or
```
ls
```
so you can see the file names

4) Invoke the flash program and pass the update as a parameter (ie: Type:
```
flash.com bu45rf.bin
```

and it should perform the update.

---

### Post by Cresho on 2008-03-19
> **munkyeetr said:**
> My first question is why are you flashing your BIOS? If it is to gain some functionality that you need that the update supplies, then read the instructions below, but if you are doing it simply because it is available, I would think twice about it. If something goes wrong with the flash process, it can potentially brick your system.

Instructions:
**** I would recommend looking for specific instructions at the download site though, in case they have suggestions**

Generally when you download the BIOS update, you also get a utility to run that flashes it, so you would have 2 files: flash.com and bu45rf.bin 9 (these filenames are nonsense, the ones you get will be different). You would then either put them on a bootable disk, or after you have booted into a DOS like environment you would do the following:

1) Put in the disk that holds your BIOS update

2) Type:
```
cd a:
```

3) Type: ```
dir
```
or
```
ls
```
so you can see the file names

4) Invoke the flash program and pass the update as a parameter (ie: Type:
```
flash.com bu45rf.bin
```

and it should perform the update.

ohh nice!  i use to use caldera dos to boot up and just dir and execute the program that flashes the bin into my bios.

---

### Post by ebony_vbac on 2008-03-19
i have a blank computer with no os and i've been trying to install ubuntu for like 2 weeks now on it, i was given the suggestion of updating the bios because there is a newer version of it  but it is not the one on my pc. sometimes it says you cannot boot from this cd insert cd2 or update the bios. so i'm trying to update the bios

---

### Post by ebony_vbac on 2008-03-19
munky when i type cd a or whatever drive it is, i think it's e it says invalid directory i cant do any dos commands that i used to do back in the day on pcs

---

### Post by maniac_X on 2008-03-19
what is the make and model# of your mobo?
does your computer have a floppy drive or not?
try to follow the recommendations of your mobo maker for flashing.

if no floppy drive, you can still get a DOS boot image that boots from CD. [[COLOR="Red"]Boot image ISOs[/COLOR]]("http://www.allbootdisks.com/download/iso.html")


if possible, delete some of the unneccessary files from the ISO, enough to make room 
for your flashing program and bios file.

yes, you should be very careful while flashing. while it isn't overly difficult, as others have noted here, it can kill the mobo if done incorrectly or failure occurs during the flash proccess.

if you have a floppy, it would be wise to backup your current bios. this is also done with the flashing program in most cases.

---

### Post by ebony_vbac on 2008-03-20
what is a mobo?

---

### Post by munkyeetr on 2008-03-20
> **ebony_vbac said:**
> what is a mobo?
motherboard or mainboard

---

