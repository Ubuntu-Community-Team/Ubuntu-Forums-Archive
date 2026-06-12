---
title: "Triple Boot Macbook Pro 2011 15&quot;"
date: 2011-08-30
forum: Apple Hardware Users
---

### Post by sebko on 2011-08-30
So i've hit many speedbumps trying to do this!
I'm using this guide

[Lifehacker Tutorial]("http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required")

Now Here is the speedbump i can't figure myself. I installed Windows already, and ubuntu. Ubuntu then asked me to restart after installation. I restarted and Clicked Tux in rEFIt, But it boots into the CD again and asks me to install again or Try it! I then took out the cd and usb, and rebooted and clicked on tux.

"Missing Operating System"

I tried syncing mbr with partition refit thing.
Below is some info from booting with LiveCD+USB.


[screenshot]("http://img84.imageshack.us/img84/3144/screenshotcfl.png")

Installed on sda5.
Any tips would be much appreciated!

PS.

For other people trying to install ubuntu 11.04 on the new Macbook Pros here are some of the solutions to some speedbumps you may experience:

1sts Speedbump.

rEFIT not working, solution: install rEFIt manually

2nd speedbump.

Unable to partition into 3 drives, Windows, Ubuntu, Ubuntu Swap. Solution, boot into RECOVERY HD (lion) and disk utilities then verify drive, then repair drive (Under Macintosh HD).

3rd speedbump.

Unable to boot to Ubuntu, solution:To boot into ubuntu, burn a cd and a mountable USB for mac! use them at the same time

---

