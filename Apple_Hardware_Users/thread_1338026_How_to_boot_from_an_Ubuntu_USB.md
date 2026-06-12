---
title: "How to boot from an Ubuntu USB?"
date: 2009-11-26
forum: Apple Hardware Users
---

### Post by Buuntu on 2009-11-26
I've done a little research about how to boot Linux from a USB in a Mac (MacBook Air) and none of them seem to point to an easy answer.  My questions is just that: is there an easy way to be able to boot from the USB if you're not really willing to mess with the mac settings too much?  Maybe there's a trick you can do from the live CD so you can use that to boot somehow? 
Anything is helpful...

---

### Post by lexfati on 2009-11-26
You could try [rEFIt]("http://refit.sourceforge.net/").  I have rEFIt installed on my macbook (4,1) in order to boot between OS X, Debian, and Windows from the hard drive.   It recognizes when external media is plugged in, and offers to boot from that as well.  I have used it to boot from CD, but I've never actually had a bootable flash drive to test it.

---

### Post by linuxopjemac on 2009-11-26
USB booting is not supported on Macs. You might give a firewire drive a chance. Apple says that you need OSX with a GUID partition scheme, to boot from USB:
[http://support.apple.com/kb/HT1948](http://support.apple.com/kb/HT1948)

There is a way, but it's complicated:
[http://ubuntuforums.org/showthread.php?t=941240](http://ubuntuforums.org/showthread.php?t=941240)

---

