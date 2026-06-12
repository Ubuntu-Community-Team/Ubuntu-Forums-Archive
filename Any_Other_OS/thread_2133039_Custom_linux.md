---
title: "Custom linux?"
date: 2013-04-06
forum: Any Other OS
---

### Post by joco1500 on 2013-04-06
i was wondering that is there was a website that will let you make something close to a custom linux opperating system.
it doesnt have to be a full-blown os, but lets you pick the desktop environment and some default package

it would have to have low system requirements though :(

like a ASUS aspire one or a Dell latitude d400

i would also like it to have wireless card support for those two, but it is not necessary.

thank you in advance

---

### Post by ibjsb4 on 2013-04-06
Not a site, but the [mini iso]("https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+mini+iso&ie=utf-8&oe=utf-8"), people running servers also put [minimum GUIs]("https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+server+gui&ie=utf-8&oe=utf-8") on them.

---

### Post by trent.josephsen on 2013-04-06
If it boots and can install software, it is pretty much a "full blown OS", so I'm a little confused by that bit.

Are you looking for a distro that installs a minimal base, so that you can pick the applications that go on it? Debian is pretty nice in that regard. (I like Arch myself, but I won't recommend it without knowing more about your goals.)

---

### Post by Rukiri on 2013-04-06
Check out Linux from scratch, Gentoo, or even arch.
You start out with squat and you install what you need, arch is a binary distro so by default your kernel has every option enabled and the same goes with packages but that isn't possible to disable features as the binary was already compiled.

A source distro is the best way to go, now granted linux from scratch would take MUCH MUCH longer than gentoo to install but it teaches you how to build a linux distro from the ground up.  Gentoo doesn't have stage1 downloads anymore, linux from scratch you build stage 1, 2 and 3.  From there you config your settings like time, etc and eventually you'll chroot into your system and configure your kernel and system and grub(or whatever boot loader you decide to use).  Than you would boot into your new linux system.

Now I would install a package manager for linux from scratch, portage is probably the best around due to you can configure youe cflags and enable/disable features per package, there's also Sorcery another source package manager.
But you can obviously instapp apt-get or pacman to your new linux system if you want, pacman or portage can be installed on ubuntu but it's more trouble than it's worth as it's an already setup distro.

---

### Post by kevinmchapman on 2013-04-07
Even Arch? ;)

A source distro is not going to be appropriate for someone who is not even aware how to build their own set-up (and of little practical use to anyone else). Nor is it going to work well with "low system requirements".

The mini iso has to be the way to go, given that the objective is not stated to be learning. That way any existing knowledge remains useful.

---

### Post by black veils on 2013-04-07
[http://www.instalinux.com/](http://www.instalinux.com/)

---

### Post by tartalo on 2013-04-07
> **joco1500 said:**
> i was wondering that is there was a website that will let you make something close to a custom linux opperating system.

Yes, [http://susestudio.com/](http://susestudio.com/)

---

### Post by Algus on 2013-04-07
What you are asking is certainly possible though it takes a bit of work and if you don't already know how to do it, you're in for some reading.  To start with, I definitely recommend you stick with Ubuntu for a bit.   If you need to use something lightweight for an older OS, go with Xubuntu or Lubuntu.   Xubuntu is my preference as I like the appearance of Xfce and feel it makes the perfect compromise between lightweight and attractiveness.

Why Ubuntu? Simple, most of the popular desktop environments on Linux have been packaged up for it already and are easy to find.  By installing a few different desktop environments you can get a feel for which environment suits you.   For more on desktop environments: 

[http://lifehacker.com/5762081/-desktop-environments-gnome-kde-and-more-explained](http://lifehacker.com/5762081/-desktop-environments-gnome-kde-and-more-explained)

Now to really dig into Linux and get a DIY distro going takes a fare bit of expertise at Linux's command line but fortunately there are some pretty handy guides on the internet.  I personally recommend Arch to get you started.   This is because there are some awesome tutorials for Arch for command line newbies like this: 

[http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process](http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process)

Seriously though, you could get replies from 100 different users and we'd all have a distro to suggest to you for this point.   If you're just looking for something that works without to much work then Xubuntu/Lubuntu or Debian with Xfce or LXDE would probably suit you fine.   I do run Ubuntu on my laptop but most of the glut has been cleared out since it has relatively low specs (its a chromebook) and it runs pretty great.

---

### Post by joco1500 on 2013-04-07
I know ***HOW*** to do it 

i just don't ***W******ANT ***to do it

I've been using linux since i was 8 and i love it

i just want to experiment a little more that's all

---

### Post by ibjsb4 on 2013-04-07
Huh ?

---

### Post by UltimateCat on 2013-04-07
> **joco1500 said:**
> i was wondering that is there was a website that will let you make something close to a custom linux opperating system.
it doesnt have to be a full-blown os, but lets you pick the desktop environment and some default package

it would have to have low system requirements though :(

like a ASUS aspire one or a Dell latitude d400

i would also like it to have wireless card support for those two, but it is not necessary.

thank you in advance

I see that you mentioned it doesn't have to be a full blown OS but
This site might give you a few ideas-

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

I just went to this store last week and it is an amazing store!
Anything you could imagine for a computer-- (Desktops only)
[http://www.microcenter.com/](http://www.microcenter.com/)

If the Ausus and the Dell you have mentioned are laptops I have found that you can only get those parts from the manufacturer-
[http://search.dell.com/results.aspx?s=dhs&c=us&l=en&cs=19&k=wireless%20card&cat=sup](http://search.dell.com/results.aspx?s=dhs&c=us&l=en&cs=19&k=wireless%20card&cat=sup)
[http://asus.mytechhelp.com/?cpid=35048&gclid=CJabopSUurYCFS4aOgodIzgARA](http://asus.mytechhelp.com/?cpid=35048&gclid=CJabopSUurYCFS4aOgodIzgARA)

HTH ;-)

---

