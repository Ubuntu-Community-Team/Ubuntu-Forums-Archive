---
title: "Trying to add a new disk drive"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Schmic on 2006-01-12
First post, new to ubuntu. I have limited experience in linux (some mandrake 9 a little while back and long forgotten cli)

I require some help on some partitioning problems. I have added a second hard disk drive(hdc) to ubuntu and wish to use it for storage as my first drive is not very large. I have searched this forum and they have come to be a great help and is my first stop on any problems i have. But alas i have as yet not found the sollution to my particular problem.

Basically i added a second drive that i wish to put files on that i will share on my local network with windows using samba.

I have:
1.	Erased partitioning on the drive using parted(previously had NTFS partitioning)
2.	Formated the drive to EXT3 using fdisk
3.	Tried to change fstab by adding
		/dev/hdc1	/shared		ext3	rw		0	0

I am missing something because i am not able to access the drive so far.

The things that seem to make my situation different to others that i have found amoungst the searches i have done are the following:

1.	This ubuntu is headless(all access via vnc) and
2.	With the second drive in i cannot use a live cd, the disk drive has to replace the cd drive in the box(no choices there)

My methods were probably a bit adhock to get where i am but i seem to have come to a point where my fumbling will not provide a solution and i need some experience applied to my situation.

---

### Post by La1nE on 2006-01-12
You remembered to type
```

$ sudo mount -a

``` 

I forgot that, the last time i mounted a drive. ;)

---

### Post by gosh on 2006-01-12
[QUOTE=Schmic]
2.	With the second drive in i cannot use a live cd, the disk drive has to replace the cd drive in the box(no choices there)

.[/QUOTE]

I don't understand your problem completely.

What do you mean exactly?
Can't you boot a live CD?
Have you set your BIOS to boot from CD?
And why is your 2nd harddisk hdc in stead of hdb?

---

### Post by Schmic on 2006-01-12
I cannot use the cd drive and the second hard disk drive at the same time due to constraints in the PC box itself. I am not sure why the disk is /hdc instead of /hdb but i do not believe that would be causing a problem.

---

