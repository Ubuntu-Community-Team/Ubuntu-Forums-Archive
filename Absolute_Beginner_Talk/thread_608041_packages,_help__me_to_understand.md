---
title: "packages, help  me to understand"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Rich78 on 2007-11-09
Hi,

I was wondering if someone could explain why some packages can break systems if they're not compiled for and tested on it?

In this instance I particularly talking about Xandros (not everyone's favourite I know).

I'm led to believe that .deb packages not compiled for Xandros can trash the system?

If I had the source and compiled it myself prior to install would that work?

Just trying to understand things better really.

Thanks

---

### Post by Rich78 on 2007-11-09
bump

---

### Post by TeaSwigger on 2007-11-09
Hello,

Well I may be off, but as my impression goes you might say that Linux is highly modular. Or you could liken it to a web.

This is grossly oversimplified and mostly fictitious but just for sake of discussion. Take an image viewer, lets call it peephole2. You have the GUI you work with - that uses another setup that supplies the buttons etc called GTK. You have a window, well that uses X and other stuff. Say it has a feature to change your wallpaper every ten minutes, well it does that by a script which uses a language called python. To show you a jpg, it uses another setup to process jpgs called Imlib or whatever. To show a .tiff image maybe it needs a different one called tiffany. To rotate the images it uses dzybits, which also uses python. To process the image tags, Urit. Etc and so on. 

But each one of those things has or will likely have different versions over time which may have specific features. Well if peephole2 was designed to use dzybits 1.8 and you have dzybits 1.7, you could upgrade to dzybits 1.8 - unless that is you have python 9.5 and dzybits 1.8 needs python 10.2, but you can't use 10.2 because other things using python work with 9.5... so much for peephole2. 

Now take a .deb of peephole1. Precompiled on ubuntu 6.10. It uses the right versions you have, but you're running LizardLinux stardate 1.0.2.51.0.1.56. Your pythons are squirming over in the /usr/bin/py9.5/py while ubuntu had them caged in /usr/sbin. The source might allow you to adjust the paths but the deb is set on /usr/sbin.

Anyway that's the general impression I have :p

---

### Post by bulldog on 2007-11-09
:lolflag:Nice story TeaSwigger.

---

