---
title: "formatting/partitioning  problems"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2007-11-15
ok so i have ubuntu 64 bit  installed on my new computer

i have worked some of the bugs with the display out now i want to add storage space 

i had 4 sata ntfs drives attached but want to.

1 learn how to format.partition,and use them in ubuntu 
2 attempt to make them part of the operating system not just an added thing 

i have gparted live cd but it gives me an error when i try to format the drive as ext3 

i ran it in live mode from the cdrom during bot up i can see the drive and adjust the size but when i click apply it will not continue also what is it supposed to be called?

what am i doing wrong ? is there  a special way to do this ? what s the preferred method to add storage space to a machine ?
 i plan on completely moving away from xp i wont even use the drive that it is installed on yet 

what am i missing?  please help i have had ubuntu for about a week now so the termnal is kinda scary i have used it but not sure of myself with it

---

### Post by Qwerty_ on 2007-11-16
If you want you can keep the drives in NTFS format.

Run the following command in your terminal.

```
 sudo apt-get install ntfs-config
```

Once it has installed run

```
sudo ntfs-config
```

And configure as required.

---

### Post by rexxxlo on 2007-11-16
i don't want to keep ntfs format 

and i allready deleted the partition so its gone anyways

is there a reason to keep it ntfs other than the abilityto go between xp and ubuntu?

i figure the usb drive is what that is for right?

---

### Post by rexxxlo on 2007-11-16
oh and i get errors whenever i use the terminal 

> lolo@lolo-desktop:~$ Reading package lists... Done
bash: Reading: command not found
lolo@lolo-desktop:~$ Building dependency tree       
bash: Building: command not found
lolo@lolo-desktop:~$ Reading state information... Done
bash: Reading: command not found
lolo@lolo-desktop:~$ The following packages were automatically installed and are no longer required:
bash: The: command not found
lolo@lolo-desktop:~$   swh-plugins blop cmt libcurl3 libfltk1.1 liblo0 libraptor1 liblrdf0
bash: swh-plugins: command not found
lolo@lolo-desktop:~$ Use 'apt-get autoremove' to remove them.
bash: Use: command not found
lolo@lolo-desktop:~$ 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bash: 0: command not found
lolo@lolo-desktop:~$ 1 not fully installed or removed.
bash: 1: command not found
lolo@lolo-desktop:~$ Need to get 0B of archives.
bash: Need: command not found
lolo@lolo-desktop:~$ After unpacking 0B of additional disk space will be used.
bash: After: command not found
lolo@lolo-desktop:~$ Setting up emifreq-applet (0.18-3ubuntu2) ...
bash: syntax error near unexpected token `('
lolo@lolo-desktop:~$ Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
bash: Starting: command not found
lolo@lolo-desktop:~$ invoke-rc.d: initscript emifreq-applet, action "start" failed.
bash: invoke-rc.d:: command not found
lolo@lolo-desktop:~$ dpkg: error processing emifreq-applet (--configure):
bash: syntax error near unexpected token `('
lolo@lolo-desktop:~$  subprocess post-installation script returned error exit status 2
bash: subprocess: command not found
lolo@lolo-desktop:~$ Errors were encountered while processing:
bash: Errors: command not found
lolo@lolo-desktop:~$  emifreq-applet
bash: emifreq-applet: command not found
lolo@lolo-desktop:~$ E: Sub-process /usr/bin/dpkg returned an error code (1)
bash: syntax error near unexpected token `('


---

### Post by Inxsible on 2007-11-16
If you are planning to get rid of XP completely, simply use GParted on the live CD and format the windows partition.


Make sure that the partitions are NOT mounted while you do this, else it will not be able to format them.

---

### Post by rexxxlo on 2007-11-16
well i tried gparted live and i get errors it will not let me continue after i click apply 

i do not have xp on the disk either it was just an ntfs storage drive now its empty and i don't know what to do with it. i cant see it in places>computer or in the system monitor.

---

### Post by Inxsible on 2007-11-16
> **rexxxlo said:**
> well i tried gparted live and i get errors it will not let me continue after i click apply 

i do not have xp on the disk either it was just an ntfs storage drive now its empty and i don't know what to do with it. i cant see it in places>computer or in the system monitor.
are you sure its not mounted while you are trying to format it ?

if you see a triangle with an exclamation mark or a lock sign near the partition, you need to fix that before you format

---

### Post by rexxxlo on 2007-11-16
can a drive be mounted in gparted live?

i will try again and convey the results 
thanks

---

### Post by rexxxlo on 2007-11-17
ok  gparted live wont let me do an ext2 or ext3 it will however partition and format fat 32....so that is what i did.

next i booted ubuntu went into computer and the drive was a visible as a read only drive. from there i went to  system>administration>partition editor (gparted) to find that drive and from there i was able to fromat to ext3. why did this happen and what am i doing wrong?

now the drive disappeared from places>computer but i can see it in the hardware manager as a "storage block" 

where is it and how do i use it ?

---

### Post by rexxxlo on 2007-11-17
sudo fdisk -l     gives me 

> lolo@lolo-desktop:~$ sudo fdisk -l
[sudo] password for lolo:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fc52fc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38184   306712948+  83  Linux
/dev/sda2           38185       38913     5855692+   5  Extended
/dev/sda5           38185       38913     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


---

### Post by Inxsible on 2007-11-17
your sdb drive needs formatting. the partition tables are all messed up. The format that you did was probably not successful.

---

### Post by rexxxlo on 2007-11-17
will i be able to do this with the gparted in the operating system or will i have to do it with the live cd?

---

### Post by Inxsible on 2007-11-17
> **rexxxlo said:**
> will i be able to do this with the gparted in the operating system or will i have to do it with the live cd?you can do it either way. you just have to make sure that the drive is NOT mounted when you are trying to format it.

---

### Post by rexxxlo on 2007-11-17
ok i formatted it again 

i get this though

> lolo@lolo-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fc52fc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38184   306712948+  83  Linux
/dev/sda2           38185       38913     5855692+   5  Extended
/dev/sda5           38185       38913     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
lolo@lolo-desktop:~$ 



---

### Post by Inxsible on 2007-11-17
> **rexxxlo said:**
> ok i formatted it again 

i get this though
no you didnt format it properly. the sdb still says there are no partition tables on it.

You need to select Format it to EXT3 or NTFS or whichever file system you want for that drive. it will take quite some time since its a 300 gb drive

---

### Post by rexxxlo on 2007-11-17
yea i did i think it says everything is fine here are a few screenshots

>>>>>here is applying the operations<<<<<

[IMG]http://i232.photobucket.com/albums/ee266/psychoacoustics/Screenshot-2.png[/IMG]

[IMG]http://i232.photobucket.com/albums/ee266/psychoacoustics/Screenshot-3.png[/IMG]




>>>>>and here is after<<<<
[IMG]http://i232.photobucket.com/albums/ee266/psychoacoustics/Screenshot-4.png[/IMG]

what do i need to do differently?

---

### Post by Inxsible on 2007-11-17
That does look like it did format it to ext3. What does sudo fdisk -l say now? post it here please.

---

### Post by rexxxlo on 2007-11-17
lolo@lolo-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fc52fc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38184   306712948+  83  Linux
/dev/sda2           38185       38913     5855692+   5  Extended
/dev/sda5           38185       38913     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
lolo@lolo-desktop:~$

---

### Post by rexxxlo on 2007-11-17
oh and gparted doesn't let me have the option to unmount this drive i assume because it isnt mounted?

---

### Post by rexxxlo on 2007-11-17
anymore ides anyone?

---

### Post by Inxsible on 2007-11-17
> **rexxxlo said:**
> anymore ides anyone?just try and start the installation.

It should be unmounted while you are formatting it.

---

### Post by rexxxlo on 2007-11-17
i tried to check and repair the file system with gparted 

it says all operations completed successfully

but it in fdisk -l  i still get 
Disk /dev/sdb doesn't contain a valid partition table

it will not show up in computer  or system monitor ?

---

### Post by Inxsible on 2007-11-17
maybe, there is hardware problem with your drive. I am not saying that it is, but it might be worth looking into.

---

### Post by rexxxlo on 2007-11-17
ok so i plugged in the xp drive rebooted into xp went to computer management found the drive formatted  it and tested it bu coying a file to it 

ll seems fine i will go back to ubuntu and try again

---

### Post by Inxsible on 2007-11-17
> **rexxxlo said:**
> ok so i plugged in the xp drive rebooted into xp went to computer management found the drive formatted  it and tested it bu coying a file to it 

ll seems fine i will go back to ubuntu and try againgood luck :D

---

### Post by rexxxlo on 2007-11-17
still wouldn't work  so i threw in the live cd and did a fresh install to the drivein question.....needless to say it works fine now

---

