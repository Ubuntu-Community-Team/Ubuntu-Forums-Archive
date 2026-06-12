---
title: "ubuntu to Kubuntu??"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-03-21
hello all, 

i've been using ubuntu for about a month but when i installed ubuntu, i was hasty. i didn't try other distros or look into deciding gnome or kde interface.

anyway, i think i want to add kubuntu to my OS's on this computer. i have ubuntu edgy and winxp on dual boot.

i was wondering if i should 

A) install kubuntu on a separate partition but was wondering how that would work with grub.

B) use the kubuntu live cd to upgrade ubuntu edgy, but was wondering what would happen to my programs, ndiswrapper (also, how does that work on kubuntu), and could i switch back if i decide i made the dumbest mistake ever.

any advice would be appreciated, even if you tell me i'm a complete moron and should just stick to what i have. :lolflag:

---

### Post by Redache on 2007-03-21
go to a terminal and type

```
sudo apt-get install kubuntu-desktop
```

and after it's installed log out and there should be a sessions option, just choose KDE and you'll log into the Kubuntu Desktop.

---

### Post by oilchangeguy on 2007-03-21
there's not that much difference. kde is more windows like in it's appearence. and gnome is more mac like. before you jump in simply burn a copy of kubuntu and run the live cd to see if you like it, and go from there.

---

### Post by gh0st on 2007-03-21
You can just install the KDE desktop into your current Ubuntu system and you can then choose KDE or Gnome in "session type" when you login

Try this
```
sudo apt-get install kubuntu-desktop
```

I haven't tried it myself but I know other people do it. The only real difference between Ubuntu and Kubuntu is one comes with Gnome the other with KDE I think, the underlying system is the same. You can have both desktops installed. No point installing a completely new system just to try KDE unless you really want to do that. If you your Ubuntu working the way you want with wireless and such, just add the Kubuntu desktop.

Hope that helps, good luck :)

---

### Post by gameman12 on 2007-03-21
thx guys. i used the livecd and i think i'm gonna go for it. thx

---

### Post by gameman12 on 2007-03-21
Thx again guys, i just did and am currentyl using kubuntu. thx a lot

---

### Post by ajgreeny on 2007-03-21
But if you do try it, don't use apt-get or synaptic, but use aptitude instead (sudo aptitude install kubuntu-desktop).  Then if you decide you prefer gnome/ubuntu and want to get rid of kubuntu/KDE, you can do it very simply with "sudo aptitude remove kubuntu-desktop" and everything kde/kubuntu will be uninstalled, leaving you with a plain ubuntu again.

Personally I have done what you are contemplating and use both desktops, but I do prefer kde, and that is my default.  Give it a try, I think you'll like it.

---

### Post by gameman12 on 2007-03-21
ok thx, but i used apt-get already and am using kde.

i agree with u, i prefer kde too

---

