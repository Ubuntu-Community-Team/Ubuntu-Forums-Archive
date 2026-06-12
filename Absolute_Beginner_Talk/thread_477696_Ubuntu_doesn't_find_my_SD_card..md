---
title: "Ubuntu doesn't find my SD card."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-06-18
I have a Windows Mobile 2003 pocket PC and used an SD card on it to store files, however, I can't find it on Ubuntu - Computer doesn't display it and when it displays the drive, I get:

```
**Unable to mount media.**
There is probably no media in the drive.
```

Any solutions?
Thanks.

---

### Post by CaptainInsaneO on 2007-06-18
It's probably a problem with the filesystem that it was formatted in. Do you happen to know what it was formatted as? (RAW, NTFS, fat16/32).

---

### Post by eoghanmurray on 2007-06-18
I don't know - whatever Windows Mobile 2003 formats it as - probably RAW then.

---

### Post by CaptainInsaneO on 2007-06-18
Most likely.

My digital camera formatted my SD card as RAW as well... now it too does not work in media card readers. I don't know why this is, but I'll do some searching for you to see if we can get you fixed.

---

### Post by CaptainInsaneO on 2007-06-18
[Try this program out]("http://software.techrepublic.com.com/download.aspx?docid=250752") and see if there's any corruptions. If not, find out what the format is and we can go from there.

---

### Post by eoghanmurray on 2007-06-21
RAW. WM2003 formats in RAW format.

---

### Post by CaptainInsaneO on 2007-06-22
Do you have a Windows install you could test the card on? There are a couple known bugs out there in Ubuntu with card readers. ([Click here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/47367")) If the card does indeed work in Windows, your card reader might be incompatible with Ubuntu.

I tested out my own SD card (which I know for a fact doesn't work in Windows - it too is classified as RAW), but it works fine in Ubuntu. It shows up as vfat.

---

### Post by eoghanmurray on 2007-06-23
It crashes. Windows Explorer (explorer.exe)

---

### Post by te.ss on 2007-06-29
hi,
Did you manage to fix your SD card problem?   If you did, do you mind sharing it?

I have a similar problem and have not seen any responses to this thread.

---

