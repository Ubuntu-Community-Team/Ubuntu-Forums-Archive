---
title: "[SOLVED] Mount Issue after suspend"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2006-12-09
Hi all,

  I've set my laptop (Dell Inspiron 1300) to go into suspend mode when I close the lid. Till that there was no problem.

  However, today I had a USB flash drive, network and FTP mounts. When I came back from suspend I had all kinds of mounts issue with them.

1- USB
 My USB was not accessible. Could not ```
sudo umount /media/usbdisk
```. Could not umount by right clicking. Kept adding another 2 mounts (usbdisk2, usbdisk3) also unaccessible.

2- My FTP mount (setup through Places => Connect to Servers) was gonne. This one is normal, as involves authentication

3- My network mount was gonne, **with my local folder**.
```
sudo smbmount //hostname/share /localfolder -o username=defaults,password=defaults
```
 There's no authentication needed for this share

  I know some ppl where having issues with suspend, but I haven't seen anyone having issue with local mounts....

  Can anyone help?



Vic...

---

### Post by dbbolton on 2006-12-10
did you try sudo mount -a  ?

---

### Post by victorbrca on 2006-12-10
I'm not using a boot mount cz it's for my laptop. All I do is run this code when I'm home and want to access a share on my XP desktop.

  The mount was not added to fstab.

  Now, since that happened I'm not able to mount it anymore. Only the share, FTP and usbkey are working normal...


Vic

---

### Post by victorbrca on 2006-12-11
Does anyone have any takes on this?

I'm not able to mount that share after the crash!!! I can still access the folder, but every time I enter the mount command it asks me for my sudo password and them the system freezes and there's nothing I can do other than a hard restart.. ](*,) 

This is the command

```
sudo smbmount //hostname/share /home/documents/localfolder -o username=defaults,password=defaults
```


Vic.

---

### Post by z600 on 2007-02-20
I was having a similar problem when my dell inspiron 6400 went into suspend mode. I found that I could unmount the share as follows:

sudo umount -lf share_name

followed by

sudo mount share_name

It's a little annoying but it gets the job done.

---

