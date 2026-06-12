---
title: "how to connect to shared folder"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by prow on 2007-06-22
I set up a shared folder on my linux box....i can see the share from my windows xp laptop but when i try to log in it will not let me.

---

### Post by Najand on 2007-06-22
Did you share it using samba?

---

### Post by NeoLithium on 2007-06-22
There's some good tutorials here to make sure you have everything set up with samba to share the folder:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

---

### Post by prow on 2007-06-22
yea im using samba....like i said i can see the share from my laptop but cant access it

---

### Post by Najand on 2007-06-22
> **NeoLithium said:**
> There's some good tutorials here to make sure you have everything set up with samba to share the folder:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

You didn't even wait to see if he has shared it using samba or not. I assume he is using that, but if not sending him to some tutorial about samba might confuse him. Let us be patient a little.

---

### Post by Najand on 2007-06-22
> **prow said:**
> yea im using samba....like i said i can see the share from my laptop but cant access it

OK, you may use the link he sent to you or you can just simply define user ID needed for samba in the terminal by using
```

smbpasswd -a <YOUR USER NAME>

```
and then enter password.

---

### Post by prow on 2007-06-22
ok i figured it out.....can you guys please help me with another issue that im having?

i have a maxtor onetouch 200GB USB hdd that has some files from a windows computer on it that i would like to mount to my ubuntu machine.  But when i plug the drive in nothing happens.

what code do i need to type in to help that?

---

### Post by Najand on 2007-06-22
Can you plug it to your computer and then type:
```

sudo fdisk -l

```
and copy/paste the output here?

---

### Post by prow on 2007-06-22
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

---

### Post by prow on 2007-06-22
bump

---

### Post by Quintin Riis on 2007-06-22
Please don't "bump" a post like that needlessly.  

Unplug the drive, plug it back in, then do "dmesg | tail" in a terminal, it should tell you the block special file for the disk.

Then do "fdisk -l /dev/<whatever>".

You should be able to mount it with just "mount /dev/foo1 /mnt/foo" or such.

---

### Post by prow on 2007-06-22
[82593.132181] end_request: I/O error, dev sdb, sector 0
[82593.133560] end_request: I/O error, dev sdb, sector 0
[82593.135055] end_request: I/O error, dev sdb, sector 0
[82593.136429] end_request: I/O error, dev sdb, sector 0
[82593.137930] end_request: I/O error, dev sdb, sector 0
[82593.139434] end_request: I/O error, dev sdb, sector 0
[82593.140804] end_request: I/O error, dev sdb, sector 0
[82593.142177] end_request: I/O error, dev sdb, sector 0
[82593.143676] end_request: I/O error, dev sdb, sector 0
[82593.145110] end_request: I/O error, dev sdb, sector 0
 
thats not good i believe

---

### Post by Quintin Riis on 2007-06-22
Not really, no.

Could be the drive, your PC's power supply, or the motherboard.  

Try rebooting.

---

### Post by prow on 2007-06-22
external drive works on windows computer and the usb controller on the linux box reads flash drives.........so drive is good, motherboard is good, and PS is still kick'n

any other suggestions?

---

### Post by prow on 2007-06-22
the one thing i noticed is that in order for me to be able to access the drive on a windows computer i have to install the setup disc for windows.......

could it be that i have to have some sort of driver for it to be able to recognise the drive?

---

### Post by prow on 2007-06-23
well i tried a lacie external hard drive and it mounts right up in seconds..........i guess ubuntu just dont like maxtor.

---

