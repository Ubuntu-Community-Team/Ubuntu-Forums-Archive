---
title: "fixing wireless (wi-fi) on ubuntu 16 LTS on 2008 macbook white"
date: 2016-07-29
forum: Apple Hardware Users
---

### Post by diegoghn on 2016-07-29
I find a hard time to fix my wireless connection after i've installed Ubuntu 16 on my old Macbook 2008.
There are so many different solutions for different machines!

So I'd like to share what have worked for me, because I believe that it might be helpfull for many Ubuntu users that run this great OS on these old notebooks.

So, here are the steps i've copy and paste on the Terminal:

1- sudo apt-get remove --purge bcmwl-kernel-source
2- sudo reboot
3- sudo apt-get install firmware-b43-installer
4- sudo modprobe -r b43 && sudo modprobe b43

And that was it! After this last command, the wireless network disconected and conected again. And WORKED!

Thanks for these two forums from which i've got these clues:[https://ubuntuforums.org/showthread.php?t=2173985](https://ubuntuforums.org/showthread.php?t=2173985)
[https://ubuntuforums.org/showthread.php?t=2325823](https://ubuntuforums.org/showthread.php?t=2325823)

---

### Post by howefield on 2016-07-30
Moved to the "*Apple Hardware Users*" forum.

---

