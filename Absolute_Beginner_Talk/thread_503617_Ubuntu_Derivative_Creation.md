---
title: "Ubuntu Derivative Creation"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by sourjax on 2007-07-18
I don't know it this is the right place for this but:

I've searched everywhere but  I can't find a tutorial on how to create a Ubuntu/Linux derivative. I know about "Linux From Scratch", but I like the way Ubuntu works, but I want a highly customized version that is more in the vein of Damn Small Linux. Maybe "Dang Small Ubuntu" :) 

Anyway, I would love to learn how to build/create a Linux Distro, specifically a Ubuntu derivative, any ideas?

My goal for my "Dang Small Ubuntu" it can be:

1. Booted from a 256MB USB as a live linux distribution (LiveUSB)
2. Booted from within a host operating system
3. Run fully in RAM with as little as 128MB 
4. Be completely Modular
5. Can be installed to a Hard Drive easily

note: "Dang Small Ubuntu" is not what I would actually call my derivative so if anyone wants to use it pls feel free.

---

### Post by shearn89 on 2007-07-18
I would recommend using the server edition, which installs a basic command line interface, from which you can install whatever else you want (eg fluxbox/openbox/blackbox/xfce/gnome etc...). I guess if you wanted to make this into an install cd you could copy the server ed. iso, and add a script to "sudo apt-get x y z"?

---

### Post by pyros on 2007-07-18
> **sourjax said:**
> I don't know it this is the right place for this but:

I've searched everywhere but  I can't find a tutorial on how to create a Ubuntu/Linux derivative. I know about "Linux From Scratch", but I like the way Ubuntu works, but I want a highly customized version that is more in the vein of Damn Small Linux. Maybe "Dang Small Ubuntu" :) 

Anyway, I would love to learn how to build/create a Linux Distro, specifically a Ubuntu derivative, any ideas?

My goal for my "Dang Small Ubuntu" it can be:

1. Booted from a 256MB USB as a live linux distribution (LiveUSB)
2. Booted from within a host operating system
3. Run fully in RAM with as little as 128MB 
4. Be completely Modular
5. Can be installed to a Hard Drive easily

note: "Dang Small Ubuntu" is not what I would actually call my derivative so if anyone wants to use it pls feel free.

you might want to start at the reconstructor website ([http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/))
and then perhaps have a chat with the folks on #ubuntu-derivative

---

### Post by mjwhitfield on 2007-07-18
> **sourjax said:**
> My goal for my "Dang Small Ubuntu" it can be:Something like this?

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by pyros on 2007-07-18
> **mjwhitfield said:**
> Something like this?

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Eh, that's just a small image to start a nework install though, he sounds like he wants an X environment. If not, you might want to look at cubuntu.

---

### Post by mjwhitfield on 2007-07-18
> **pyros said:**
> Eh, that's just a small image to start a nework install though, he sounds like he wants an X environment. If not, you might want to look at cubuntu.But the genius of that image is you can build whatever you want from it, then it can be packaged and used as he suggested.

---

### Post by sourjax on 2007-07-18
Thanks for the quick replies...

@shern 
How would I go about adding those scripts?

@pyros
I think the reconstructor program is only part of what I need, I want to create a completely customized derivative of Ubuntu, branding and all...

@pyros #2
What is cubuntu?

Are there any tutorials out there or anything that can tell me how Kubuntu, Xubuntu, Edubuntu, etc were built/created. 

I guess what I'm asking is how was Kubuntu or Xubuntu created from Ubuntu. Or how was Linux Mint or Fluxbuntu created.

---

### Post by shearn89 on 2007-07-18
I think you'd just write a script (something like):
```

#!/bin/bash
sudo apt-get install -y --with-recommends x y z

```
and burn it onto the cd as well, then you could just run it from the cd once the server is set up. (I think).

---

### Post by urukrama on 2007-07-18
[fluxbuntu]("http://www.fluxbuntu.com/")?

---

### Post by sourjax on 2007-07-18
@urukrama
Fluxbuntu? How was it built?

Is there no where I can find out how these were built? Is there no "Ubuntu From Scratch" or something, anything?

---

### Post by pyros on 2007-07-18
> **sourjax said:**
> @urukrama
Fluxbuntu? How was it built?

Is there no where I can find out how these were built? Is there no "Ubuntu From Scratch" or something, anything?

well, remember that ubuntu is still debian really. take a look here:
[http://wiki.debian.org/DebianCustomCD](http://wiki.debian.org/DebianCustomCD)
[http://wiki.debian.org/Simple-CDD](http://wiki.debian.org/Simple-CDD)

1. reconstructor handles most of the branding.
2. cubuntu is a textmode-only ubuntu derivative.

also, take a look at gnewsense, I'm pretty sure it is exactly what you want: [http://www.gnewsense.org/Builder/HowToCreateYourOwnGNULinuxDistribution](http://www.gnewsense.org/Builder/HowToCreateYourOwnGNULinuxDistribution)

---

### Post by sourjax on 2007-07-19
@Pyros

I haven't had much time to look at the things from you post but the short look I did get shows me you may have solved it I'll let you know when I get a chance to look at it further. Thank you for your help.

---

### Post by sourjax on 2007-07-19
> **mjwhitfield said:**
> But the genius of that image is you can build whatever you want from it, then it can be packaged and used as he suggested.

Are you saying that I can download, burn and install the minimal.iso then "sudo apt-get install" everything I need and then create a installation disk from that?

---

### Post by mjwhitfield on 2007-07-19
Probably, I'm not sure how you go about compressing the stuff up and making the install disk however.

---

### Post by sourjax on 2007-07-19
If I start with the minimal.iso and build on top of that, will the reconstructor program do the rest. e.g. Branding, default theme creation, etc.

BTW anybody know how I can create a Theme?

---

### Post by pyros on 2007-07-19
> **sourjax said:**
> Are you saying that I can download, burn and install the minimal.iso then "sudo apt-get install" everything I need and then create a installation disk from that?

The first link I posted, to the DebianCustomCD is essentially a howto for creating a custom install disc based on the minimal cd.

Try downloading a theme from the repositories and opening the deb up with archive manager. that should get you started.

---

