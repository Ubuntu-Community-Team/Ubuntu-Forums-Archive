---
title: "still cannot get online."
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by nehc on 2006-12-23
hello,
since i have no answer in my first post  :( [http://www.ubuntuforums.org/showthread.php?t=322244&highlight=usb+wireless](http://www.ubuntuforums.org/showthread.php?t=322244&highlight=usb+wireless)
i was looking and trying different method to get online like this one
[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588) (i use edgy eft), but i don't think it will work because it says that after i put blacklist rt2570, there will be no wireless wlan0 but i still have it.
i put this too 
nehc@NEHC:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
wlan0     IEEE 802.11g  ESSID:"ColdPot"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
sit0      no wireless extensions.

my questions are: do i have the drivers? if yes why i cannot get online?
also, i cannot find the driver from my usb installation cd. so i downloaded it (see my desktop from the snapshot i took from my first post) and put in the .sys and .inf in /home/username/ and install it following the howto but no work.
these are all the files in the usb installation cd
[http://img145.imageshack.us/my.php?image=cdmk2.gif](http://img145.imageshack.us/my.php?image=cdmk2.gif)

pd: in the howto, there is one part where i have to extract the ndiswrapper file (i got error)
$tar zxvf ndiswrapper-version.tar.gz
what zxvf means? the name of my file is ndiswrapper-1.8.tar.gz and it was in the desktop
i wrote $tar zxvf ndiswrapper-1.8.tar.gz and got error too.

---

### Post by dbbolton on 2006-12-23
so, can you get online with a wired connection ?


btw, if you start the same thread over, the mods will delete it. i know it's frustrating, but sometimes it helps to be patient :)

---

### Post by c.dric on 2006-12-23
> **nehc said:**
> pd: in the howto, there is one part where i have to extract the ndiswrapper file (i got error)
$tar zxvf ndiswrapper-version.tar.gz
what zxvf means? the name of my file is ndiswrapper-1.8.tar.gz and it was in the desktop
i wrote $tar zxvf ndiswrapper-1.8.tar.gz and got error too.

hey,

zxvf are options for the command tar.
- x for extract
- v for verbose 
- z tells tar to filter the archive through gzip before untarring.
- f tells tar to use the files that follows. ndiswrapper-1.8.tar.gz in this case.

if ndiswrapper-1.8.tar.gz is on your desktop, you should go there 

```
cd ~/Desktop
```

and continue from there

```
tar zxvf ndiswrapper-1.8.tar.gz
cd ndiswrapper-1.8

make distclean
make
sudo make install
```

if you get that far without error message, you have ndiswrapper installed properly and you can try to install the driver.

i hope this will help :)

---

### Post by NESFreak on 2006-12-23
according to your post iwconfig states that your wlancard isn't called "wlan0" but "wmaster0" mine for instance is called "ra0" and it works. so it's just another name for the same.
iwconfig states that there aren't any problems.

NESFreak

---

