---
title: "Computer doesn't bumblebeed at startup"
date: 2013-04-07
forum: Any Other OS
---

### Post by mszegedy on 2013-04-07
PREFIX: My problem was, initially, that optirun wouldn't work at all. However, when I went to get the terminal output for the console, it suddenly started working at all, which I am very happy about. However, I still have a problem.

Hi, I am running Linux Mint 13 Maya 64-bit edition on a Lenovo Thinkpad T430 mid-range (2552?). It is an Optimus laptop, with both Intel integrated graphics and a Nvidia NVS 5400M. I want to install bumblebee, the Nvidia Optimus driver for Linux. I have gone through every possible installation guideline there is to be found on the Internet. I have uninstalled and reinstalled many, many times. However, I simply cannot, for the life of me, get bumblebee to* work (at startup).* Every time, I install and restart, and it just goes like this:

```
$ optirun glxspheres
[   27.293617] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[   27.293728] [ERROR]Could not connect to bumblebee daemon - is it running? 
$ sudo bumblebeed --daemon
$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: NVS 5400M/PCIe/SSE2
166.476225 frames/sec - 175.053080 Mpixels/sec
178.791021 frames/sec - 188.002334 Mpixels/sec
179.028984 frames/sec - 188.252557 Mpixels/sec
178.880776 frames/sec - 188.096714 Mpixels/sec
179.026281 frames/sec - 188.249715 Mpixels/sec
178.860108 frames/sec - 188.074981 Mpixels/sec
179.572828 frames/sec - 188.824420 Mpixels/sec
179.457856 frames/sec - 188.703524 Mpixels/sec
168.109536 frames/sec - 176.770540 Mpixels/sec
165.448997 frames/sec - 173.972929 Mpixels/sec
```

Works great mostly (this is new; until I tested it out for this post, optirun anything just hung and then I had to Ctrl-C it and then I got a stupid error message). I can't optirun Steam, but that's supposed to be hard, so I'll keep working at that. But how do I get the machine to bumblebeed at startup? If it's installed correctly, that should be what is happening anyway. However, every time at login, I still have to bumblebeed. I can't just *make* the command run at startup; that's not how it's supposed to work. What's wrong? (I've purged and reinstalled every relevant package, purged and re-added every relevant repository. I've reinstalled my kernel. I'm pretty sure the problems don't lie in inexpert installation.)

---

