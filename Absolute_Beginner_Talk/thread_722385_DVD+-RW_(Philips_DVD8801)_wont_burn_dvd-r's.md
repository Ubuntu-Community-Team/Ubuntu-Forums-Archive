---
title: "DVD+-RW (Philips DVD8801) wont burn dvd-r's"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by DamonChyld on 2008-03-12
My old burner was not finalizing disks so I called Dell and they sent me out a replacement drive. After I installed it and restarted, I tried to burn a dvd-r but the nautilus burner complained that the drive would only accept dvd+r dl disks.

I thought that perhaps Ubuntu was having issues because of the swap so I figured the easiest way to make sure it was completely recognized was to do a reinstall. After the reinstall Gibbon I was still having the same issues with the nautilus burner so installed k3b, but it too tells me "Please insert an empty or appendable Double Layer DVD+/- R. 

My lshw output for the drive is 
```
*-cdrom:1
                description: DVD writer
                product: DVD+-RW DVD8801
                vendor: PHILIPS
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 4D28
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom

```
As you can see it says that it accepts dvd-r's and does not mention dl's. I called Dell and they confirmed that the drive is a Philips Dvd8801 and is capable of writing dvd-r as well as dl disks. A google search has not turned up any similar problems so I am hoping someone could help me out.

---

### Post by jseiser on 2008-03-12
just a question - are the discs good quality?  Cheap dvdr's i have been unable to burn on before.  Also, do you have the dvd+rw-tools installed?  I know without that my dvd burner will open and burn cd's etc, but i couldnt write dvd's.

---

### Post by DamonChyld on 2008-03-12
The media I am using is TDK DVD-R's and yes, I do have dvd+rw-tools installed. The drive will burn CD-R's though...

---

### Post by dilly1066 on 2008-05-28
> **DamonChyld said:**
> The media I am using is TDK DVD-R's and yes, I do have dvd+rw-tools installed. The drive will burn CD-R's though...

is this just for single layer.4.37g dvd-rs cause if it is i have a philips dvd 8801 and it does them fine im having big trouble with dual layer like xbox 360 games and stuff can you do them???

---

