---
title: "Long 500gb usb ext3 format time"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by extension on 2007-06-03
GParted has been on:

mkfs.ext3 /dev/sda1 

for over an hour on a 500gb USB MyBook. Is this a normal format time for a drive? There is no feedback as to how far along it is so I cant tell if its doing anything or if its locked up. Is there a way to format the drive with feedback? Is canceling the format bad for the drive?

---

### Post by Outrunner on 2007-06-03
Well, formatting ext3 usually takes quite long, and with 500gb, well... Anyway I wouldn't stop the formatting if I were you. Dunno if it can do anything bad, but better safe than sorry

---

### Post by Inxsible on 2007-06-03
Yes, you definitely dont wanna stop a formatting in the middle.

I did format my external 500GB, but it didnt take that long.  :confused:

---

### Post by Golyadkin on 2007-06-03
Well, I am not sure but if the harddisk uses USB 2 Hi-Speed (with the right cable and the right USB 2 port on your computer) it can keep up a sustained transfer rate of 34MB/s. Now your harddisk is roughly 500.000 megabytes. So it will take a minimum of 500.000 / 34 / 60 = 245 minutes (or just over 4 hours). 

If I am wrong, please correct me. Btw, isn't there a "quick format" option for ext3? Like NTFS has...

---

### Post by extension on 2007-06-03
Is there a way to know if the drive is connected using USB 1 or 2?

---

### Post by Golyadkin on 2007-06-03
You can see in your motherboard manual if you have USB 2 or 1 ports. If you computer is newer than 3 years, it is most likely USB 2. If it is older than that, it could be USB 1 still.

---

### Post by Golyadkin on 2007-06-03
Also you can try to run the command:   "lshw"

It shows something like this:
```

        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=128 maxlatency=80
             resources: iomemory:cffff000-cfffffff irq:16
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s

```

---

### Post by Thomas# on 2007-07-06
I have a patch file for ext3 quick formatting,
I tested with USB HD well.

you can get my patch file from here: [http://bean-pig.idv.tw/emb_study/archives/001098.html]("http://bean-pig.idv.tw/emb_study/archives/001098.html")

---

### Post by KyleBrandt on 2007-07-06
Thomas#: How does one use that patch?

---

### Post by Thomas# on 2007-07-10
** How to use this patch file:
# tar xzvf e2fsprogs-1.38.tar.gz
# cp e2fsprogs-1.38_mke2fs_quickformat.patch e2fsprogs-1.38/misc/
# cd e2fsprogs-1.38/misc/
# patch -p0< e2fsprogs-1.38_mke2fs_quickformat.patch 

see README in e2fsprogs-1.38 to compile mke2s(mkfs.ext3).

---

### Post by Raymond Day on 2007-08-16
I have a new 750GB hard drive. Cost $190 with shipping. I want to install Ubuntu server on. It's a old motherboard with 1GB ram and 1000 MHz celeron CPU.

I had to use a IDE to SATA adapter. Ubuntu sees the 750GB hard drive.

[IMG]http://i93.photobucket.com/albums/l41/RaymondDay/Ubuntu/Ubuntu-sees-750GB.jpg[/IMG]

I tell it to use the hole hard drive and it shows the swop and rest ext3.

When it starts to format it goes right to 33% right away. No 1% just right to 33% so is something wrong?  I don't see the hard drive LED going on. The screen shows nothing moving.

[IMG]http://i93.photobucket.com/albums/l41/RaymondDay/Ubuntu/Ubuntu-stuck-formating-750GB.jpg[/IMG]

I left it there for about a hour then turned it off and started over and it did the same. This time I started a stop watch. I guess I will give it 4 or 5 hours to see if it goes to 100%

But because it went right to 33% nothing before that is something wrong?

-Raymond Day

---

### Post by Raymond Day on 2007-08-16
Hay it worked. My stop watch said 38 minutes. Maybe it helped formating for a hour before. I don't know but I guess it went to 33% to a 100% because when I seen it it was done formating.

-Raymond Day

---

### Post by Raymond Day on 2007-08-16
After it rebooted it hangs at:

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 18
_

I guess I will look for Error 18.

-Raymond Day

---

### Post by Raymond Day on 2007-08-16
I put the ubuntu server disc back in and booted in rescue mode and said reinstall GRUB. But it errors saying this:

> Unable to install GRUB in /dev/hda
EXECUTING 'grub-install /dev/hda' failed.

This is a fatal error.

<Go Back>   <Continue>

I don't know what else to do?

I did "/dev/sda1" it came back with no errors.

Rebooted but it still did error 18.

-Raymond Day

---

