---
title: "compiling error when installing alsa"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by ikevie on 2008-03-25
Hi Fellow Linux user,

I'm new to linux and my sound card the newer hda intel isn't working properly on a dv6500 series and people recomended me to use this guide: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but when i tried to make the newer alsa-driver by using the make command this is what i get:

make -C /lib/modules/2.6.22-14-generic/source SUBDIRS=/home/khvu/Desktop/documents/Downloads/alsa-driver-1.0.16  CPP="gcc -E" CC="gcc" modules
make: *** /lib/modules/2.6.22-14-generic/source: No such file or directory.  Stop.

any suggestion or help would be appreciated. 

Note: ./configure went smoothly.

---

### Post by Oldsoldier2003 on 2008-03-25
> **ikevie said:**
> Hi Fellow Linux user,

I'm new to linux and my sound card the newer hda intel isn't working properly on a dv6500 series and people recomended me to use this guide: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but when i tried to make the newer alsa-driver by using the make command this is what i get:

make -C /lib/modules/2.6.22-14-generic/source SUBDIRS=/home/khvu/Desktop/documents/Downloads/alsa-driver-1.0.16  CPP="gcc -E" CC="gcc" modules
make: *** /lib/modules/2.6.22-14-generic/source: No such file or directory.  Stop.

any suggestion or help would be appreciated. 

Note: ./configure went smoothly.

did you install the headers and source for your kernel?
```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```

---

### Post by ikevie on 2008-03-25
yes, all those packages have been installed. Also I'm running the 7.10 gutsy amd64 version using the  kernel   linux-headers-2.6.22-14-generic 2.6.22-14.52

do i have to manually install that. since aptitute said its already the newest.

Thanks again

---

