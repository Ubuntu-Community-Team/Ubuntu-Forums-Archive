---
title: "USB-HDD writing"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by goobermaster on 2007-08-30
Hi, I am trying to backup a partition on a computer that I just formatted(the system partition)

I realized that I have to format the _whole_ disk and I need to keep those files.

Therefore I am trying to use the ubuntu liveCD in order to copy these files to an external usb hard drive.

However, I cannot write them (or anything) to the usb device as it says that I do not have permission.

Can anybody help me on this? I know little about the inner workings of ubuntu...

---

### Post by very_japi on 2007-08-30
I dont know how mounting behaves on a live cd. although... i would bet my two cents this  could work.

```
sudo mount /dev/{you usb drive logical address} /home/{your user name}/Desktop
```

As i never have used the ubuntu live CD i have no clue wether this will work. Keep me posted.

---

### Post by schorsch on 2007-08-30
What is the filesystem on the USB device? FAT32, NTFS ... or something else?

---

### Post by goobermaster on 2007-08-30
ntfs it says under properties...

---

### Post by very_japi on 2007-08-30
I might be playin naive, ut have you checked if, once ou plug in your Flash drive, a new USB 2.0 Flash disk appears in Places->Computer?

if so... the just right  click on it, and select "mount"

also, post the output of

```
ls /dev -l
```

---

