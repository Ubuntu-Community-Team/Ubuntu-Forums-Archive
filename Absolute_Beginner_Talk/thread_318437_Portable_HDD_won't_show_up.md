---
title: "Portable HDD won't show up"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by The Iron Curtain on 2006-12-14
Hi, I tried to look for answers, but I couldn't find any....

I have a 20GB portable harddrive that I used in my windows days to back up files and store stuff on. As far as I know, it has FAT32 format. 

When I connect it by USB, nothing shows up on my desktop, and I've poked around the dev and mnt folder and couldn't find anything that resembled my harddrive. 

Am I supposed to do something special to get it to work, or is it supposed to be  automatically recognized?

I'm new to linux, so I don't know much, but I've had to use the CLI before, so that's no problem.

One thing, when I used it on my windoze machine, at some point windows stopped auto running it. I would have to manually open it to actually access it. I don't know if this is relevant, but maybe.

THank you very much! these forums have always been a fast response.

---

### Post by bodhi.zazen on 2006-12-14
Plug in our disk

post the output of ```
sudo fdisk -l
```

---

### Post by The Iron Curtain on 2006-12-14
Okay:

```

dfoer@dfoer-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2341    18804051   83  Linux
/dev/hda2            2342        2432      730957+   5  Extended
/dev/hda5            2342        2432      730926   82  Linux swap / Solaris
dfoer@dfoer-laptop:~$

```

BTW, my laptop HDD is 20 Gigs as well

---

### Post by xyz on 2006-12-14
Seems like your external HD isn't there.
As an exemple, I'll post what mine look like:
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+   b  W95 FAT32
/dev/sda2            1913        6374    35841015    b  W95 FAT32
/dev/sda3            6375        9733    26981167+   b  W95 FAT32

My external HD is divided into 3 partition. I used Gparted Boot CD to achieve that.
One important thing to find out is: is your external HD converted to vfat or what? 
Mine's in FAT because I share it.
A quick check: System > Administration > Disks...it may be possible to mount it there.
Also go here:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Let us know...

---

### Post by bodhi.zazen on 2006-12-14
I agree with XYZ

What is the brand and model of your external HD, check to see if it is compatible with Linux.

---

### Post by The Iron Curtain on 2006-12-15
[quote=xyz]
One important thing to find out is: is your external HD converted to vfat or what?
Mine's in FAT because I share it.
A quick check: System > Administration > Disks...it may be possible to mount it there.
[/quote]

I checked on another computer and it is indeed FAT32 ... or it could be ATF23 and I'm just very dyslexic :p

I checked System > Administration > Disks ...  and I don't know how to mount from there. It shows my laptop HDD and my CD ROM, but no external HDD.


[QUOTE=bodhi.zazen]What is the brand and model of your external HD, check to see if it is compatible with Linux.[/QUOTE]

I bought the HDD in Shanghai. I bought the actual harddrive from one vendor (I have no idea what brand or anything) and then walked over to another guy and bought the case. He also installed the harddrive into the case. The case is an IBM travelstar.

One last bit of info....before I had this laptop , I had another running XP. I would use my portable HDD to back up my files from the laptop. One day, I had it plugged in and inevitably, Windows froze and I had to disconnect the power to shut it down. When I restarted, Windoze was corrupt (and not just morally) and I lost my settings. However, I was able to view my external HDD and I found a number of hidden files... ones that looked like important XP-related files like command.com and desktop.ini

I have no idea if the above is relevant to anything (besides probably explaining why my former laptop crashed), but I figured I might as well mention it in case it's important.

---

### Post by xyz on 2006-12-15
To find out what brand your HD is, run this in a terminal with...the external HD plugged in, of course:
```
sudo lshw
```
Look for something like this. This is my external HD:
>   *-disk
                      description: SCSI Disk
                      product: MP0804H
                     ** vendor: SAMSUNG**
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: UE10
                      size: 74GB
                      capabilities: partitioned partitioned:dos
                    *-volume:0
                         description: W95 FAT32 partition
                         physical id: 1
                         bus info: scsi@0:0.0.0,1
                         logical name: /dev/sda1
                         capacity: 14GB
                         capabilities: primary


---

### Post by The Iron Curtain on 2006-12-15
Thank you for that handy command! Unfortunately, I read the whole thing and could not find anything that looked like my portable HDD. My guess is that it's not recognized.

---

### Post by xyz on 2006-12-15
You need to mount your drive...mounting sorf of means make the drive accessible,visible,usable.
But first you need to create a mount point.
In a terminal and with the drive plugged in, try and type/copy/paste one line at a time:
```
sudo mkdir /media/usb
sudo mount -vfat /dev/sda1 /media/usb -o users,rw
``` 
Also try this in a terminal and see what gives:
```
lsusb
```

---

