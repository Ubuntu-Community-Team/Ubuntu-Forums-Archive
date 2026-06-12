---
title: "Problem with seting up bluetooth headset packages"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-07-12
Hi, I was running through the following How To 
[http://www.ubuntuforums.org/showthread.php?t=75978]("http://www.ubuntuforums.org/showthread.php?t=75978")

I am OK up to the point below....

Quote:
Originally Posted by joker667 View Post
PART 2: Using a Bluetooth Headset - tricky, but also easy when knowing how

1. Load Kernel Module for btsco: "sudo modprobe btsco", checking "dmesg" if it runs. To load it permanently add it to /etc/modules, just write "btsco" at the end of the File
2. Install the following missing (at least on my system) packages needed by the btsco Userspace driver. Easy, because you have apt-get or synaptic:
gcc
gcc-4.0
altgcc
libc6-dev
linux-kernel-headers
libasound2-dev
libao-dev
libbluetooth1-dev
3. Download latest btsco from [http://sourceforge.net/projects/bluetooth-alsa/](http://sourceforge.net/projects/bluetooth-alsa/), unzip to Desktop perhaps
4. Time for the shell!
cd btsco-0.4
./configure
make
sudo make install



First of all, When I run 'sudo modprobe btsco', I get the error

FATAL: Module btsco not found.


I tried ignoring this to try configuring the latest btsco (point 2) and came up with the configure error :

checking bluetooth/bluetooth.h usability... no
checking bluetooth/bluetooth.h presence... no
checking for bluetooth/bluetooth.h... no
configure: error: Bluetooth header files not found

What do I need to do to continue with getting my bluetooth headset working?

Thanks in advance,

Adam.

---

### Post by chele on 2006-08-03
```
sudo modprobe snd_bt_sco
``` loaded the module for me.

---

