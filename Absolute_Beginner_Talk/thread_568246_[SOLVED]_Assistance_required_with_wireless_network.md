---
title: "[SOLVED] Assistance required with wireless networking issue."
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-10-05
Okay, I've got a computer with Ubuntu 7.04 installed onto it.  I'm trying to get my wireless to work, the problem is, I've followed a tutorial to install the Serialmonkey driver for it, and it hasn't worked. The lights flash on it when it turns on, however still there is no luck trying to connect.  It can see the wireless networks.

The output of the lsusb command gives me the following ID:
```

ID 07d1:3c03 D-Link System

```

I followed [this]("http://www.linuxquestions.org/questions/ubuntu-63/how-to-install-rt73-driver-for-dwl-g122-rev.-c1-in-ubuntu-578894/") tutorial to get it to work, however when I attempted the 
```

sudo rmmod rt73usb
sudo rmmod rt2570

```
commands, they failed to work.
```

module rt73usb does not exist in /proc/modules

```

I can get it to see the wireless router with the 
```

iwlist scan

```
command.



It is a D-link G122 rev C. 


I'm not sure quite what I'm doing wrong here...


Any help would be greatly appreciated on this matter.    

Does ndiswrapper support this dongle?

Thanks.




I posted this in the "networking" thread, but it's dropped off the first page and nobody's replied and it's been a few days, so I'm posting it here.  Thanks for the understanding.

---

### Post by OffAxis on 2007-10-05
> I can get it to see the wireless router

so the card itself is working?
It's just not connecting to the network?


what does
[B]iwconfig
[/B]
give you?

---

### Post by ayenack on 2007-10-05
This is the best way to get the D-Link DWL-G122 rev C1 working.

[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

Ndiswrraper is a disaster with this USB dongle in my experience.

---

### Post by Neon_Knight on 2007-10-05
> **ayenack said:**
> This is the best way to get the D-Link DWL-G122 rev C1 working.

[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

Ndiswrraper is a disaster with this USB dongle in my experience.

That is extremely long and extremely complex for myself to understand fully... D:

Does anybody mind making a short tutorial (taking the relevant bits from the one you linked - removing unnecessary bits) on how to do this with no internet connection?   :(


And seeing as I've already tried installing some drivers for it...won't that mess things up a bit?

And to the other person who posted, I am not on the computer at the present minute but I shall give you the output of that command as soon as possible.

---

### Post by ayenack on 2007-10-06
If I understand your first post you have already downloaded the serialmonkey driver, correct?
Also do you have the CD you installed Ubuntu with?

Both these will be needed to make the install possible. If you have not got these you'll need to download the serialmonkey rt73 drivers from

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads) (Scroll down to the **rt73 (USB)** driver and download that.)

And the Ubuntu install CD from

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Using a different PC or the wired connection on the install PC. Let me know if you have these or not and I will try to adapt the install process for your PC and get your wireless working.

ayenack.

---

### Post by Neon_Knight on 2007-10-06
> **ayenack said:**
> If I understand your first post you have already downloaded the serialmonkey driver, correct?
Also do you have the CD you installed Ubuntu with?

Both these will be needed to make the install possible. If you have not got these you'll need to download the serialmonkey rt73 drivers from

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads) (Scroll down to the **rt73 (USB)** driver and download that.)

And the Ubuntu install CD from

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Using a different PC or the wired connection on the install PC. Let me know if you have these or not and I will try to adapt the install process for your PC and get your wireless working.

ayenack.


Thank you very much for your help, the problem is sorted.  Anyone else who has a similar problem with this dongle, go to 
[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73) 
to solve the problem.  It looks complicated, but it really isn't.

---

### Post by thamood on 2007-10-06
i don't know if this will help..but when my patop connects to an wireless network it's takes a looong time be4 it can surf the internet an and i dont know why.. you said that that you can see the wireless network can you connect? if you can onnect try to wait a few minutes then try surfing the internte...!!! it's a long shot but i hope it helps

---

### Post by ayenack on 2007-10-06
Not much help ;). As always the thanks should go to diepruis's thread. Glad you got it sorted though. Mark as Solved so others can learn from your experience. Top of page **Thread Tools>Mark as Solved**.

ayenack.

---

### Post by ayenack on 2007-10-16
This card is now fully supported under Ubuntu 7.10 Gusty Gibbon. WPA and everything. So if you have Gusty you don't need to install anything.

---

