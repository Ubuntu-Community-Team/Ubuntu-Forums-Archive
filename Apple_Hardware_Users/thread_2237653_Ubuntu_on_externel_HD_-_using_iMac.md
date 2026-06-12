---
title: "Ubuntu on externel HD - using iMac"
date: 2014-08-03
forum: Apple Hardware Users
---

### Post by maltje on 2014-08-03
Hi,

After a long time I would try to get Ubuntu again.
I installed it on a External HD but I have no dual boot on my Imac.
At the end of the installation I got an error,no startup on the disk,or something like that.
What can I do to start ubuntu from external HD?
I try to use refit,but don't understand it good.

Kind regards.

---

### Post by sudodus on 2014-08-03
I have no Mac so I cannot give any direct help, but I suggest that you read these links.

See [How to install Ubuntu on MacBook using USB flash drive]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick") and [this Ubuntu Forum thread by Quackers]("http://ubuntuforums.org/showthread.php?t=2174630")[URL="http://ubuntuforums.org/showthread.php?t=2174630"]
[/URL]
You might also post in Quacker's thread hoping to get some help.

---

### Post by coffeecat on 2014-08-03
*Thread moved to **Apple Hardware Users**.*

I've also added iMac to your thread title to help attract those with experience of this.

Good luck.

---

### Post by julian13 on 2014-08-04
I have the same problem.

And I don't want use rEEFInd as Bootmanager. I found this solution:
[http://ubuntuforums.org/showthread.php?t=2144172](http://ubuntuforums.org/showthread.php?t=2144172)

I can install Ubuntu on my external drive but the Bootmanager from Mac don't find it in the end... something is going wrong...^^'

Edit: With Fedora I have no trouble.

---

### Post by entangled on 2014-08-07
@julian13 I use an iMac and boot OSX (Mavericks and Yosemite) and linux. Refind is very useful to detect and load boot images.
I found that only Fedora and Arch installation media (disk and USB) were capable of being detected by the iMac firmware.  
Others, like Ubuntu, Kubuntu, Debian, OpenSUSE, were all ignored.
I think it is because my iMac has no BIOS emulation mode set up; it is pure gpt boot and these other distribution media need BIOS to boot. 
ubuntu publishes images for mac but they will only boot when BIOS emulation mode is present. See the 'Answers' on [http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image](http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image) .

---

