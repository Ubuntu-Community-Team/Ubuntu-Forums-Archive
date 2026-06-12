---
title: "amule-Synaptic says I have it installed, but..."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Toadmund on 2007-03-09
Where is it?
I figure I still have to install it, even though synaptic says it is already installed (or is that just the file?), but the install says I need wx widgets, so I try, and one file is always unobtainable:
```
sudo  apt-get install g++ libwxbase2.6-dev libcurl3-dev libgtk1.2-dev libwxgtk2.6-dev gettext make
Reading package lists... Done
Building dependency tree... Done
g++ is already the newest version.
E: Couldn't find package libwxbase2.6-dev

```
and
```
 sudo apt-get install libwxgtk2.5-dev libwxgtk2.5.3 wx2.5-headers
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libwxgtk2.5-dev

```
2 days now, trying to figure this stuff out, all I have managed to do productively is install updates. I want amule to actually test out the sound and video stuff.

Please, any help, I don't want to have to get Vistamized by BillCo (or BallmerCo).
:confused:

---

### Post by mikewhatever on 2007-03-09
System->Administration->Software Sources, and make sure Universe and Multiverse are enabled. I don't think aMule is installed by default, but things may be different.

---

### Post by Toadmund on 2007-03-09
Do you mean 'software properties'?
I don't see software 'sources'.

---

### Post by halitech on 2007-03-09
You are correct but instead of doing it from the command line, you could also go into Synamtic and do a search to install it that way

---

### Post by picpak on 2007-03-09
Or you can go to Applications > Add/Remove > Amule, because I really don't see why you're installing -dev packages.

---

### Post by Toadmund on 2007-03-09
> Amule, because I really don't see why you're installing -dev packages.
It's because I am fresh from windows, I don't know what I am doing yet, that's why I ask questions and try to figure it out, any suggestions on what package I should use?

---

### Post by halitech on 2007-03-09
maybe try

```

sudo aptitude install amule

```

that should install amule with whatever dependencies it requires

---

### Post by mikewhatever on 2007-03-09
> **Toadmund said:**
> Do you mean 'software properties'?
I don't see software 'sources'.

Could be. I do not know which version of Ubuntu you have. It might be properties in 6.06.

---

### Post by picpak on 2007-03-09
> It's because I am fresh from windows, I don't know what I am doing yet, that's why I ask questions and try to figure it out, any suggestions on what package I should use?

Well, installing programs can be frustrating if you're used to the Windows way...but once you get used to the Ubuntu way, it's much easier through Applications > Add/Remove (unlike Windows, the Add in Add/Remove actually means something).

Just open it up, search for aMule, and install it. In case anything you want isn't in there, it's probably in Synaptic.

---

### Post by Toadmund on 2007-03-09
picpak got it, add/remove worked!
Thanks man!
And thanks to all who contributed, my first installed program!
Now, to get a desk icon to open it, I can probably cut and paste?

---

### Post by RomeReactor on 2007-03-09
Hi. Just open "Applications-->Internet"; you should be able to drag the **aMule** icon to your desktop.

---

