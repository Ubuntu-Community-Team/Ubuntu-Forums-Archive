---
title: "Gnome and KDE"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by TannerLD on 2006-08-31
Hi all,

I've been using Ubuntu so far for about 3 days and so far so good.

What I'm wondering now is it possible to install KDE and still retain the Gnome stuff so I could kind of switch back and forth? Or is that not possible?

I found [this]("http://www.psychocats.net/ubuntu/kde.html") tutorial, but not sure if thats the right way to go. I don't want to screw up. :D

Thanks
-Tanner

---

### Post by Dinerty on 2006-08-31
I do believe this is accessiable by the "Session", choose as you wish :)

---

### Post by calvinthomas on 2006-08-31
That tutorial is exactly the way to do it and you'll be able to log into a KDE environment or a Gnome one, when I first changed I preferred gnome (it's quicker) then I preferred KDE (its prettier) and now I prefer an XGL session running Gnome with tweaks to the eye candy! For me its the best of both worlds. Many people are different though and both KDE and Gnome are excellent!

Calv

---

### Post by sirlancelot on 2006-08-31
That tutorial will work, and you can safely switch between them without problem.

One issue though is that you will have a lot of apps that will do the same thing, but one is designed for gnome and the other, KDE.

Now the app will work in both environments, but I bring it up because your menu will be cluttered after installation.

I recommend KDE to anyone looking for a good, visually attractive window manager.

---

### Post by xpod on 2006-08-31
apparently you can install both the KDE and Gnome desktop environments and you get the option at the logon i believe of which you wish to use.

I personally passed on dual desktops as i have a kubunto pc but i really like the KDE.....theres quite a few differences i remember prefering but i could`nt list them as my heads got SO much of the both of them going round and round from this first two weeks that i aint sure which is which anymore.

LOVE IT

EDIT:...oh well..there you go then...lol

---

### Post by TannerLD on 2006-08-31
Wow, that was fast. Thanks for the replies.

One more thing. If I don't like KDE and wish to uninstall it how would I go about that?

Many thanks
-Tanner

---

### Post by xander848 on 2006-08-31
Use aptitude to install kde so that the desktop and all the dependencies will be removed by: sudo aptitude remove kubuntu-desktop

(its all in the tutorial)

---

### Post by Toxicity999 on 2006-08-31
Install with sudo aptitude install kubuntu-desktop!!!!! I can not stress that enough! Then if you desire to get rid of it with sudo aptitude remove kubuntu-desktop Aptitude will present you with a solution to get rid of all the dependancies. Otherwise you have to remove them by hand which is any Debian users nightmare. (anyone come up with a script to remove the kubuntu-desktop dependancies if they do happen to use synaptic or something? It would be easy as pudding to do. (Instant at that! only less stirring.)

---

### Post by enopepsoo on 2006-08-31
I found that having KDE stuff installed did either one of two things:
[LIST=1]
[*]It was slow to load my kde apps in gnome OR
[*]It slowed down my gnome in general.
[/LIST]
I can't really remember.  This was a while ago

They give you gnome for a reason though.  It is because the developers and whoever REALLY know what they are doing.  If they say 'Use Gnome,' I generally try to say 'How HIGH?'

:tongue: :^o

Honestly though, I tried XFCE as well.  I did not noticed enough of a Speed Boost to keep it (I ran it for a month and just switched back a few days ago).

---

### Post by TannerLD on 2006-09-01
Thanks all.

I installed KDE, and the uninstalled it. Its not really for me. :P

What would the command for XFCE?

Thanks
-Tanner

---

### Post by lowey23 on 2006-09-01
Just go back to the psychocats site and look for installing Xubuntu.

Cheers

lowey

---

### Post by benfindlay on 2006-09-01
to install xfce just type

```
sudo aptitude install xubuntu-desktop
```

Makes it easy to fully uninstall too...

HTH

---

### Post by TannerLD on 2006-09-01
> **benfindlay said:**
> to install xfce just type

```
sudo aptitude install xubuntu-desktop
```

Makes it easy to fully uninstall too...

HTH

Both in the same one? I must've missed that...

-Tanner

---

### Post by benfindlay on 2006-09-01
Yeah on the login screen it asks you which session you want to use: from the ones you have installed. Currently toying with the idea of instaling kubunut-desktop AND xubuntu-desktop to see what theyre like. Luckily I have hard drive space to burn! ;)

Also I can't stress enough using aptitude over apt-get, as aptitude associates your installed file with all of its dependencies so it will get fully removed, whereas apt-get will just leave the dependencies behind if you try to uninstall, adn trust me, desktops install a LOT of dependencies!

Hope this helps!

---

