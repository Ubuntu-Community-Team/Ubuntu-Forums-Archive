---
title: "Burning iso image with finder."
date: 2017-04-18
forum: Apple Hardware Users
---

### Post by brokeisoguy on 2017-04-18
I'm facing problems with *ubuntu-gnome-17.04-desktop-amd64.iso *as well. On my Mac OS machine I'm not able to open the iso with the disk utility app. If I burn the iso image with finder (right-click on iso, burn image ..) it fails in the end. Can someone confirm that the provided iso is intact?

---

### Post by Cbhihe on 2017-04-18
@brokeisoguy:
Your question has little to do with the problem in OP, I believe, and you probably want to start a new thread.
But here are the first elements that you probably need to start troubleshooting. Please don't respond to this here.
If you choose to, do so in a different thread, taking this thread's 10th post as a reference.
1) [Here]("https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos") and [here]("https://help.ubuntu.com/community/BurningIsoHowto") are the instructions to burn a USB flash drive with an ISO image in a MacOS environment.
2) On the Canonical [official repo]("http://cdimage.ubuntu.com/ubuntu-gnome/releases/17.04/release/"), you will find several hash fingerprints for Zesty-gnome (MacOS version). 
Choose one, e.g. md5sum, and check that the hash fingerprint of your downloaded ISO is identical to that found following that [link]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Mac_OS_X")... 
To obtain the md5sum fingerprint and compare it with the official one, the console command is: ```
$ md5sum your-iso-file.iso
```
Good luck.

---

### Post by howefield on 2017-04-19
Posts moved to own thread and to the "*Apple Hardware Users*" forum for a better fit.

---

