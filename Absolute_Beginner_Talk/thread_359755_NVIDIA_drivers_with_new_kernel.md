---
title: "NVIDIA drivers with new kernel"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Nightmist on 2007-02-12
Hello,

I updated this morning, and apparently there was a new kernel image in there. I just got home from work, was tired, and didn't look at what I was updating :)

Anyway, when I try to start the new kernel KDE wont start. When I try 'startx' X.org returns an error with the nvidia display driver and says...

Could not open /lib/modules/2-6.17-11-generic/volatile/nvidia.ko

Xorg.conf seems to be untouched by the update (when looking at the date it was last modified).

Any help would be welcome.

---

### Post by Bachstelze on 2007-02-12
sudo apt-get install linux-restricted-modules-$(uname -r)

alternatively, you can also instal linux-restricted-modules-generic to make sure your nvidia driver will always stay up to date.

---

### Post by Nightmist on 2007-02-12
> **HymnToLife said:**
> sudo apt-get install linux-restricted-modules-$(uname -r)

alternatively, you can also instal linux-restricted-modules-generic to make sure your nvidia driver will always stay up to date.

I think I used Automatix first, then some other script that was just for updating the latest nvidia driver. But I'm not sure if the latter worked, and I forgot what it's called. Any idea?

Anyway, I'll try what you suggested. But it would be nice if you could explain what is wrong and what that line does. Also, how do I do what you suggested so it gets updated automatically next time?

Thanks.

---

### Post by Zzl1xndd on 2007-02-12
using envy worked rather well for me :).

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Nightmist on 2007-02-12
> **tweakedenigma said:**
> using envy worked rather well for me :).

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

That's the name I forgot. When I ran it outside of KDE (like you're suppose to, right?) it just went to black after a while and nothing happened until I did something. Oh well. I'll try it.

---

### Post by Nightmist on 2007-02-12
I'm running the new kernel now, and it seems to be working. Thanks for reminding me of envy :)

And I still got the lock-up problem, but I found a tips about pressing Alt + F1 when it happens, and it worked out well.

---

