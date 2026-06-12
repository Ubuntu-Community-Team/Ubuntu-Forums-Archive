---
title: "MPlayer doesn't work"
date: 2005-06-12
forum: Apple PPC Users
---

### Post by jhk on 2005-06-12
Hello!  I've recently got a new eMac after running Arch Linux on an x86, and while Mac Os X is spiffy and all that, I still got an ich to run linux, so I installed Ubuntu on it.  It works fine- I'm running Enlightenment e17 now and it's really nifty.

My problem is that I can't get mPlayer to work!  It's my favorite media player- I use it fine in Mac os X- but for some reason, when I install it using apt, the binary files don't show up in /usr/bin like they're supposed to, and there's no way to actually run mplayer/gmplayer.  This applies for both versions available on apt.  So I tried compiling it, but when I enable the gui make always hangs on 
/usr/include/sys/uio.h:40: error: invalid vector type for attribute 'vector_size'
/usr/include/sys/uio.h:50: error: invalid vector type for attribute 'vector_size'

when it's working in vo_x11.o inside libvo. I have no idea what the problem is and google doesn't help.

Can anyone help me either install the package or compile it?

Thanks!

---

### Post by pvz on 2005-06-12
Or you could try and search this forum...
Try to compile it with --disable-altivec and see if that works for you.
You can give vlc-player a try as well, you might be in for a pleasant surprise.

---

