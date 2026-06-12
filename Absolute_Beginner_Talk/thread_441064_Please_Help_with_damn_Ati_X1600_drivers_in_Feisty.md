---
title: "Please Help with damn Ati X1600 drivers in Feisty"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by SSamaeLL on 2007-05-12
I can't get the 3D running with my Ati X1600 on Feisty.

I did follow all this guides,

- [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
- [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

( Restricted Drivers in Feisty, Envy, Official Ati Drivers.... Thousands of Guides...) but nothing works. My main propose is to enable the 3D acceleration in order to use (Beryl, Games, Cedega....).After searching in Internet I realise there is some bug with my graphics card in Feisty. Other users can't even see anything once the restricted drivers is enabled, but in my case everything works fine apart from the 3D.
Do I have some chance to have my Ati X1600 Pro AGP running 3D on Feisty?

Thanks Mates.

---

### Post by mcduck on 2007-05-12
On top of this forum there's a sticky thread with instructions how to get Ati X-series working in Feisty:
[http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by Golyadkin on 2007-05-12
mcduck, SSamaeLL said he followed that guide in this opening post and it didn't work for him.

I myself can only say that I am running Feisty with a X1650XT but it is PCI-express and it works fine with the restricted drivers from that sticky post. However, I have not tried getting Beryl or Compiz to run because the computer is too critical for me to mess around with. I would try out enabling 3D for you if I could, but I am sorry that I can't risk not being able to boot into GDM at the moment.

I am surprised though that for the Windows platform ATI has one driver for practically every single card they ever made and for Linux there are different tricks needed for every single card :)  I hope the people at AMD start seeing the future of Linux and start supporting it, but as we see how AMD is doing lately, they first need to look at surviving the furst place.

However, I am definitively interested if you find a solution as it might apply to me as well. I am sorry I cannot help at the moment.

---

### Post by mcduck on 2007-05-13
I have Mobility Radeon X1600 on my laptop, and following that instruction worked without any problems.. It really should work just as well with normal X1600..

---

### Post by Golyadkin on 2007-05-13
I think there might be a problem with all these ways of getting it to work. Because if you try any of the ways and it doesn't work, there are no steps included to completely 100% absolutely go back to the state of configuration and everything before you started trying out that. I can imagine that if you try two ways, and they don't work, and then try a third, it still doesn't work, but it would have worked if you had tried that one first.

---

### Post by SSamaeLL on 2007-05-14
I tried already any post and wiki I found. without any single success !!!. I have reinstalled almost 15 times my ubuntu 7.04.
I'm really desperate with this....

---

### Post by Hellionxxx on 2007-05-30
I am a newb to the whole linux thing. It would seem pretty straight forward from what I have read, but I have tried all the same things you have tried and ended up with the same results. Looks like its no luck for now if you are running feisty 7.04 and an X1600 Radeon. 
On the brighter side of things though, I have learned many things that you would never learn if it was too easy.
Hope somebody can help out soon. 
Feisty is great other than this hang up.
Thank god for sudo dpkg-reconfigure xserver-xorg.  It makes getting back in the game cake.
;)

---

### Post by Brightbelt on 2007-05-30
I have an ATI X-1650 and went through several crashes... Finally someone showed me this program
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

*******A word of CAUTION: This ONLY PARTIALLY worked for me. How can I say that?...Well, after I installed it, my system crashed (yet again), BUT, I tried booting into a different Kernel and it worked there for some reason !!

As for me, I was uncomfortable with a situation where one Kernal worked and another didn't. So, I uninstalled the accelerated driver. But this program came closer to fixing it than any other method.

I hope this helps, Frank Bright

---

### Post by Hellionxxx on 2007-05-31
I have tried that as well. It would make the whole process way easier. However, I had no luck with it.  :(

---

