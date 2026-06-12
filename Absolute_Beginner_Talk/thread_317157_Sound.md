---
title: "Sound?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by &lt;xunil&gt; on 2006-12-12
I'm like ten minutes into using linux for my very first time, so all the post-installation tweaks and setting up it all out of my range and comprehension at this current time.  So, to my problem.  I can't hear any sound when I play music or videos,(they're just ones that came on the image) But anyway, how do I drag all my drivers, be it sound, visual like my Nvidia drivers and all that to my ubuntu os?  And if anyone could give me like a crash course on installing things, how it works and where you get them from and basically like a step by step process? I hear alot about some program called WINE or something, so if someone could maybe give a step by step process on getting that program downloaded and installed and running, that would be a great stepping stone for me.

Thanks

---

### Post by Ecthelion on 2006-12-12
Hi and welcome to Ubuntu!

> I'm like ten minutes into using linux for my very first time, so all the post-installation tweaks and setting up it all out of my range and comprehension at this current time.
So, to my problem. I can't hear any sound when I play music or videos,(they're just ones that came on the image)

Which player do you use?

> But anyway, how do I drag all my drivers, be it sound, visual like my Nvidia drivers and all that to my ubuntu os?

For your sound I would recommend you to install some more gstreamer packages...
Just go to System > Administartion > Synaptic Package Manager
Click search and enter "gstreamer"
Read the descriptions and install those you find usefull.

For your Nvidia drivers you'll have to follow a guide.

I would recommend you [this one]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy"), but it is for the latest nvidia drivers.
Maybe someone else knows an easier guide for a good NVidia driver?

---

### Post by bodhi.zazen on 2006-12-12
for sound you need "Restricted formats":

[Restricted formats](https://help.ubuntu.com/community/RestrictedFormats)

The Nvidia drivers just got a whole lot easier.


See this guide: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Yes, that  is correct the nvidia drivers are available as a .deb ...

---

