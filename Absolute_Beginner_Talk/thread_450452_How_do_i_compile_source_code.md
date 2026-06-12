---
title: "How do i compile source code?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by K_Alex on 2007-05-21
Greetings

I have myself in an interesting predicament;
I really wanna get into ubuntu and stuff but I've found it kinda hard without an internet connection for that box. 

Currently, I get on the net via my phone and a 3G connection. This however requires propriety software (Motorola Phone Tools) which i can't find a replacement for.

So my plan to get it working is to run it all through wine. Here's where my problem lies; How do i compile/install wine without an internet connection?
All I have so far is the wine source sitting on my windows box.

---

### Post by ThinkBuntu on 2007-05-21
Follow the instructions at [http://www.winehq.com]("http://www.winehq.com"). It should guide you through pretty well. Or, to make it easier, go to the Ubuntu repository through your browser and track your way to the Wine .deb installer. You can find the link to the repository in the "Repositories" window in Synaptic Package Manager.

---

### Post by Iarwain ben-adar on 2007-05-21
Hiya,

you'd best install wine from the .deb they offer for download

=> [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

(choose what you want :D )


Iarwain

---

### Post by ruy_lopez on 2007-05-21
I don't know the dependencies for WINE, but compiling usually just involves typing "./configure", then "make", then if all went well, "sudo make install". If it's a good package it'll usually tell you if there are other packages that have to be installed first. If it's a bad package it'll just fail to compile and spit out unhelpful error messages. 

The link gives a list of recommended packages for wine:

[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

If your build fails and the errors resemble one of these package names, try building the package from the list, and then try building WINE again. In this situation you would do "make clean" before retrying the build.

---

### Post by K_Alex on 2007-05-21
Thanx for the insanely quick replies :)

Remember, I don't have net (yet) on my ubuntu system.
And some confirmation, if I download the .deb package, I can just paste it on my ubuntu desktop, run it, and it'll install itself? (and my life will be magic once more!)

---

### Post by Iarwain ben-adar on 2007-05-21
Yes you can.

Just make sure you have the dependancies installed..

This is what i get when i type 'apt-cache depends wine'
> Vereisten: libstdc++6
  Vereisten: libasound2
  Vereisten: libaudio2
  Vereisten: libaudiofile0
  Vereisten: libc6
 |Vereisten: libesd-alsa0
  Vereisten: libesd0
  Vereisten: libgcc1
 |Vereisten: libgl1-mesa-glx
  Vereisten: <libgl1>
    libgl1-mesa-glide3
    libgl1-mesa-glx
    libgl1-mesa-swx11
 |Vereisten: libglu1-mesa
  Vereisten: <libglu1>
    libglu1-mesa
  Vereisten: libgphoto2-2
  Vereisten: libgphoto2-port0
  Vereisten: libice6
  Vereisten: liblcms1
  Vereisten: libldap2
  Vereisten: libsm6
  Vereisten: libstdc++6
  Vereisten: libx11-6
  Vereisten: libxau6
  Vereisten: libxext6
  Vereisten: libxml2
  Vereisten: libxslt1.1
  Vereisten: libxt6
  Vereisten: libxxf86vm1
  Suggesties: msttcorefonts


Vereisten = dependencies
Suggesties = suggestions 

Normally you have most (if not all) dep's installed by default..


Iarwain

---

### Post by K_Alex on 2007-05-21
Awesome!

Hopefully my next post will be with ubuntu as my backdrop.

---

