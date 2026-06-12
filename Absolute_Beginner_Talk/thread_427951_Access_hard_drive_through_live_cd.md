---
title: "Access hard drive through live cd"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by karishbhr on 2007-04-29
So basically its like this:

ubuntu is messed up for me and i dont know if I can handle the difficulty of linux just yet.  The problem is I already installed it and am having problems with the xserv thing (cannot fix it for the life of me)... instead of bothering anymore I just want to go back to my old OS.  I need to get my files from the linux partition though.  I have an external drive which shows up when using the live cd, which i plan on using to take my files off and onto the external, but my main partition does not.  what can I do?

---

### Post by soulfly7x on 2007-04-29
I don't know how to fix your xserve problem, and I don't know if you can access your Ubuntu partition with the live cd, BUT

You can definitely do it with a PCLinux OS live CD. While I don't like PCLOS enough to install it, I have used the live CD several times to mess with locked files because I'm not smart enough to know how to do it in Ubuntu.

Get the PCLOS live CD and log in as root. Transfer the files. Sorry for the bad experience. I'd try dual booting next time,,, if there is a next time.

---

### Post by Nythain on 2007-04-29
just mount it temporarily somewhere... sudo mount /dev/sd1(or whatever the partition is) /media

---

### Post by [S|G] on 2007-04-29
Do you know what was your main partition? It must have been something like /dev/hda1 or /dev/sda1. If you don't remember, do this:
```
sudo fdisk -l /dev/hda
```
Your hard drive might not be hda, so you can try hdb, hdc, hdd, sda, sdb, etc. After you find out what is your partition, mount it:
```
sudo mount /dev/hda1 /mnt
```
The contents of that drive will be at the /mnt directory so you can copy your files (remember to change hda1 for whatever is your partition.).

If you get the partition wrong, unmount it like this:
```
sudo umount -l /mnt
```
And then try again with another partition.

---

### Post by bobplano on 2007-04-29
i think the internal drive is not mounted which is why it isn't showing up. as for the xserver problem generally 
```
sudo dpkg-reconfigure xserver-xorg
```
will fix it if you have the right drivers

---

### Post by karishbhr on 2007-04-29
> **'[S|G] said:**
> Do you know what was your main partition? It must have been something like /dev/hda1 or /dev/sda1. If you don't remember, do this:
```
sudo fdisk -l /dev/hda
```
Your hard drive might not be hda, so you can try hdb, hdc, hdd, sda, sdb, etc. After you find out what is your partition, mount it:
```
sudo mount /dev/hda1 /mnt
```
The contents of that drive will be at the /mnt directory so you can copy your files (remember to change hda1 for whatever is your partition.).

If you get the partition wrong, unmount it like this:
```
sudo umount -l /mnt
```
And then try again with another partition.

I dont know what the harddrive was labeled as (sda hda or w.e) and i tried your method of finding out and I did not understand what i was looking for

---

### Post by [S|G] on 2007-04-29
You're looking for something like this:
```

diegolima@ColdWire:~$ sudo fdisk -l /dev/sda

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabeças, 63 setores/trilha, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1               1          10       80293+  83  Linux
/dev/sda2           19393       19457      522112+  82  Linux swap / Solaris
/dev/sda3              11       19392   155685915    5  Estendida
/dev/sda5           17435       19392    15727635   83  Linux
/dev/sda6              11        1968    15727572    b  W95 FAT32
/dev/sda7            1969       17433   124222581   83  Linux

```
This is a sample from my own computer (it's in portuguese, by the way). You'll find some partitions that are Linux. On my computer, /dev/sda5 is my root ( / ) partition and /dev/sda7 is my /home partition. 

So if I was to recover my files, I'd mount /dev/sda7.

---

### Post by karishbhr on 2007-04-29
i acutally figured it out but now the two folders I really need to access are not within my "permissions" how do i fix this?

---

### Post by [S|G] on 2007-04-29
Since you're just copying your files, you could start nautilus as root:
```
sudo nautilus
```
That way you wouldn't have to worry about permissions

---

### Post by karishbhr on 2007-04-29
but when i do that it lets me see everything but when I try to copy something to the external it doesnt do anything, no errors or anything.  

It may help to know that when I do the sudo nautilus thing and the new window pops up, my external drive is no longer listed there

---

### Post by [S|G] on 2007-04-29
Ok, try this then:
1 - Open nautilus as root
2 - Right click on the directory you want to copy
3 - Adjust the permissions so that everyone can read the directory
4 - Now try to open nautilus the normal way and try to copy the files

---

### Post by karishbhr on 2007-04-29
worked like a charm :)

---

