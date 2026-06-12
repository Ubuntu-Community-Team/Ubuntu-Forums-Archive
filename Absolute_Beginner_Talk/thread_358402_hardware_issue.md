---
title: "hardware issue"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Unlockitall on 2007-02-10
i have a minor problem... i have a 1 gig flash drive that works beutifully, and i have an old pc, with usb ports. the issue is that when the flash driv is plugged in, it doesnt even know theres anything there. this wouldnt be an issue, but i wont be downloading applications from the computer, i will be downloading them from school, onto a flash drive, bringing them home, and then attempting to run them. is there any inexpensive way to make the computer get the files other then burning them to a cd, any help would be appreciated!:)

---

### Post by sardion on 2007-02-10
Probably your flash drive is USB 2.0 but the old machine is USB 1.1.

You may be able to get a USB card for your computer that is USB 2.0 (~$20 I think).

---

### Post by Unlockitall on 2007-02-10
thanks, im going to check bestbuys website, do you know if the installation is difficult?

---

### Post by teaker1s on 2007-02-10
depending on brand some work some don't, I've a Q Tec 5 port usb2 card and it worked perfectly without anything needed doing

---

### Post by Unlockitall on 2007-02-10
actually, do you know if there is a usb 1.1 to 2.0 converter, becaus i only need the one port

---

### Post by teaker1s on 2007-02-10
no, cards are not expensive and usb 2 is faster

---

### Post by Unlockitall on 2007-02-10
huh?

---

### Post by localzuk on 2007-02-10
USB 2 is backwards compatible... You don't have to have a USB 2 port to connect a USB 1.1 device.

You may have the problem that the device is drawing too much power though, in which case, an external powered USB hub should solve that.

---

### Post by teaker1s on 2007-02-10
my experience of some usb 2 devices with external power haven't worked or took for ever to initialise

---

### Post by Unlockitall on 2007-02-10
so what is my best option for making my flash drive work on the old pc (best meaning best inexpesive option) any help is greatly appreciated

---

### Post by nickoli_02 on 2007-02-10
Does the drive mount? Or does it mount but no files are found on the drive when there should be? Is the drive formatted as FAT32 or NTFS? Sorry I don't fully understand the problem :)

---

### Post by Unlockitall on 2007-02-10
localzuk, i have the oppisite problem, i have a 2.0 device and a 1.1 port

---

### Post by Unlockitall on 2007-02-10
no the drive doesnt mount, or even attempt to

---

### Post by nickoli_02 on 2007-02-10
try 
```
sudo mount -t vfat /dev/sda1 /media/sda1
```

if it's a fat filesystem, or

```
sudo mount -t ntfs /dev/sda1 /media/sda1
```

if it's ntfs. You may need to create the /media/sda1 directory

```
mkdir /media/sda1
```

---

### Post by teaker1s on 2007-02-10
it is a usb mass storage device?
add diskmounter to gnome panel-try this

---

### Post by Unlockitall on 2007-02-11
right now its still running windows, i cant get a copy of linux until tomorrow. but the flash drive doesnt mount and i think the ports are usb 1.1, and my flash drive is 2.0

---

### Post by Unlockitall on 2007-02-11
so right now, what is my best option? any help would be greatly appreciated:)

---

### Post by nickoli_02 on 2007-02-11
Are you dual booting ubuntu and windows? does the drive mount in windows?

---

### Post by Unlockitall on 2007-02-11
i dont have ubuntu yet but im getting it tomorrow, and the flashdrive doesnt mount, or try to or anything

---

### Post by teaker1s on 2007-02-12
unless you have xp all previous windows need driver update to recognise Usb Mass Storage Devices-usb sticks normally come with a cd with driver for windows 98/me/nt

---

