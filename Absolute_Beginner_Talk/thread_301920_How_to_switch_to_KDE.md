---
title: "How to switch to KDE?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by thelocust on 2006-11-17
ok i have ubuntu installed but i want to be running KDE i tried to download and install kubuntu but for some reason i cant burn a decent cd. Is there an easy way to _**replace**_ gnome with kde or should i just give the cd another go.

---

### Post by Mike_N on 2006-11-17
you can add KDE just by opening up yer terminal and typing "sudo apt-get install kde". you then have to approve the large download and just walk away for about 20 minutes while it's downloading. From then on, you can choose witch desktop you want to boot into every time you log into a new session. You can also set witch one you want it to default to...

---

### Post by nazgulord on 2006-11-17
It used to be "sudo apt-get install kubuntu-desktop", right? Is that no longer the preferred command?

nazgulord.

---

### Post by urukrama on 2006-11-17
There is no need to do a complete install of kubuntu to try KDE. Kubuntu is basically the same as Ubuntu (same base system), but with a different desktop environment.

But, instead of apt-get (as was suggested earlier), better use aptitude.

Apt-get does not deal very well with dependencies. If you want to remove kubuntu-desktop and installed it with apt-get, you'll have to uninstall all the programs that come with it *manually*.

Better try:

```
sudo aptitude update
```

then, to install kubuntu

```
sudo **aptitude** install kubuntu-desktop
```

if you ever want to remove it, just do:

```
sudo aptitude remove kubuntu-desktop
```

See also [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) and [http://www.ubuntuforums.org/showthread.php?t=205002](http://www.ubuntuforums.org/showthread.php?t=205002)

---

### Post by msak007 on 2006-11-17
> **urukrama said:**
> Apt-get does not deal very well with dependencies. If you want to remove kubuntu-desktop and installed it with apt-get, you'll have to uninstall all the programs that come with it *manually*.

That's one of the improvements I find very useful in Edgy. I personally use aptitude in Dapper, but the new apt-get "autoremove" feature in Edgy removes any apps left behind after an uninstall if they were installed as dependencies, just like aptitude. So it depends on whether or not the OP has Dapper or Edgy installed, but either way using aptitude is good advice.

---

### Post by 454redhawk on 2006-11-17
Do yourself a BIG FAVOR and go for MEPIS 6 if you want to run KDE.
Kubuntu lacks attention and effort. MEPIS picks up where Kubuntu left off.
As its based on Ubuntu these great support forums right here still apply.

:D

---

### Post by mike_hore on 2006-11-18
> **454redhawk said:**
> Do yourself a BIG FAVOR and go for MEPIS 6 if you want to run KDE.
Kubuntu lacks attention and effort. MEPIS picks up where Kubuntu left off.
As its based on Ubuntu these great support forums right here still apply.

:D

For PowerPC??

---

### Post by aysiu on 2006-11-18
You might want to think about using *kde-core*:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by poohbear1616 on 2006-11-18
:???: I thought I'd check out kde since I'm a noob to linux. I wanted to see if gnome or kde worked better for me. I used aptitude like urukrama suggested and evrything went fine. Set kde as default desktop but it's like the two environments merged. All the gnome aps and my background are still there. I guess that is suppose to be? The kde aps are listed along with the others. So, my question is, if I decide to remove gnome will there be problems?

---

### Post by urukrama on 2006-11-18
If you don't want certain KDE applications to show in Gnome, you can use Alacarta Menu editor to not show them in the menus. If you don't want certain Gnome apps to show in KDE, use the menu editor to do likewise.

But there shouldn't be a problem with removing Gnome if you do it properly. Just open a terminal and type 

```
sudo aptitude update
sudo aptitude remove ubuntu-desktop
```

and you should have just KDE left.

---

### Post by d3v1ant_0n3 on 2006-11-18
> **urukrama said:**
> If you don't want certain KDE applications to show in Gnome, you can use Alacarta Menu editor to not show them in the menus. If you don't want certain Gnome apps to show in KDE, use the menu editor to do likewise.

But there shouldn't be a problem with removing Gnome if you do it properly. Just open a terminal and type 

```
sudo aptitude update
sudo aptitude remove ubuntu-desktop
```

and you should have just KDE left.

I tried that a while back. It didn't work for me. I think it's something to do with the installer (from a fresh install) not installing ubuntu-desktop as a metapackage.

---

### Post by aysiu on 2006-11-18
> **d3v1ant_0n3 said:**
> I tried that a while back. It didn't work for me. I think it's something to do with the installer (from a fresh install) not installing ubuntu-desktop as a metapackage.
To remove Gnome, follow this tutorial:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by poohbear1616 on 2006-11-19
Here's been my experience: I used aptitude like urukrama suggested and evrything went fine. Set kde as default desktop but it's like the two environments merged. All the gnome aps and my background are still there. The kde aps are listed along with the others. So would a better way to do it to be to install the core first to get the true kde experience?

---

### Post by urukrama on 2006-11-19
I'm not sure what you mean, poohbear, when you say the two 'merged'. 

If you mean that the Gnome applications appear in the KDE menu (or KDE apps in the Gnome menus): that is quite normal; you can run some Gnome/GTK apps in KDE, just as you can run some KDE apps in Gnome. If you don't want to see them there, just use the menu editor to change the settings (you won't uninstall the applications in this way, just make them disappear from the menus), as I explained in my previous post.

---

### Post by poohbear1616 on 2006-11-19
Pretty much as far as I could tell, what I had was the gnome environment with kde aps listed with the others. Sorry, I must of mis-quoted what was happening...I am a noob so I'm learning as I go.

---

### Post by dpar on 2006-11-19
You have to switch to the KDE desktop at the login screen. Click on Options in the lower left corner.

---

### Post by slugvision on 2008-02-08
hmm i tried to install kubuntu on my macbook......there were 169 updated to install off the bat. not to mention that everytime i instaled the updates 52% through it would get a terminate error like in windows.....and the driver or update it was installing would get corrupted..... to boot i really want to use kde. so now im gonna try to change my ubuntu dektop to kde and see if the same thing still occurs!

---

