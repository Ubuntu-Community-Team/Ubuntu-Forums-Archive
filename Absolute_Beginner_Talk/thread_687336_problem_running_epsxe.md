---
title: "problem running epsxe"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by KevNice on 2008-02-04
I checked some of the other threads, but didnt see anyone else with this particular problem...

I set up epsxe, found the BIOS and set up that too, got an ISO file. When I try to run the ISO follow here is the error I get:

```
 epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH7001.bin]. 
 * Loading ISO Format [NRG2336] ok
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
Gdk-ERROR **: GLXUnsupportedPrivateRequest
  serial 40 error_code 162 request_code 143 minor_code 16
kevin@kevin-laptop:~$ 

```


any thoughts?

---

### Post by kshane on 2008-02-04
> **KevNice said:**
> I checked some of the other threads, but didnt see anyone else with this particular problem...

I set up epsxe, found the BIOS and set up that too, got an ISO file. When I try to run the ISO follow here is the error I get:

```
 epsxe
 * Running ePSXe emulator version 1.6.0. 
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//SCPH7001.bin]. 
 * Loading ISO Format [NRG2336] ok
 * NTSC cdrom detected. 
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8] 
[B]Gdk-ERROR **: GLXUnsupportedPrivateRequest
  serial 40 error_code 162 request_code 143 minor_code 16[/B]
kevin@kevin-laptop:~$ 

```


any thoughts?

It appears to me that you have a video driver problem....  Are you running the proprietary drivers?

Kevin

---

### Post by jan quark on 2008-02-04
yes I also guess it is a graphic issue

run and post
```

lspci
```

---

### Post by KevNice on 2008-02-04
It was indeed the video driver, I changed it and now I dont get the error.

However, when epsxe loads up, all I get is a black screen and no activity (the FPS guage stays at zero)

I took a screenshot just in case:

[http://www.kevnice.com/images/Screenshot.png](http://www.kevnice.com/images/Screenshot.png)


ETA: the game I am trying to run is final fantasy 7, I heard that maybe the config needs to be different?

---

### Post by KevNice on 2008-02-05
nevermind.. got it working now.

Turns out it was a bad ISO. And surprisingly, epsxe runs .mdf files that arent mounted!

---

