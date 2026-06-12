---
title: "Gnome &amp; KDE?"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-04-03
I installed Ubuntu w/ Gnome.  I've only ever used gnome, though I am constantly hearing KDE mentioned.  I'd like to try it.  Is it possible to install KDE as well and use both?

---

### Post by taurus on 2007-04-03
Yes.  You can install KDE from a terminal with

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
You can choose which window manager to run at the GUI login screen.  Look at the Option at the bottom left corner for the Sessions menu.

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by tux_rox on 2007-04-03
Besides looks, what are the real differences between Gnome and KDE?

(I have a feeling I'm going to get some long answers...)

---

### Post by in_flu_ence on 2007-04-03
There are softwares that are specially built for Gnome / KDE. Though most of these softwares are compatible on the other desktop platform, there are some that don't.

For me, i classify KDE for those who wants visual effect since you can tweak alot more stuff on the desktop while Gnome is a more down-to-earth load-n-run kinda desktop. Some people find Gnome abit dry but I like it.

Just personal comments. So I am not saying which is better.

---

### Post by mikewhatever on 2007-04-03
Here is a good and basic gmone/kde comparison [http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)
The difference is mainly in the looks, programs, menus and general behavior.
The down side of having both gnome&kde installed is having the menus cluttered with all the programs. If you liked gnome's simplicity, it might drive you mad along with kde's sounds and jumping icons. :) 
Another down side is that if you decide to remove kde (or gnome I suppose), it will leave a lot of junk behind. 
[http://ubuntuforums.org/showthread.php?t=393945](http://ubuntuforums.org/showthread.php?t=393945)

---

### Post by Dual Cortex on 2007-04-03
nvm...

---

### Post by in_flu_ence on 2007-04-03
That's always the con for having multiple desktop. (same goes to xcfe). I am not sure if it leaves that much junk for fluxbox though.

There are some guides out there that teach you to do a clean remove or almost clean remove. Again do that with risk. It works on most system but it might just break yours.

Anyway, you can always download the livecd for ubuntu/kubuntu and have a try. Think trying is the best way to know which is 'better' for your own like.

---

### Post by RealG187 on 2007-04-13
> **taurus said:**
> Yes.  You can install KDE from a terminal with


[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)
That's what I did! [wine dont work for me though!](http://ubuntuforums.org/showthread.php?t=408145)

Anyways, I have Desktops 1,2,3, and 4 and love how I cant sort them, no more constantly minimizing and maximixing over and over! Is there a quick way to switch, I know about the mouse wheel way, but can I use the keypad or row of numbers under the "F" (Function) keys? Like CTRL+ something + number or desktop I want?

---

### Post by Marsolin on 2007-04-14
The best feature of KDE is the KIO slaves.  They all KDE apps to have seamless access over ftp, samba, and other protocols. The advantage of this is being able to treat a share, ftp site, etc. as a normal drive without mounting. It's totally network transparent.

The other big difference for me is that KDE lets you customize a lot more. If you don't like a default setting, chances are you can change it.

If you install KDE and decide to remove it you can easily clean up the leftover by running "sudo apt-get autoremove". You may need the deborphan package installed for that to work though.

---

### Post by Stevo0687 on 2007-04-14
Thanks for the [http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde) link it worked great!  I'm still playing around with Ubuntu a lot.  I like the opening.  But when in Ubuntu I noticed there are some new applications it seems, unless they came from another update.  But the looks don't seem much different.  But who knows.  I'm still very new.  I think I'm gonna delete Ubuntu soon and start over.  I'm just experimenting with it right now and since I'm triple-booting I can afford to delete this and still be fine.  But thanks for the link. I'm still discovering what I like.

---

### Post by randiroo76073 on 2007-04-14
One of the best things I like about Linux is the ability to multi-boot, I've got 14 distros on tap and can play with any of them any time I want with just a simple reboot, no hassle & I'm in another one :)

---

### Post by ubromtoo on 2007-04-14
I'm also about to switch from Gnome desktop to KDE, at least 

experimentally, especially since reading that Linus Torvalds recommends

KDE over Gnome desktop:


         [http://www.desktoplinux.com/news/NS8745257437.html](http://www.desktoplinux.com/news/NS8745257437.html)

                                                             
                                                                               :)

---

### Post by hyper_ch on 2007-04-14
Well, this is Tovalds' point of you... each one has its own needs and you chose the desktop (environment) that suits you best... same goes for the OS - you chose what suits you best...

I run Xubuntu but in Xfce I run a lot of KDE appz... I don't like the KDE interface but I like its appz... it's choices :)

---

### Post by RealG187 on 2007-04-14
> **Stevo0687 said:**
> Thanks for the [http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde) link it worked great!  I'm still playing around with Ubuntu a lot.  I like the opening.  But when in Ubuntu I noticed there are some new applications it seems, unless they came from another update.  But the looks don't seem much different.  But who knows.  I'm still very new.  I think I'm gonna delete Ubuntu soon and start over.  I'm just experimenting with it right now and since I'm triple-booting I can afford to delete this and still be fine.  But thanks for the link. I'm still discovering what I like.

I luv KDE! I like it better than Gnome [sorry GNOME:(  ur gr8 too, beter than windoze:D ]

That was a gr8 link, I am adding it to my sig, should said it would take a long time, it practically reinstalled a new OS, I thought it would just tweak the GUI a little!

---

