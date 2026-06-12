---
title: "No more than one audio source working"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by nastavirss on 2007-10-01
I am using Edgy Eft

At any time, only one audio source seems to be working. When i use gaim and say VLC, i am able to hear only vlc and not gaim.

Can anyone tell me how to get around with this problem.


Thanks

---

### Post by Paulmd on 2007-10-01
> **nastavirss said:**
> I am using Edgy Eft

At any time, only one audio source seems to be working. When i use gaim and say VLC, i am able to hear only vlc and not gaim.

Can anyone tell me how to get around with this problem.


Thanks

Feisty, by default mixes audio sources. There is a package, called esound (and esound-common), that handles this. I'm not sure if it's available on Edgy, but do look. If nothing else, google it, and you may find a .deb, to install. Worst case is you can get it from sourceforge, and compile it. Compiling can be a pain, so don't go there unless you have to.

If the packages are available in edgy, this will work. (it will error out if they're not, no harm done) In the terminal:

```
sudo apt-get install esound esound-common
```

---

### Post by Hospadar on 2007-10-01
the problem is that the older sound drivers (OSS) don't support mixing like the newer (alsa) drivers. so doing as above will hopefully work.

---

### Post by FranMichaels on 2007-10-01
> **nastavirss said:**
> I am using Edgy Eft

At any time, only one audio source seems to be working. When i use gaim and say VLC, i am able to hear only vlc and not gaim.

Can anyone tell me how to get around with this problem.


Thanks

I will suggest the opposite of another poster here. Disable ESD, under System->Preferences>Sound uncheck Enable Software Mixing (ESD) 

Reload or kill esd from system monitor, and see if there is sound mixing now. ALSA+dmix should handle it... If not no harm done, and you can re-enable ESD.

:popcorn:

---

