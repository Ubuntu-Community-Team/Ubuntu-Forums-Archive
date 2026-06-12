---
title: "Synaptic installation difficulties"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-04
Hi
This is my eleventh day using Ubuntu dapper and, during that time, I must have installed/reinstalled Flashplugin-nonfree at least 10 times.
The reason is the very frequent failure of sound in Flash movies and I need to do this to get it back.

Normally, the reinstall takes at most a couple of minutes. However, today, in the twice I tried it, it went to over 30 minutes before I cancelled the operation.
Problem here is that, having cancelled the installation, Synaptic demands that you complete the operation through a dpkg command before Synaptic can be used for anything.

The dpkg command does what seems to be the same "setting up FlashPlugin-nonfree" operation in Terminal that was taking forever in Synaptic. It does at least go to completion in Terminal after about 6-7 minutes.

I'm concerned that the trend is moving towards an unusable Synaptic.
Anybody come across this behaviour before?

Thanks
Paul

---

### Post by em3raldxiii on 2006-08-04
The only time I have ever come across this sort of behavior is with commercial packages from companies like Macromedia, nVidia, ATI, etc.  I think (I'm not an authority) that it has something to do with proprietary software and the fact that the companies do not allow open-source communities access to the code.  This causes problems with producing packages that handle the required dependencies, I think, so that Synaptic can't really do all that it does with open-source packages (or multiverse ported packages).
 
So as to this "moving toward an unusable Synaptic", I don't think that's the concern.  On the contrary, in fact, as these problematic software packages become more acknowledged in the commercial world, I think they will become resolved.
 
As to answering your specific problem ... I can't.  Partly because I am not at my Ubuntu computer (I'm at work), but also partly because I lack the expertise :/ ... good luck though! :D

---

### Post by 23meg on 2006-08-04
The flashplugin-nonfree package that you download from the repository doesn't contain the plugin itself, but a program that downloads the plugin. This is what it does when it says "Setting up flashplugin-nonfree..." and it sometimes takes longer than usual. This is due to network/host conditions. To remove half installed / broken packages, do this:```
sudo apt-get -f install
```

---

### Post by PaulFXH on 2006-08-04
Thanks to everybody for the replies.
It seems from what 23meg says that the problem is more likely to be related to difficulties with the server from which I'm downloading the FlashPlugin package.
This conclusion certainly fits in with the evidence and is much more convenient for me to believe.

Paul

---

### Post by 23meg on 2006-08-04
> **PaulFXH said:**
> 
It seems from what 23meg says that the problem is more likely to be related to difficulties with the server from which I'm downloading the FlashPlugin package.
Paul
I was saying that it's related to difficulties with the server from which the application in the flashplugin-nonfree package is downloading the plugin from, which is perhaps Macromedia's server.

---

### Post by em3raldxiii on 2006-08-04
So in essence, I am still not 100% wrong ... yay!  Basically if the *ACTUAL* plugin was supplied by the repositories, then we'd have no problems.  But since it's Macromedia/Adobe's baby, we can't HAVE it, it's gotta be acquired from THEIR servers.  I always blame it on the "big" guy. ;)

---

