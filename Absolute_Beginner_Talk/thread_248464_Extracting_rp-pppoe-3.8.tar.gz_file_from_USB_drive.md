---
title: "Extracting rp-pppoe-3.8.tar.gz file from USB drive"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Stephen_A on 2006-09-01
Hi, I'm following the instructions for 'Easy PPPoe connections' on the following link. 
[http://ubuntuforums.org/showthread.php?t=183062&highlight=pppoe](http://ubuntuforums.org/showthread.php?t=183062&highlight=pppoe)

I've installed the software by using 

  sudo apt-get install build-essential. 

But the only way I can get the rp-pppoe-3.8.tar.gz file is to download it on another (Windows) machine, copy it a USB flash drive and then plug the drive into the Linux box. 

Would somebody be so kind and tell me exactly where I need to copy this file so that the command:

   tar xzf rp-pppoe-3.8.tar.gz

...will correctly extract the file? Or please could someone tell me how to extract this file from the USB drive so that the software is correctly installed? I've extracted it on the USB drive and clicked on the 'go' file and some installation seems to take place. However the test command - 

  sudo pppoe-start

Just gives 'command not found. 

Thanks very much for your patience and help.

---

### Post by nickpaton on 2006-09-01
Stephen

You will need to copy the file rp-pppoe-3.8.tar.gz file from the USB drive into your Home/Stephen directory (or whatever you call yourself within the Home Directory!) and run the commands from there.

---

### Post by Stephen_A on 2006-09-01
Nick, 
Thank you for your reply. So that's were the downloads should go. 

Stephen.

---

