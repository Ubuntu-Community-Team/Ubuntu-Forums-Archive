---
title: "something wrong in sources.list?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by coconeco on 2007-04-24
Hello.

I have just downloaded 7.04 last night and knew something wrong in the sources.list.  (It might have already been something wrong.)  

Output of cat /etc/apt/sources.list is ;

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main

Just this...

I tried to find the way to recover it but it is too difficult for me.   :( 

Need your help..

Coco

---

### Post by Rui Pais on 2007-04-24
Hi

Start synaptic, on menus choose Settings -> Repositories. Check the missing ones, under Ubuntu Software.
You can choose too a mirror close to you, to speed up a bit.

Or you can use a site to do your sources.list. Like[ source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/").

hth

---

### Post by kerry_s on 2007-04-24
Here's what i'm using->

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) feisty-commercial main 

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main 



For the multimedia key:

sudo apt-get debian-multimedia-keyring
or 
just find it in synaptic and install.

---

### Post by Rui Pais on 2007-04-24
hi kerry_s,
i noted the "deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main" entry on your suggestions.

Isn't mixing debian with ubuntu repos considered a bad idea?

You may consider check Mediubuntu:
[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

---

### Post by coconeco on 2007-04-24
Thanks for the prompt reply, Rui Pais and kerry_s!

---

### Post by kerry_s on 2007-04-24
> **Rui Pais said:**
> hi kerry_s,
i noted the "deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main" entry on your suggestions.

Isn't mixing debian with ubuntu repos considered a bad idea?

You may consider check Mediubuntu:
[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)


Normally, i been using it since dapper with no problems. i use it for the w32codecs and libdvdcss2. depending on what player i use, with vlc i don't need it.

---

