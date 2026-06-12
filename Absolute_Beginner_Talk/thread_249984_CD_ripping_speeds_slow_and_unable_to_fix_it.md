---
title: "CD ripping speeds slow and unable to fix it"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Sensei Eggwoah on 2006-09-03
Hello again,

I've been ripping some of my cds to my computer, but the ripping speeds are not as fast as they should be.  Right now I am only getting 5x ripping speed.  I know it can do better than that. I did some searches on this subject and found advice to do:

```
sudo hdparm /dev/cdrom
```

I get the following:

```
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

So I went ahead with the advice to turn dma on (by the what is dma?).

[quote=http://www.cs.cornell.edu/~djm/ubuntu/#fix-dma]
      If DMA was off for the device, enable it:

      sudo hdparm -d1 /dev/cdrom
      sudo cp /etc/hdparm.conf /etc/hdparm.conf.backup.dma
      sudo gedit /etc/hdparm.conf

      Append the following to the /etc/hdparm.conf

      /dev/cdrom {
             dma = on
      }

[/quote]

However, after entering "sudo pdparm -d1 /dev/cdrom", I get the following error:

```
/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

```

Can anyone help me with this?

---

### Post by Sensei Eggwoah on 2006-09-04
bump

---

