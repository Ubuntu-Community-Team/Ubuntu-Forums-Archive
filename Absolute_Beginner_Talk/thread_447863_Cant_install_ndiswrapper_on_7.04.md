---
title: "Cant install ndiswrapper on 7.04"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by lochbroom on 2007-05-18
After installing this new version of Ubuntu, I just cant get ndiswrapper installed. I have read many posts about it and read info on various site but I still cant get it.

I have tried both versions 1.43 and 1.44. I know I'm doing something wrong. Can someone give me the the step by step instructions.  Thank you for the help....John

---

### Post by theicyj on 2007-05-18
Easy method: 

Try [Automatix]("http://www.getautomatix.com/").

Ubuntu 7.04 (Feisty i386)
[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb) 

Ubuntu 7.04 (Feisty AMD64)
[http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/automatix2_1.1-4.4-7.04feisty_amd64.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/automatix2_1.1-4.4-7.04feisty_amd64.deb)

If that doesn't work, then I am not sure.  My wireless worked out-of-the-box using a D-Link G630 in my laptop and a Belkin PCI card in my desktop (both atheros based).

---

### Post by lochbroom on 2007-05-18
automatix wont work as it has the dependency problem re Python 2.4. I wonder is there any way around that?

---

### Post by chamberlain2006 on 2007-05-18
Please don't use Automatix.  Follow [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_manually_update_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_manually_update_Ubuntu) method, and I can help if need be, but PLEASE don't use Automatix.  Automatix is known to screw your system, and will haunt you later.

---

### Post by chamberlain2006 on 2007-05-18
Whoops, the proper link is [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

---

### Post by lochbroom on 2007-05-19
Thanks very much for your help but still no luck. Here is some more info

When I installed 7.04 on a 40G drive which had XP on it before, I just did an Fdisk and left the whole disk go to Ubuntu...the install went flawless twice in fact.

This is a sequence I just performed which may help to determine where I'm going wrong....

I  have Ndiswrapper 1.42rc2 in it own directory.

from the root@spare(drive name) I can CD to dir ndiswrapper-1.42.rc2

then I do 'make install'

and it seems to do it's job as it starts to install, it appears to be putting driver files on but about 20 lines down it starts printing error lines and it goes through another 20 lines or so like this and it ends up at original but without ndiswrapper getting installed.

I have done the same with version 1.43 and 1.44.

---

### Post by Bachstelze on 2007-05-19
You musn't do make install right away. make install just installs the program but before, you need to configure and build it. First, make sure you have all the tools required to build it :

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then do this :

```
sudo make uninstall
make
sudo make install
```

you're there :)

---

### Post by lochbroom on 2007-05-19
Thanks very much...now it works. Step 1 was what I needed. I still cant get the wireless to work but I'll figure that out but at least I have the driver installed for my D-link DWL-G122.

Thanks...John

---

### Post by haw730 on 2007-05-19
I am having a similar problem with installing ndiswrapper. I am new to linux and had the similar problem of errors that lochbroom had. I think my kernel is outdated. it shows that the build is 2.62-15 on the boot screen. for ndiswrapper the readme says it needs 2.6.6 or 2.4.26 to work. Can someone point me in the right direction and give me a detailed way to install the kernel? It would be much appreciated.

---

### Post by Bachstelze on 2007-05-19
To know your kernel version :

```
uname -r
```

My guess is that you made a mistake and you have in fact a 2.6.20 kernel, which is perfectly compatible with ndiswrapper.

---

### Post by haw730 on 2007-05-19
Thanks! My only question now is how to get it to work. After going through the commands of extracting the tar and trying the codes that you posted, it wont work. I think it might be an issue with being in the right directory. 
 I type cd /home/andrew/ndiswrapper-1.44 then I try the codes and it brings up errors and warnings.

---

### Post by Bachstelze on 2007-05-19
It definitely should work... What errors do you get ?

---

### Post by haw730 on 2007-05-19
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory

loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/andrew/ndiswrapper-1.44/utils'
make: *** [install] Error 2

Those are some of the errors

---

### Post by Bachstelze on 2007-05-19
Did you install your kernel headers and build-essential as I pointed earlier ?

---

### Post by haw730 on 2007-05-19
yeah when I ran that command it said that there was no file found. Here is what happened:
root@baygaw101:~/ndiswrapper-1.44# sudo apt-get install build-essential linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

---

