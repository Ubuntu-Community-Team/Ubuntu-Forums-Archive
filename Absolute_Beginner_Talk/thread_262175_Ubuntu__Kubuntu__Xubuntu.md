---
title: "Ubuntu / Kubuntu / Xubuntu?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by hyper_ch on 2006-09-21
Hello

I finally tested everything out that I wanted... everything works fine so far... even got vmware to run for the last few windoze appz that I still require... I did this so far on ubuntu and I'm just about to wipe everything for a clean install (as I messed a lot up while I was trying out things).

My question now is what are the main differences betwen (KX)ubuntu?

I know Ubuntu uses Gnome, Kubuntu uses KDE, Xubuntu uses Xfce but in the end where are those differences?
What is recommended for whom?

Or is there a way to install KDE, Gnome anx Xfce on the same machine so that on the login window I just can select what I want? Is that possible?

Thanks for the feedback :)

---

### Post by Perfect Storm on 2006-09-21
The diffrences lies in the Envoriment you choose as you named (KDE, Gnome, XFCE). Nothing else.

---

### Post by missmoondog on 2006-09-21
and all it takes to install all of them is a simple apt-get or right through synaptic. all will run fine. then, when you login, you just choose which environment.

---

### Post by xyz on 2006-09-21
> Or is there a way to install KDE, Gnome anx Xfce on the same machine so that on the login window I just can select what I want? Is that possible?

Yes it is!
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) See "Playing Around"...have fun!!

---

### Post by bulldog on 2006-09-21
The difference between the three buntu's is basicly the looks and the amount of system resources that they use.

Offcourse you can install all three of them and choose at login which one you want to use.

But keep in mind that there will be some mix up in the apllications menu.
Meaning you will see KDE programs in your Gnome menu.
You can alter this with alacarte but it should be mentioned.

---

### Post by benfindlay on 2006-09-21
Pretty much the only diffreences are the way it looks on screen, and a couple of alternative programs (eg for text editing gnome uses gedit, kde uses kate)

you can install all desktops easily, lthough it'll take up a fair bit of space.

Once you've installed ubuntu from the live cd, launch a terminal and type

```
sudo aptitude install kubuntu desktop
sudo aptitude install xubuntu desktop
```

Or say you installed Kubuntu or Xubuntu, replace the line above that relates to your chosen install with
```
sudo aptitude install ubuntu desktop
```

This will install everything that the 3 systems do differently. Then, when you boot up to the login screen, you can choose which "session" you want to use

I should warn you however, installing the 2 more desktop environments will take up somewhere between an extra 300Mb and 1 Gb of your hard-drive I think once theyre unpacked and installed (perhaps someone else can confirm these figures)

Hope this helps

---

### Post by xyz on 2006-09-21
**orb9220** ran into this pbm:
Where is it written? Installing kde uninstalls xfce!  
[http://www.ubuntuforums.org/showthread.php?t=259714](http://www.ubuntuforums.org/showthread.php?t=259714)

---

### Post by benfindlay on 2006-09-21
> **xyz said:**
> **orb9220** ran into this pbm:
Where is it written? Installing kde uninstalls xfce!  
[http://www.ubuntuforums.org/showthread.php?t=259714](http://www.ubuntuforums.org/showthread.php?t=259714)

lol it certainly didn't do that for me, and I installed kubuntu last of all! Bizarre

---

### Post by hyper_ch on 2006-09-21
Thx for your replies... as I currently have a 60 GB, a 120 GB and a 160 GB drive and only have 50 GBs of MP3s, a couple of movies and dvd images and tons of documents and pictures I still have plenty of space left :) I think even more than half of it so installing all three desktops (using approx. 1 GB) won't hurt me at all :)

Thx for all the feedback...

Just one question: So far I've used Ubuntu and also I installed some of the KDE appz that were available in the "Add Software" app (was that synaptic?) and according icons were added to the gnome menu.

If I install now all three desktops and install in gnome some KDE app, will the app icon be added to all three desktop menus?

---

### Post by Metacarpal on 2006-09-21
> **sjau said:**
> Thx for your replies... as I currently have a 60 GB, a 120 GB and a 160 GB drive and only have 50 GBs of MP3s, a couple of movies and dvd images and tons of documents and pictures I still have plenty of space left :) I think even more than half of it so installing all three desktops (using approx. 1 GB) won't hurt me at all :)

Thx for all the feedback...

Just one question: So far I've used Ubuntu and also I installed some of the KDE appz that were available in the "Add Software" app (was that synaptic?) and according icons were added to the gnome menu.

If I install now all three desktops and install in gnome some KDE app, will the app icon be added to all three desktop menus?

You should have access to most, if not all, of your Gnome/KDE/XFCE apps in all three environments...

and hey - if you're not using those hard drives, can I have one? LOL

---

### Post by benfindlay on 2006-09-21
I believe they will. However, to my knowledge certain applications do not work properly in their non-native desktop environment (i.e. certain kde apps will not work, or will run badly/slowly under gnome/kde/xfce etc)

This may well make having all 3 desktops installed a blessing in disguise as you can just log into whatever session you need to run a certain app! ;)

While you're at it, you should also install fluxbox and icewm just for the sake of having as many different desktop environments as possible! ;)

---

### Post by xyz on 2006-09-21
> I currently have a 60 GB, a 120 GB and a 160 GB drive...wow...gimme some! just kidding lol!

---

### Post by hyper_ch on 2006-09-21
> 
fluxbox and icewm

Even more desktops... hmmm :) I guess it won't break anything installing them...
^^

With regard to the HDs... the 60GB will be used for windoze (well, VmWare Server will use that partition for a windoze virtual pc as I still need my Lotus Notes, my Photoshop, Skype with Video support, Word 2003 with the "cite while you write" option provided by EndNote and a few other small things), the 120 GB will be the linux root and swap and on the 160 GB I'll just make incremental backups with rsync :) so there's no drive left for giving to other people, sorry ^^

---

### Post by hyper_ch on 2006-09-21
Just one more question: How big should the swap partition be?

---

### Post by Metacarpal on 2006-09-21
Generally speaking, it's recommended to have a swap between 1.5 and 2 times the size of your RAM.  Of course, if you have 1GB or more of RAM, the swap file will probably be completely redundant unless you are running some seriously intensive apps.

---

### Post by hyper_ch on 2006-09-21
Well, I guess VmWare is an intensive app :) I got 1 GB DDR and assign 512 MB to VmWare...

---

### Post by Sentinel83 on 2006-09-21
> sjau  	Just one more question: How big should the swap partition be?

sjau,

I believe it is general practice to have your swap be twice your amount of RAM.  So for a 512 MB system, about 1GB of swap space...

---

