---
title: "wireless card (Broadcom 43225 802.11b/g/n) is not recognized on Backtrack 5 R1"
date: 2012-02-19
forum: Any Other OS
---

### Post by Pedro Neves on 2012-02-19
Hello everyone, i'm new in linux in general. I had recently reinstalled my 2 pc and i decided to install ubuntu in one of them and backtrack 5 r1 on another. The problem is that, on my laptop (hp pavillion dv6 2160ep) which has Broadcom 43225 802.11b/g/n wireless adapter i had installed Backtrack and it cannot recognise the wireless card. can anyone help me?

my kind regards to everyone

---

### Post by uRock on 2012-02-19
Welcome to the forums,

I have moved the thread to "*Other OS/Distro Talk*"

---

### Post by Dlambert on 2012-02-19
It's probably missing the driver: [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

But if you're running BT in live mode, this could be tricky.

---

### Post by Pedro Neves on 2012-02-20
> **Dlambert said:**
> It's probably missing the driver: [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

But if you're running BT in live mode, this could be tricky.



I've burned the image to a Dvd and i installed side by side with Windows 7. As i said i'm new in linux. Probably i screw everything.

---

### Post by Pedro Neves on 2012-02-20
> **Dlambert said:**
> It's probably missing the driver: [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

But if you're running BT in live mode, this could be tricky.



I'm currently tryin to install the packages but when i prompt the command make i have the output:



root@bt:~/Desktop/hybrid_wl# make clean
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-source-2.6.39.4'
CFG80211 API is prefered for this kernel version
/root/Desktop/hybrid_wl/Makefile:80: Neither CFG80211 nor Wireless Extension is enabled in kernel
  CLEAN   /root/Desktop/hybrid_wl/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-source-2.6.39.4'

root@bt:~/Desktop/hybrid_wl# make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-source-2.6.39.4'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.39.4/Module.symvers
           is missing; modules will have no dependencies and modversions.

CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /root/Desktop/hybrid_wl/built-in.o
  CC [M]  /root/Desktop/hybrid_wl/src/shared/linux_osl.o
  CC [M]  /root/Desktop/hybrid_wl/src/wl/sys/wl_linux.o
  CC [M]  /root/Desktop/hybrid_wl/src/wl/sys/wl_iw.o
  CC [M]  /root/Desktop/hybrid_wl/src/wl/sys/wl_cfg80211.o
/root/Desktop/hybrid_wl/src/wl/sys/wl_cfg80211.c: In function &#8216;wl_inform_single_bss&#8217;:
/root/Desktop/hybrid_wl/src/wl/sys/wl_cfg80211.c:1817: error: too few arguments to function &#8216;ieee80211_channel_to_frequency&#8217;
make[2]: *** [/root/Desktop/hybrid_wl/src/wl/sys/wl_cfg80211.o] Error 1
make[1]: *** [_module_/root/Desktop/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.39.4'
make: *** [all] Error 2

-> after this i tried to reinstall the packages that instruction manual specifies: 


root@bt:~/Desktop/hybrid_wl# apt-get install build-essential linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-generic has no installation candidate


-> The first one was nice :D
-> on the second one i had the following output :(:

root@bt:~/Desktop/hybrid_wl# apt-get build-dep linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list



Can you tell me why do i get the error in the make file? :(

---

### Post by haqking on 2012-02-20
broadcom suck in Linux generally speaking (my opinion of course)

[http://blog.xuite.net/fecbob.fecstar/BackTrack/54839501-Broadcom+wireless](http://blog.xuite.net/fecbob.fecstar/BackTrack/54839501-Broadcom+wireless)

Anyways no offence, as you said you are new to linux so why are you using Backtrack anyways ?

You know it is not a typical desktop distro for everyday use right ?

I mean it can be used that way but it is a suite of sec auditing tools built around a specialist kernel compiled for purpose.

Plus if you want to use the wireless auditing tools under BT with that card such as aircrack or similar then they are not the best (and those tools are not supported here either incase any support questions arise about it ;-)

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)

and your errors are to do with sources, Backtrack uses its own repos specific to its tools and kernel, though you can add more i am pretty sure you will end up borking your system if you dont know what you are doing.



Enjoy

---

### Post by Pedro Neves on 2012-02-20
> **haqking said:**
> broadcom suck in Linux generally speaking (my opinion of course)

[http://blog.xuite.net/fecbob.fecstar/BackTrack/54839501-Broadcom+wireless](http://blog.xuite.net/fecbob.fecstar/BackTrack/54839501-Broadcom+wireless)

Anyways no offence, as you said you are new to linux so why are you using Backtrack anyways ?

You know it is not a typical desktop distro for everyday use right ?

I mean it can be used that way but it is a suite of sec auditing tools built around a specialist kernel compiled for purpose.

Plus if you want to use the wireless auditing tools under BT with that card such as aircrack or similar then they are not the best (and those tools are not supported here either incase any support questions arise about it ;-)

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers)

and your errors are to do with sources, Backtrack uses its own repos specific to its tools and kernel, though you can add more i am pretty sure you will end up borking your system if you dont know what you are doing.



Enjoy



Im using backtrack because i have need to get some more experience in net auditoring. But thanks for the opinion ;)

---

### Post by haqking on 2012-02-20
> **Pedro Neves said:**
> Im using backtrack because i have need to get some more experience in net auditoring. But thanks for the opinion ;)

I would learn Linux in general first otherwise nothing in BT or sec auditing will make any sense

BT requires a certain level of Linux knowledge to be used and so does the security tools that are built into it.

BT is not the best distro to learn Linux, and using BT without a knowledge in Linux will leave a borked system and a headache ;-)

Just my 2 cents of course and long time BT user.

Peace

---

### Post by Pedro Neves on 2012-02-20
> **haqking said:**
> I would learn Linux in general first otherwise nothing in BT or sec auditing will make any sense

BT requires a certain level of Linux knowledge to be used and so does the security tools that are built into it.

BT is not the best distro to learn Linux, and using BT without a knowledge in Linux will leave a borked system and a headache ;-)

Just my 2 cents of course and long time BT user.

Peace


So do u suggest me to try on UBUNTU first? for example? I've some network knowlodge (well a little of course) thats why this was one of my choices.

---

### Post by haqking on 2012-02-20
> **Pedro Neves said:**
> So do u suggest me to try on UBUNTU first? for example? I've some network knowlodge (well a little of course) thats why this was one of my choices.

try what ?

I mean you said you new to Linux, by your posts above and not recognising the errors and such i would agree that you are (all due respect of course)

So i would recommend getting a more grounded knowledge base in Linux itself and especially in the use of the terminal before trying to learn how to use BT.

I am not saying you cant use BT , you can do what you like, but it will be a ongoing cause of frustration and things not working if you dont have a better grounding in general Linux skills.

But use what works for you or you can make work ;-)

especially compiling from source and setting up wireless and other devices as BT is only set to work with specific chipsets out of the box, others take some tweaking if work at all

And you are better off in the BT forums for BT related questions

you can get to them here [http://www.backtrack-linux.org/wiki/index.php/Main_Page](http://www.backtrack-linux.org/wiki/index.php/Main_Page)

Peace

---

### Post by Pedro Neves on 2012-02-20
> **haqking said:**
> try what ?

I mean you said you new to Linux, by your posts above and not recognising the errors and such i would agree that you are (all due respect of course)

So i would recommend getting a more grounded knowledge base in Linux itself and especially in the use of the terminal before trying to learn how to use BT.

I am not saying you cant use BT , you can do what you like, but it will be a ongoing cause of frustration and things not working if you dont have a better grounding in general Linux skills.

But use what works for you or you can make work ;-)

especially compiling from source and setting up wireless and other devices as BT is only set to work with specific chipsets out of the box, others take some tweaking if work at all

And you are better off in the BT forums for BT related questions

you can get to them here [http://www.backtrack-linux.org/wiki/index.php/Main_Page](http://www.backtrack-linux.org/wiki/index.php/Main_Page)

Peace


Ok i think u're right perhaps it is a big step. ;) i'll explore more about linux in general. Thanks for your opinion ;)

---

### Post by haqking on 2012-02-20
> **Pedro Neves said:**
> Ok i think u're right perhaps it is a big step. ;) i'll explore more about linux in general. Thanks for your opinion ;)

you are welcome.

If you choose to still go with BT right now or when you do then stick it in a virtual machine, you can download a VM image if you want.

It wont trash your system then ;-)

Obviously you cant use built in hardware such as internal wifi, but you can use a USB wifi device that is supported like the excellent Alfa AWUS036NH which is supported out of the box in BT and supported replay/injection and other such activities using wireless tools.

Anyways like i said those activities are not supported here but now you have more options.

Enjoy and peace

---

### Post by Pedro Neves on 2012-02-20
:)

Thanks a lot

U know, windows close up our eyes. 

my regards

---

