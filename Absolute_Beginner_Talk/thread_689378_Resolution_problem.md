---
title: "Resolution problem"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Domy on 2008-02-06
Hi

I have a problem. I can't change resolution higher than 1024*768. I have 19" monitor, i have downloaded ati driver for my graphic card ati radeon 9600xt and i can't (i don't know how to install this driver). When I click at the downloaded .run file, firefox automaticaly starts it and instalation doesn't start. :S 

Any ideas?

please help, I am new in linux ;)

---

### Post by OffAxis on 2008-02-06
Updating the driver and available screen resolutions are not necessarily the same thing.

For the driver try the 'Restricted Driver Manager'. It's in System Settings, I believe.

To modify the available screen resolutions try this

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Domy on 2008-02-06
Thnx man. It works.:)

---

### Post by OffAxis on 2008-02-06
glad to help.
:)

---

### Post by LouieIV on 2008-02-06
New to Linux, Ubuntu, and the forum. I have a very similar problem. I'm running an old nVidia GeForce2 GTS I belive I have the legacy drivers installed although I don't know where to find the version so I can't verify that it is nvidia's last release. I assume since it's called legacy that it is the last release. The highest resolution I get is 800x600. I tried "sudo dpkg-reconfigure -phigh xserver-xorg" after that not sure if I was supposed to do anything else in the terminal? Went to system- administration- Screens and Graphics and there were a couple more lower resolutions. I'd like to be able to bump it up 1 or 2 notches.

Any help is much appreciated :)

-LouieIV

---

### Post by LouieIV on 2008-02-06
Problem solved. I changed to lower res and rebooted viola! all kinds of res choices.

Found this solution in this thread [http://ubuntuforums.org/showthread.php?p=4282450#post4282450]("http://ubuntuforums.org/showthread.php?p=4282450#post4282450")

-LouieIV

---

