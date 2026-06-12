---
title: "[SOLVED] tvtime DOESN'T WORK :(("
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by vasiauvi on 2008-03-29
Hi all,
I have a TV tuner Leadtek WinFast TV200 XP RM. From about 3 hours I try to make it work but first of all I don't manage to properly make it work the TVTIME. The same error ocure every time:
```
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/vasia/.tvtime/tvtime.xml"
I/O error : Permission denied

```
What is wrong? I have tried:
[http://ubuntuforums.org/showthread.php?t=255730&highlight=tvtuner]("http://ubuntuforums.org/showthread.php?t=255730&highlight=tvtuner")
[http://ubuntuforums.org/showthread.php?t=256374]("http://ubuntuforums.org/showthread.php?t=256374")
[http://ubuntuforums.org/showthread.php?t=153935]("http://ubuntuforums.org/showthread.php?t=153935")
and other sites.
I don't understand.It's so hard to install a program???
Please give me a feedback!

---

### Post by vasiauvi on 2008-03-30
I have managed to make it work.
I have used this comand:
```
chown -hR root /u 
```

```
chown -hR root .tvtime
```
Changes the owner of /u (here .tvtime) and all the files from .tvtime folder to the owner root.

---

### Post by vasiauvi on 2008-04-05
Can anyone tell me what "tuner" I must use to see all the programs with the TV tuner? My card is 34 because I have :
```
34 -> Leadtek WinFast 2000/ WinFast 2000 XP               [107d:6606,107d:6609,6606:217d,f6ff:fff6]
```
Please tell me what tuner I must use.This is the result of the dmesg | grep bttv :
```
[   98.590722] bttv: driver version 0.9.17 loaded
[   98.590729] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   98.590804] bttv: Bt8xx card found (0).
[   98.590847] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 19, latency: 32, mmio: 0xfa000000
[   98.590862] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[   98.590867] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[   98.590907] bttv0: gpio: en=00000000, out=00000000 in=003ff182 [init]
[   98.591280] bttv0: using tuner=23
[   98.591285] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   99.192898] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>input: PC Speaker as /class/input/input2
[   99.473968] bttv0: i2c: checking for TDA7432 @ 0x8a... <4>nvidia: module license 'NVIDIA' taints kernel.
[  100.506032] bttv0: i2c: checking for TDA9887 @ 0x86... <6>/build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[  101.070263] bttv0: registered device video0
[  101.070313] bttv0: registered device vbi0
[  101.070379] bttv0: registered device radio0
[  101.070403] bttv0: PLL: 28636363 => 35468950 .. ok
[  101.107916] input: bttv IR (card=34) as /class/input/input4
[  155.652000] bttv0: PLL can sleep, using XTAL (28636363).
[  155.804000] bttv0: PLL: 28636363 => 35468950 .. ok
[  491.492000] bttv0: PLL can sleep, using XTAL (28636363).
[  491.896000] bttv0: PLL: 28636363 => 35468950 .. ok
[  511.016000] bttv0: PLL can sleep, using XTAL (28636363).
[  570.476000] bttv0: PLL: 28636363 => 35468950 .. ok
[  689.436000] bttv0: PLL can sleep, using XTAL (28636363).
[  689.528000] bttv0: PLL: 28636363 => 35468950 .. ok
[  770.404000] bttv0: timeout: drop=55 irq=49983/49983, risc=18a2503c, bits: HSYNC
[  770.404000] bttv0: reset, reinitialize
[  770.404000] bttv0: PLL: 28636363 => 35468950 . ok
[  780.080000] bttv0: timeout: drop=108 irq=50119/50119, risc=028d0034, bits: VSYNC HSYNC FBUS FDSR
[  780.080000] bttv0: reset, reinitialize
[  780.080000] bttv0: PLL: 28636363 => 35468950 . ok
[  807.692000] bttv0: timeout: drop=264 irq=50469/50469, risc=18a2503c, bits: VSYNC HSYNC FBUS FDSR
[  807.692000] bttv0: reset, reinitialize
[  807.692000] bttv0: PLL: 28636363 => 35468950 . ok
[ 1373.956000] bttv0: timeout: drop=1278 irq=54866/54866, risc=01d00044, bits: HSYNC FDSR
[ 1373.956000] bttv0: reset, reinitialize
[ 1373.956000] bttv0: PLL: 28636363 => 35468950 . ok

```

---

