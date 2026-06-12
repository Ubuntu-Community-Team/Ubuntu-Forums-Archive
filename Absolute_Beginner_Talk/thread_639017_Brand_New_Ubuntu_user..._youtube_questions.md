---
title: "Brand New Ubuntu user... youtube questions"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by computernub1 on 2007-12-12
Hi, i'm a brand new ubuntu user - former microsoft user.

On youtube videos, the video seems scrunched up. I believe I installed gnache SWF player and also the adobe flash player - I only want the adobe flash player. But now this is how the videos look on youtube:

[IMG]http://img148.imageshack.us/img148/74/screenshotly6.jpg[/IMG]
(notice how its scrunched up at the bottom)
Also when a youtube video is embedded it will not play.
Thank you so much in advance!!!

---

### Post by PeterJS on 2007-12-12
Have you tried uninstalling gnash?

---

### Post by computernub1 on 2007-12-12
I am sorry I am completely new at this. Where would I go to uninstall it?

---

### Post by spiderbatdad on 2007-12-12
try, in a terminal:
```
sudo dpkg -r --purge gnash
```

---

### Post by computernub1 on 2007-12-12
> **spiderbatdad said:**
> try, in a terminal:
```
sudo dpkg -r --purge gnash
``` Thanks for the reply. This came up:

```
dpkg: conflicting actions -P (--purge) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

So does that mean I should change the purge to remove? or the R to a P? or something else?

---

### Post by PeterJS on 2007-12-12
You could also go to System > Administration > Synaptic Package Manager. From synaptic search for gnash, and you can right click on it and select mark for complete remove and then apply the changes.

Here's a good guide to installing things (and conversely uninstalling them) in Ubuntu:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by spiderbatdad on 2007-12-12
sorry about that brain cramp. if you got it from synaptic you can:
```
sudo apt-get remove --purge gnash
```

otherwise:
```
sudo dpkg --purge gnash
```

or like Peterjs said, is probably easiest.

---

### Post by computernub1 on 2007-12-12
Thanks to both of you for the help. I was able to get gnash uninstalled. But now I am having the same problem as the person of this thread:

[http://ubuntuforums.org/showthread.php?t=638305](http://ubuntuforums.org/showthread.php?t=638305)

So I am trying to download it directly from the Adobe website.

I downloaded the first one, extracted it to my documents folder, but am now confused as to what I should do to install it using the terminal.

I should choose the first option, right? .tar.gz (I am using Ubuntu 7.10 - the Gutsy Gibbon ) 

If so, how do I install it with the terminal? Thanks!

---

### Post by jken146 on 2007-12-12
[http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by spiderbatdad on 2007-12-12
here's a thumbnail of my you tube. I dont remember installing any special software other than adobe flash player from synaptic: called, flashplayer-nonfree

---

### Post by Sims2789 on 2007-12-12
> **computernub1 said:**
> I am sorry I am completely new at this. Where would I go to uninstall it?

Or, if you're like most people and have a graphical user interface, go to Applications -> Add/Remove and search for Gnash (and open-source Flash plugin). It probably isn't installed. I bet the proprietary Flash plugin from Adobe isn't either.

Try installing one of them. If that one doesn't work, go to Add/Remove again and uncheck it to uninstall it and then install the other.

You don't need the command line. ;-)

Unless of course your installation of Gnash is broken, which is rare but in that case then follow the other guy's instructions.

---

### Post by jken146 on 2007-12-12
> **spiderbatdad said:**
> here's a thumbnail of my you tube. I dont remember installing any special software

What do you mean by special software?

---

### Post by spiderbatdad on 2007-12-12
i meant i didn't have to get a tarball. i got flashplayer-nonfree right out of synaptic

---

### Post by computernub1 on 2007-12-12
Thank you all very much. I was able to download the file, and just clicked the install executable file within the folder. Youtube and other flash players on firefox are working fine. Thanks!

---

### Post by jken146 on 2007-12-12
> **spiderbatdad said:**
> i meant i didn't have to get a tarball. i got flashplayer-nonfree right out of synaptic

The bug fix is in the Proposed updates now, so if you have those enabled you would have gotten the fix automatically.  If that's not the case for you then I don't know why flash didn't break.  It seems to have done for everyone else.

---

### Post by 2005fz1 on 2007-12-12
Wow I have struggled through youtube for weeks now!! That really helps !
Thanks
Mike

---

### Post by spiderbatdad on 2007-12-12
> **jken146 said:**
> The bug fix is in the Proposed updates now, so if you have those enabled you would have gotten the fix automatically.  If that's not the case for you then I don't know why flash didn't break.  It seems to have done for everyone else.

I have gutsy-updates multiverse enabled in the sources.list. Is that what you mean?

---

