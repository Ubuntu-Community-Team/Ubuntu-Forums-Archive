---
title: "ATI Drivers installed and now &quot;Preinitdal failed&quot;"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by buhrmi on 2007-04-19
Hi there,

I'm totally new to Linux / Ubuntu (well I had Suse 5.? installed many years ago but installing it was all I was able to manage) and thought I should give it a try. So I installed the currently released 7.04 Feisty Fawn.

I followed this exact guide to install the prop. ATI drivers for my 9600 Pro: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Now, i get the error message: PreIntiDAL failed ...and... no screens found when booting linux.

I've searched the forums and found two possible solutions for my Problem: Disable the Framebuffer in the kernel and takeout the VGA= option in grub.conf . BUT: How would I do that? O.o All I have is a command line. I'm kinda lost right now ^^

Help appreciated ;)

Thank you :popcorn:

---

### Post by buhrmi on 2007-04-19
Here is the exact Message:
(EE) fglrx(0): PreIntiDAL failed
(EE) fglrx(0): PreInit failed
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

:(

---

### Post by ajgreeny on 2007-04-19
To be honest I have found the fglrx driver for my 9200SE card not worth the hassle.  You should also find that the open source ati driver works great with your card and will give 3D as well, so you can run beryl if you want.

Run *sudo dpkg-reconfigure xserver-xorg* in a terminal and change just the driver to ati, but accept all other things as default, and see if that works better.

---

### Post by buhrmi on 2007-04-19
Hi,

ok I'll try the open drivers. I planned to use the ati drivers in order to play world of warcraft using wine. Will this still be possible with the open source drivers?

---

### Post by buhrmi on 2007-04-19
So

here I am finally having figured out how to install wine and launch world of warcraft with it. on a second thought, that was not very difficult. I wonder why it took me so long. Oh well... everything seems easy when you finally get the idea ;)

HOWEVER... In world of warcraft I have about 10 SPF (thats seconds per frame or 0.1 FPS). is there a way to get to a reasonable framerate using the open source drivers? If I know there is no way, I'd go back and fizzle with the prop. drivers.

Help appreciated - again :popcorn: 

buhrmi

---

### Post by ajgreeny on 2007-04-19
Sorry, I don't know about that as I'm not a gamer at all.  I'll bet someone else knows and will tell you how, if it is possible to do with the OS driver.

---

