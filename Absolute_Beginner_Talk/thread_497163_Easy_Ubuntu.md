---
title: "Easy Ubuntu"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by cino on 2007-07-09
After installation of easy_ubuntu for Dapper, I am told to load real player 10 from sound & video but alas, it is not there.

Also, system tools-->nVidia settings does not work:
Details: Failed to execute child process "nvidia-settings" (No such file or directory)

Pretty olde computer I am on with a NV31 [GeForce FX 5600XT].

The card is seen in device manager but as a new user I am a bit confused as to whether it is working properly or not.

status = status
device type & capabilities =unknown

I thought I would use easy_ubuntu...

---

### Post by chrome saint on 2007-07-09
Are you using the proprietary nVIDIA driver that you have to download after installing or just the plain one included in the distribution?  In 7.04 the install automatically used the proprietary INTEL wireless driver but I had to download and enable the nVIDIA one after the install was complete and I had downloaded the 70 odd updates to the system.

Once you have the proprietary nVIDIA driver installed you can launch the nVIDIA X Server Settings application and configure the operation of the card and monitors.  At a command prompt you type **nvidia-settings** to launch it.  I set it up as a launcher so I could just double click an icon when needed instead of typing the command.

---

### Post by cino on 2007-07-10
cheers

---

