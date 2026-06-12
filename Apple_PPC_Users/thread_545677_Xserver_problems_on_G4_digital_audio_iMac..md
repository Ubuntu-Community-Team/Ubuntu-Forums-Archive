---
title: "Xserver problems on G4 digital audio iMac."
date: 2007-09-07
forum: Apple PPC Users
---

### Post by smfenn on 2007-09-07
Hi there,

I've been trying to get my version of fiesty ubuntu installed on my graphite G4 tower (digital audio) which has an ATI rage 128 card in it, but no matter how much i try, i cannot boot into ubuntu properly because xserver won't start up correctly.

I've tried the ATI, VGA, FbDev and some of the other drivers and none of them worked. the FbDev driver gaves me a very garbled incorrectly sized b/w boot into ubuntu. I thought changing the refresh rates might work but it hasn't helped.

[Update] I've just tried using the r128 driver and got some different error messages which might means something to someone.

```
end of block range 0xefffffff <begin 0xf0000000
unable to find a valid frame buffer device
R128(0): failed to open frame buffer device
screen(s) found, but none have a usable configuration.
```

I have already edited the xorg.conf file to make sure the frame rates for the apple studio montior i'm using are correct, but i'm still getting all this stuff about the buffer.

any help would be appreicated.

---

