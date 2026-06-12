---
title: "Cisco VPN Client and 7.04"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by BigFlatBrook on 2007-05-21
To compile the Cisco VPN client for my laptop (running ubuntu 7.04),  I need kernel source and a compiler that matches the one that the kernel was compiled with.

I downloaded the 7.04 iso image and installed from that. 

Can anyone give a hand here?  Thanks!

---

### Post by Happy_Man on 2007-05-21
Great, so you want to compile a program? Easy!

```
sudo apt-get install build-essential
```

Will give you all the tools you need to compile....

---

### Post by BigFlatBrook on 2007-05-21
Much appreciated.  The errors I get (after sudo apt-get install build-essential) are

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/jrw/software/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/jrw/software/vpnclient/linuxcniapi.o
/home/jrw/software/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/jrw/software/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/jrw/software/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

 In fact, there is no config.h in /usr/src/linux-headers-2.6.20-15-generic/include/linux, which is where I think it's looking for that file.

I'm coming to the conclusion that the cisco vpn  client is not compatible with 7.04, maybe because of the version of the kernel it uses.  

Do I have that right?

Thanks!

---

### Post by Happy_Man on 2007-05-21
Could you give us a download link? I'd like to try this for myself...

---

### Post by BigFlatBrook on 2007-05-22
Ok, back to trying to get this to work.  But as far as I can tell, the Cisco VPN client is not generally available -- only to cisco clients it seems.   At least, I can't find a public place to download it.

In any case, I've migrated over to trying to get openvpn vpnc to work.

I do greatly appreciate your response, and sorry to take so long to reply.

---

### Post by hise0001 on 2007-05-23
the cisco client source references several include files that don't exist under that name.  The following link has a patch that will update the source to reference the correct includes.  I believe it only works with the 4.8 version of the cisco client.

[http://tuxx-home.at/archives/2007/04/10/T15_55_43/](http://tuxx-home.at/archives/2007/04/10/T15_55_43/)

---

### Post by David Valentine on 2007-05-24
Thanks!  That patch worked for me, though you're right--only on version 4.8.  Now that it's installed, time to see if I can get it working...

---

