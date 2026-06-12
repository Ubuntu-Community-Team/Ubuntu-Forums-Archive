---
title: "Need clarification on use of bcm43xx-fwcutter"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-01-28
My previous 2 attempts to get either bcm43xx-fwcutter or ndiswrapper to enable my built in Broadcom BCM4306 resulted unbootable Edgy, requiring hard reset.  Because I'm a noob it was more expedient for me to reinstall.  This is an HP pavillion zv5000, running AMD64 Edgy.  I have a 64bit driver from another user here on the ubuntu forum,BCMWL564.SYS. 

Other than this wireless chip and the SD cardreader, Ubuntu-amd64 runs like candy on this laptop.

I'm following this guide for fwcutter now. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy")
I have fwcutter pointed at the driver I believe it should write to /lib/firmware/2.6.17-10 but I get an error.

```
root@ck-laptop:/home/ck/Desktop/BCMDriver# bcm43xx-fwcutter -w /lib/2.6.17-10-generic BCMWL564.SYS
bcm43xx-fwcutter can cut the firmware out of BCMWL564.SYS

  filename :  bcmwl564.sys
  version  :  3.70.17.5
  MD5      :  f5590c8784b91dfd9ee092d3040b6e40

extracting bcm43xx_microcode2.fw ...
/lib/2.6.17-10-generic/bcm43xx_microcode2.fw: No such file or directory

```
It may just be a syntax error on my part, I dont know.  Thanks in advance.

---

### Post by Blutack on 2007-01-28
From
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

If you are using 64bit Edgy Eft and the 2.6.17-10-generic, make sure you are NOT using the 2.6.17-10-generic kernel as it doesn't work (after running the script, you will be warned if there is a problem). If you need help finding a different kernel, check here.

---

