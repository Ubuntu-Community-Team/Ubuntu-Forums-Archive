---
title: "Don't understand why xawtv won't launch"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-01-28
I installed xawtv and streamer with aptitude, and it adds itself to "sound and video" but when  I click it, it does nothing. Thanks for any help/suggestions.

---

### Post by crispy_420 on 2007-01-30
Try to launch from command line and it will show errors. 

My guess is a video driver issue.

Post you errors here to get some help. I know no tv app would launch for me when I had my ATI (fglrx) drivers setup wrong.

---

### Post by Ripfox on 2007-01-30
This is xawtv-3.95, running on Linux/i686 (2.6.17-10-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

I am running Beryl smoothly, so my Nvidia driver is, I assume, set up right.

---

### Post by crispy_420 on 2007-01-31
You know I had the same issue when I installed "eye candy" too. The way I fixed it was going back to a 2D desktop, no more eye candy. I'm no expert but it looks like with eye candy installed, tvtime/xawtv can't render an image.

If I find anything to help I'll post back.

---

### Post by Ripfox on 2007-01-31
TvTime works fine though...

---

