---
title: "NVIDIA Drivers."
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-06-04
I just recently downloaded the most current nvidia drivers for my graphics card.  
I try to install them but to no avail.  I continue to get an error that states "Verifying archive integrity...Error in check sums 2860440353 375714808"

I read on the nvnews forums that some people had downloaded the file multiple times and got the same others, while others had the install go perfectly.  I was wondering if there was a work around or anything that I could do to remedy this?

---

### Post by angkor on 2006-06-04
Maybe Tseliot's script will work for you:

[http://www.webalice.it/albertomilone/ubuntu/nvidia/nvidia_scripts.html](http://www.webalice.it/albertomilone/ubuntu/nvidia/nvidia_scripts.html)

---

### Post by bluefrog on 2006-06-04
the easiest way being installing nvidia-glx from ubuntu repository.

then
sudo nvidia-glx-config enable

then

ctrl + alt + return to restart X

James

---

