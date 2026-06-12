---
title: "Audio device not detected"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Soap_Dude on 2006-07-14
My onboard ESS1869 sound works fine in Windows XP, but Ubuntu is not detecting/configuring it. I can't do any audio stuff on Ubuntu. I've alread read some archaic HOWTO that told me to get the DMA channels and I/O ports, as well as recompile the kernel. 

Since I'm a n00b, does anybody have any other suggestions as to how I might configure the device? 

hmmm... I'm wondering if the ESS1869 chip is supported. After all, it's quite old.

Any help will be appreciated.

---

### Post by Wyrm_1972 on 2006-07-14
[https://help.ubuntu.com/community/forum/hardware/OldSoundCard](https://help.ubuntu.com/community/forum/hardware/OldSoundCard)

Sounds like an old ISA card. Not autodetected by Ubuntu.

Worst comes to worst you can do what I did and walk into your local computer shop and buy the cheapest PCI card they have.

Essentially in terminal type
```
modprobe snd-es18xx
``` 
then
```
alsamixer
```

to see if this has done anything. If it has then you can make the change permanent by adding...

snd-es18xx

to /etc/modules
```
sudo gedit /etc/modules
```

---

### Post by Soap_Dude on 2006-07-15
Hi, I did some stuff according to [https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems") and it worked. 

When I run **lspci -v**, nothing in the list shows a sound chip. I am still confused as to why the physical device is not there. By the way, terminal doesn't recognize **lspnp**

But I was lucky, the settings on my ESS1869 matched exactly the example: 
```
#modprobe example
$ sudo modprobe snd_es18xx isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=5 irq=5 fm_port=0x388
```

So I run the next few lines of command, and all my audio worked!

---

