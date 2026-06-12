---
title: "[SOLVED] driver install problem"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Emmazing on 2008-01-30
I am trying to install an NVIDIA driver update since that's what card I have and the driver I have won't work. I'm sure that this is the driver I need, but I can't get it to install. I followed [The instructions that came with it on the NVIDIA site]("http://www.nvidia.com/object/linux_display_ia32_169.04.html") and made sure that the checklist provided in the link was good as well. I'm just having a problem running the script. I tryed the command they provide to install it but get the error
```
emma@ubuntu:~$ sh NVIDIA-linux-x86-169.04-pkgl.run
sh: Can't open NVIDIA-linux-x86-169.04-pkgl.run
```
When I right click the file (its on my desktop) and run it in the terminal, the script starts but says that I need to run the installer as root. How do I go about using this installer?
Thanks

---

### Post by jleaker01z on 2008-01-30
Download and install envy via the following link.  It will take care of everything for you

[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb)

BTW...if you really want to use the file you have, insert 'sudo' before the command you want to run as root.  IE...sudo sh nvidia-blah-blah.run

---

### Post by oedha on 2008-01-30
i believe you have to shutdown the gdm before you run that script
open console : ctrl+alt+F2
type : sudo /etc/init.d/gdm stop
then : sudo sh /home/username/Dekstop/filename

envy is perfect for nvidia....but i failed last time
~E~

---

### Post by Emmazing on 2008-01-31
> **oedha said:**
> i believe you have to shutdown the gdm before you run that script
open console : ctrl+alt+F2
type : sudo /etc/init.d/gdm stop
then : sudo sh /home/username/Dekstop/filename

envy is perfect for nvidia....but i failed last time
~E~

after I stopped gdm and tried it I got the same error. I then restarted gdm.
Envy is good for nvidia, but the driver I am trying to install isn't listed in the program after I installed it..

---

### Post by oedha on 2008-01-31
is that the correct filename ???
should it be :==> [SIZE=-1][B]NVIDIA-Linux-x86-169.04-pkg.run

~E~
[/B][/SIZE]

---

### Post by Emmazing on 2008-01-31
> **oedha said:**
> is that the correct filename ???
should it be :==> [SIZE=-1][B]NVIDIA-Linux-x86-169.04-pkg.run

~E~
[/B][/SIZE]
 Yup I double checked. there's also a package 2 so I would assume that's why the one I want reads pkg1. I'm thinking of trying the nvidia driver in envy and seeing if it works anyways even though it's not the one I think I need. Worst case scenario is that I have to run sudo dpkg-reconfigure xserver-xorg. I'll see what happens.

---

### Post by oedha on 2008-01-31
the driver is the one with pkg only

so...is this thread solved ???
~E~

---

### Post by Emmazing on 2008-01-31
Yes, I believe it is. Thanks so much! envy worked out just fine.

---

### Post by oedha on 2008-01-31
ok then......
it means...you have to scrool up and click on thread tools....to marked this thread as solved.....
[optional]if you want to thanks to people......click on the star sign on the right bottom corner of a post......

see ya
~E~

---

