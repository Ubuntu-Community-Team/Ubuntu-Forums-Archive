---
title: "Still no OpenGL"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by CompakDark on 2006-02-12
My brother told me to install Ubuntu and I agreed, I like Ubuntu, but I'm also a big fan of the game Enemy Territory, which I know can be ran on Linux if I could get my video drivers to install. 

My brother has been helping me and he's stumped. He uses an ATI Radeon 9600Pro and this guide worked fine for him, but when I use it for my 9200LE, it still will not work. 

Could someone give me some advice or is my card not supported?

**lspci | grep ATI** gives this:

```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)

```
[B]
dmesg | grep fglrx[/B] :

```
[4294722.404000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294722.407000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294722.407000] [fglrx] module loaded - fglrx 8.22.5 [Feb  7 2006] on minor 0
[4294722.980000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294722.980000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294722.980000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294722.980000] [fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
[4294722.980000] [fglrx:firegl_unlock] *ERROR* Process 6270 using kernel context 0

```

and **fglrxinfo** gives this:

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

---

