---
title: "Shane11"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Shane11 on 2006-09-01
Belkin wireless F5D7050B help please.(Using Breezy Badger still). 

I've been trying to install this device on and off for about 4 months!! I can connect to the net via my Speedtouch modem but 
I'd like to get the wireless connection sorted.

I follow a 'how to' that walks me through the initial stage, I untarred the rt2570-1.1.0-b1.
cd into /usr/src cd rt2570-1.1.0-b1/Module
enter sudo make
I get the following error:
make: *** /lib/modules 2.6.12-10-386/build: No such file or directory. Stop.
rt2570.ko failed to build!
make: *** [Module] Error 1.

Does this indicate that there are some libraries missing? 
I've used apt-get update and I'm told that the system is up to date.

When I tried:
sudo apt-get install build-essential 
I got a page full of errors ie

W: Couldn't stat source package list cdrom ://Ubuntu 5.10 _Breezy Badger - Relea se i386 )20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fB reezy%20Badger%5f%20-%20i386%20(20051012)_dists_breezy_main_binary_i38 6_Packages)-stat (2 No such file or directory)

This is followed by about 15 similar errors.

I'm slowly going nuts here so any assistance would be appreciated. I've obviously missed something simple and fundamental.

Thanks in advance.

---

### Post by meborc on 2006-09-01
maybe this thread helps you... or at least you can contact the person that already has similar card and got it working... [http://ubuntuforums.org/showthread.php?t=246994](http://ubuntuforums.org/showthread.php?t=246994)

BUT i strongly advise you to get dapper as your primary OS... there are a lot of improvements specially in wireless area (ndiswrapper) :rolleyes:

---

### Post by TFX360 on 2006-09-01
> **meborc said:**
> maybe this thread helps you... or at least you can contact the person that already has similar card and got it working... [http://ubuntuforums.org/showthread.php?t=246994](http://ubuntuforums.org/showthread.php?t=246994)

BUT i strongly advise you to get dapper as your primary OS... there are a lot of improvements specially in wireless area (ndiswrapper) :rolleyes:

Correct me if I'm wrong but rt25xx is natively supported in Ubuntu Dapper Drake.

Swoong!

---

### Post by TFX360 on 2006-09-01
As far as I know rt25xx isn't supported by ndiswrapper. It gives IOCTLSO erorrs or something like that!

---

