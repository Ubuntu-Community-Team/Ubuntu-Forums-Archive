---
title: "ASUS G75 Screen Resolution."
date: 2012-06-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by vavewave on 2012-06-10
So I installed Ubuntu 12.04 on my ASUS G75, but the resolution is kind of wack. It's stuck at a lower resolution than intended (it's supposed to be 1920x10800). From what I gathered, I guess it's because it won't recognize the graphics card, which is the nVidia GeForce 660M GTX. Can I solve this problem in any way?

---

### Post by igorrafaeldesousa on 2012-06-10
In my G75 I did this: first installed bumblebee ( [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) ) then use the "Additional drivers" application (jockey) to install the nvidia driver then uninstall bumblebee via apt-get and after rebooting it worked.

Bear in  mind that this was totally empirical and that if I had put some effort I probably wouldn't have to have uninstalled bumblebee.

---

### Post by Sophont on 2012-06-18
Bumblebee helps you you with Optimus card switching. Using the intel graphics for low power regular office apps and then switch to dedicated 3D accelerated NVidia card for Games and other demanding stuff. It's not needed for getting the resolution and full 3D acc on this Lptop.

The most recent NVidia (proprietary) drivers handles the 660M on the G75 just fine. Correct resolution and I've got Left4Dead on Steam via Wine running right away - no tweaks needed.

I've got everything working on my G75 almost out-of-the-box - except the media keys (volume, play, stop, etc..).

Even Hibernate seems working well.

---

### Post by Sophont on 2012-09-23
Addendum. Recent Kernel update solved the problem with the Fn/media keys.

---

