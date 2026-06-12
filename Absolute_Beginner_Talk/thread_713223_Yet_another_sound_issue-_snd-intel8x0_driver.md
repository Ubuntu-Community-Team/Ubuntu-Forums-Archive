---
title: "Yet another sound issue- snd-intel8x0 driver"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Sentrosi on 2008-03-02
Hi guys, I recently installed ubuntu and am loving it so far. However, I am having a problem with getting it to recognize my sound card. I followed the instructions in the "Sound Troubleshooting" guide ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)), but it still does not recognize it. 

When I input 
```
aplay -l
``` 
I get
 ```
aplay: device_list:204: no soundcards found...

```

I then input 
```
lspci -v

``` 

which shows 

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: fast devsel, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

```

Through a little research I discovered that the driver for that card is snd-intel8x0. So I put in 
```
sudo modprobe snd-intel8x0

```
which gave me another command prompt, so I assumed that to mean that it worked. I then input
```
sudo nano /etc/modules
``` 
and input "snd-intel8x0" onto the bottom of the list. I then tried to use alsamixer, but got
```
alsamixer: function snd_ctl_open failed for default: No such device

``` 

So I rebooted in tried again, but got the same result. Thank you for reading my (long-winded) post, and thank you in advance for any help you can provide.

---

### Post by Sentrosi on 2008-03-02
No help to be had? :(

---

### Post by superprash2003 on 2008-03-03
try this..hopefully will help..[http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

