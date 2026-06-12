---
title: "Zenbook UX31A - doesn't recognize second display on boot / wakeup"
date: 2013-11-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by asiandub on 2013-11-15
I use 12.04.3 (64 bit) on an Asus Zenbook Prime with an Intel hd 3000 video card:
```
    uname -a
    Linux maroubra 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:28:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```
```
    sudo lspci -v
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Zenbook Prime UX31A
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

```

Problem is that after boot and wake up the **second display won't always be recognized**. The computer boots / wakes up just fine, but after login / password screen the second display will either work or not. 
[B]
If it works[/B] I get the following output on xrandr:
```
    xrandr
    Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 32767 x 32767
    eDP1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 282mm x 165mm
       1920x1080      60.0*+   59.9     40.0  
       1680x1050      60.0     59.9  
       1600x1024      60.2  
       1400x1050      60.0  
       1280x1024      60.0  
       1440x900       59.9  
       1280x960       60.0  
       1360x768       59.8     60.0  
       1152x864       60.0  
       1024x768       60.0  
       800x600        60.3     56.2  
       640x480        59.9  
    VGA1 disconnected (normal left inverted right x axis y axis)
    HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
       1920x1080      60.0*+   50.0  
       1680x1050      59.9  
       1600x900       60.0  
       1280x1024      75.0     60.0  
       1440x900       59.9  
       1280x800       59.9  
       1152x864       75.0  
       1280x720       50.0     60.0  
       1024x768       75.1     70.1     60.0  
       832x624        74.6  
       800x600        72.2     75.0     60.3     56.2  
       720x576        50.0  
       720x480        59.9  
       640x480        72.8     75.0     66.7     60.0  
       720x400        70.1  
    DP1 disconnected (normal left inverted right x axis y axis)



```
**It it's not working **xrandr looks like this:
```
    xrandr
    Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
    eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 282mm x 165mm
       1920x1080      60.0*+   59.9     40.0  
       1680x1050      60.0     59.9  
       1600x1024      60.2  
       1400x1050      60.0  
       1280x1024      60.0  
       1440x900       59.9  
       1280x960       60.0  
       1360x768       59.8     60.0  
       1152x864       60.0  
       1024x768       60.0  
       800x600        60.3     56.2  
       640x480        59.9  
    VGA1 disconnected (normal left inverted right x axis y axis)
    HDMI1 disconnected (normal left inverted right x axis y axis)
    DP1 disconnected (normal left inverted right x axis y axis)



```

I can 'fix' this by re-connecting the HDMI cable which will usually make Ubuntu recognize the second screen (might need a few attempts though). This not only is very annoying but also starts to wear out the (mini-) HDMI connection on my laptop (Did that about a million times in the last year).

I should add that I'm observing this behavior over quite a few distros (Linux Mint, Ubuntu 12.04 / 12.10 / 13.10) and kernels, pretty much since I bought the machine. I've never paid much attention to setting up dual displays so far - which makes it fairly vanilla in this regards. 

Intel provides Linux drivers for hd 3000, but they don't support 12.04 any more, and most information I find seems to indicate that special drivers shouldn't be required.

ps: does it work on Windows? I don't know ;)

---

