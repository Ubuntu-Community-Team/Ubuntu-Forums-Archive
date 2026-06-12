---
title: "Bluetooth Problem on Asus K55VD"
date: 2012-12-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by utack on 2012-12-24
Hello,

I have sort of a special problem with the bluetooth in my new notebook, let me explain.

I am not completely sure whether or not a bluetooth module is even installed!

Cons:


[LIST]
[*]The notebook is a certain version built for the local store and they say no bluetooth..however they had wrong data on their websites before
[*]lshw and lsusb as well as lspci do not see a bluetooth module
[/LIST]

Pros:


[LIST]
[*]dmidecode sees a bluetooth module
[*]the kernel modul "bluetooth" is loaded on boot and the icon shows up
[*]Asus says it is an option for this notebook and they offer drivers for windows on the website
[*]dmesg starts up bluetooth on booting..but does not mention any hardware specifically
[/LIST]
However if bluetooth is installed it would be the AR3011 from Atheros.


Can someone tell me how to find out if there is even a bluetooth module installed and if yes: how can I get it working on my Ubuntu 12.10?


Thank you very much!
Jakob

---

### Post by utack on 2012-12-26
Hello,

after a while I got motivated enough to dig out the hdd that came with the notebook and Windows8 still on it.

There is no bluetooth module built into this notebook!

Please close the thread...


Thank you!

---

### Post by kenweill on 2013-01-01
We have the same hardware.
Bluetooth is detected on both Windows 7 and Linux Mint 14 (based on Ubuntu 12.10). I just haven't tested it if it works or not in LM. But it won't work on W7. It's installed but can't detect my bluetooth on mobile phone.

Tested on Ubuntu 12.10 64bit. Bluetooth works. My Samsung Galaxy SIII was able to connect to my laptop, ASUS K55VD, bluetooth.

The only problem I have is NVIDIA 610M is not detected on Linux but instead, installed an Intel driver for the video.

I don't know how their video works but on Windows 7, installing NVIDIA drivers won't work unless Intel video driver is installed first before installing the NVIDIA driver.

On LM14, only Intel video is detected and installed. No NVIDIA is detected or installed.

---

