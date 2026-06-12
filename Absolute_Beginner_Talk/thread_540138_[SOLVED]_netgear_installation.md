---
title: "[SOLVED] netgear installation"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by jatiesch on 2007-09-01
hi i am a linux beginner and got stuck early on....

My wifi card is Netgear WG311v3...
when i use ndiswrapper graphical interface for installing my wireless network card i get a window of no hardware found..

however on using command line interface i am able to install the driver...
on ndiswrapper-l  i get-
> wg311v3 : driver installed
        device (11AB:1FAA) present
which means it identifies the card...
but on ifconfig/iwconfig ino wlan0 is shown...

Plz help as i cannot proceed without internet connection,,,,,,

---

### Post by jatiesch on 2007-09-01
hi...:(
problem is i cannot proceed with installing other programs without net....
waiting eagerly for ur responce...

---

### Post by peebly on 2007-09-01
Hello

Did you reboot Linux, I had to do this to get my card going.

---

### Post by jatiesch on 2007-09-01
i am stuck on this for almost 4-5 days now....
so no question of reboot...

---

### Post by wormser on 2007-09-01
I found a nice [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3").

---

### Post by jatiesch on 2007-09-01
hi thanxs for ur post but,
n i also went through a similar guide....
but after* sudo modprobe ndiswrapper *
when i run *iwconfig * i get no wlan0..

i have AMD64 system...if that may be a source of the problem...

---

### Post by wormser on 2007-09-01
> **jatiesch said:**
> hi thanxs for ur post but,
n i also went through a similar guide....
but after* sudo modprobe ndiswrapper *
when i run *iwconfig * i get no wlan0..

i have AMD64 system...if that may be a source of the problem...
Maybe that is the problem?... It is the problem.  You need to post details like that if you are asking for help.  If you search the forum you will find solutions like this [one]("http://ubuntuforums.org/showthread.php?t=320111&highlight=wg311v3").

---

### Post by zevero on 2007-10-28
I tried with gutsy and feisty both in amd64, but it didnt work. It seems that it should work see [http://ubuntuforums.org/showthread.php?p=1895897](http://ubuntuforums.org/showthread.php?p=1895897) but I also reported that it does not work here (entry from zevero)
Would be happy if you can compare my dmesg - output with yours!

---

### Post by kvonb on 2007-10-28
You might have to blacklist one or many of the other Ubuntu drivers in order to use the NDISWrapper supplied driver properly.

I have no idea which one, you will have to find out what chipset your wireless card uses and blacklist it.

As a quick test, you could move ALL the Ubuntu wireless drivers out of

/lib/modules/2.6.2(your kernel #)-generic/kernel/ubuntu/wireless/

I would simply move that whole folder to another location, reboot and see if the ndiswrapper driver works, and either move it back if it doesn't, or just leave it if all is well.

This guide might help, it's for wg111 usb adapters, but should be similar.

[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)

See the last few pages for updates.

---

### Post by jatiesch on 2008-01-20
thanks wormser...problem solved :)

---

