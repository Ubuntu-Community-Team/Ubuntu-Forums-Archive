---
title: "NVidia GT550M on Asus N53S Series - Not Working!"
date: 2012-04-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Ivankh on 2012-04-28
Dear Ubuntu Community,

I have just joined these forums and I am also relatively new to Ubuntu, but very tech. friendly. For the past few days I have been learning sheel scripting intensively which helped me with my current problem to an extent. I will now elaborate:

After a few days of playing with Ubuntu I realised games were not running on it because my Nvidia GT550M graphics drivers were not installed. So I did the following:
- downloaded the nvidia graphics driver from their website
- ran "sudo stop lightdm"
- installed the driver by running "sudo sh /home/aivo/Downloads/drivername.run"
- during installation I was prompted to overwrite the /etc/X11/xorg.conf file after backup which I did
- rebooted the computer and had a black screen with 2 "fail" options :-(
- I went into CTRL+ALT+F1 and copied the backup of the Xorg.conf file
- After reboot all worked again but I the driver wasn't installed...

I did some research on the forums and multiple times came across "bumblebee" which confuses me a lot...

I thought I would start a new thread and hope that someone would have the perfect solution steps to my problem outlined above!

Thank you so much everyone. I look forward to the answer :-)

~Ivankh

---

### Post by oldfred on 2012-04-28
I have a desktop with nVidia card. I have to use nomodeset to get it to boot first time.

But you have the optimus combination of two video drivers which nVidia does not seem to support. There has been some discussion on how soon they might.

Before, most suggested turning off one or the other. But bumblebee seems to be a way to make both work.

Now older, best to check for newer info.
[http://ubuntuforums.org/archive/index.php/t-1749740.html](http://ubuntuforums.org/archive/index.php/t-1749740.html)

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by Ivankh on 2012-04-28
> **oldfred said:**
> I have a desktop with nVidia card. I have to use nomodeset to get it to boot first time.

But you have the optimus combination of two video drivers which nVidia does not seem to support. There has been some discussion on how soon they might.

Before, most suggested turning off one or the other. But bumblebee seems to be a way to make both work.

Now older, best to check for newer info.
[http://ubuntuforums.org/archive/index.php/t-1749740.html](http://ubuntuforums.org/archive/index.php/t-1749740.html)

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

Oldfred, thank you for this fast reply!

I have just read the explanation for the Optimus cards and it doesn't sound good :-(

I guess there isn't much that I can do at the moment. Going to look for a full Ubuntu compatible laptop!

Thanks again!

---

