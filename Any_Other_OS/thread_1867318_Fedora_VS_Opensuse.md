---
title: "Fedora VS Opensuse"
date: 2011-10-22
forum: Any Other OS
---

### Post by Glenn nl on 2011-10-22
Hi.
I tried Gnome 3 yesterday and I really like it (except for no shutdown button, but there are tweaks for that) so I want to switch to a Gnome 3 distro. I am considering Fedora 16 and Opensuse 12.1. I kinda like Fedora (Systemd, no mono) but I heard it isn´t very user friendly. Is Opensuse more user friendly (in installing codecs etc.) and what are the differences between Yast and Yum?

Thanks. :popcorn:

---

### Post by wolfen69 on 2011-10-22
What's wrong with gnome 3 on ubuntu? They all look exactly the same after install.

But as far as Fedora and OpenSuse, I prefer fedora. OpenSuse always seemed kind of glitchy to me.

---

### Post by boydrice on 2011-10-23
> **Glenn nl said:**
> Hi.
I tried Gnome 3 yesterday and I really like it (except for no shutdown button, but there are tweaks for that) so I want to switch to a Gnome 3 distro. I am considering Fedora 16 and Opensuse 12.1. I kinda like Fedora (Systemd, no mono) but I heard it isn´t very user friendly. Is Opensuse more user friendly (in installing codecs etc.) and what are the differences between Yast and Yum?

Thanks. :popcorn:

They are pretty similar in terms of codecs, you will need Rpmfusion for Fedora and Packman for openSUSE.  Basically they are fairly similar, Fedora is more bleeding edge with shorter release cycles where openSUSE has a slighty longer release cycle.  YUM and Zypper are similar in features.  Try them out see which one you like.

---

### Post by collisionystm on 2011-10-23
> **Glenn nl said:**
> Hi.
I tried Gnome 3 yesterday and I really like it (except for no shutdown button, but there are tweaks for that) so I want to switch to a Gnome 3 distro. I am considering Fedora 16 and Opensuse 12.1. I kinda like Fedora (Systemd, no mono) but I heard it isn´t very user friendly. Is Opensuse more user friendly (in installing codecs etc.) and what are the differences between Yast and Yum?

Thanks. :popcorn:


You hold the ALT key when you click on the menu to logout. Power Off will appear.

---

### Post by collisionystm on 2011-10-23
> **Glenn nl said:**
> Hi.
I tried Gnome 3 yesterday and I really like it (except for no shutdown button, but there are tweaks for that) so I want to switch to a Gnome 3 distro. I am considering Fedora 16 and Opensuse 12.1. I kinda like Fedora (Systemd, no mono) but I heard it isn´t very user friendly. Is Opensuse more user friendly (in installing codecs etc.) and what are the differences between Yast and Yum?

Thanks. :popcorn:

I admire OpenSuse, and I really really wish I could make it work for me... but I cannot. So I can only give a personal recommendation that you use Fedora. Fedora is a very solid OS and very fast. Install Codec's..etc is a breeze.
Use this program, easy life
[http://easylifeproject.org/](http://easylifeproject.org/)
It will get you everything you need.

Once you have ran easy life, you will want office I am sure.
Open terminal
sudo yum install @office

Enjoy it. It is a great OS. Oh and there is no software center, but you will find that 'yum search' is pretty good!

---

### Post by Utew on 2011-10-23
OpenSuse is a KDE based distro, but Gnome3/Shell runs fine on it... though I would have to agree it can be a bit glitchy (at least for me). Fedora is a great distro.. and if you go that way you might want to install Yumex for package management, I wouldn't use Fedora without it, myself (Similar to Synaptic).

But Wolfen69 hit it on the head "What's wrong with Gnome 3 on Ubuntu?" Which is what I am running.. I have removed Unity 3d and compiz. Working flawlessly...

 If I had to compare the stability of Fedora 15 and Ubuntu 11.10 (both running Gnome 3/Shell).. I'd say it's a dead heat.. they both are rock solid. I'm preferring Ubuntu/ Gnome Shell atm.... PPA's make the difference for me personally, though I would like to see Ubuntu migrate to systemd as Fedora has done... no matter. In any case good luck with your decision. :)

---

### Post by Glenn nl on 2011-10-23
> **Utew said:**
>  But Wolfen69 hit it on the head "What's wrong with Gnome 3 on Ubuntu?" Which is what I am running.. I have removed Unity 3d and compiz. Working flawlessly...

I am running that now too. I prefer an official Gnome 3 distro above installing packages on Ubuntu. With Fedora I know they will make sure Gnome 3 is working flawlessly, with Ubuntu (Canonical to be more specific) I don´t think so. Besides, I am still young and want to learn more about Linux, just apt-get and debs is boring. I have been running Ubuntu for 2.5 years, it´s time for something else. ;)

---

### Post by ilovelinux33467 on 2011-10-23
IMO they are both great distros (they are my two favourites although I prefer Fedora slightly more). As boydrice said Yum and Zypper are pretty much on par and both have Delta RPM support (means that you use less bandwidth when updating by only downloading the difference between the last update and the new update). Fedora is a lot more bleeding edge which I like. Try them both and see which one fits you best.

---

### Post by sffvba[e0rt on 2011-10-23
If I have a choice of only there two I personally would choose openSUSE (Geeko FTW!).  If I hadn't fallen for all the Mono FUD a few years ago I would possibly still be using it...


404

---

### Post by satanselbow on 2011-10-23
+1 for gnome3 on Ubuntu 11.10. It takes no longer than 10 minutes install gnome3 and remove all traces of unity. Gnome3 being in the official repos is the biggest step forward of the 11.10 release.

If it really came down to Fedora or OpenSuse... I would use Arch :popcorn:

---

### Post by boydrice on 2011-10-23
> **Utew said:**
> OpenSuse is a KDE based distro, but Gnome3/Shell runs fine on it...

This isn't quite true.  It was only a release or two ago that openSUSE actually had a default desktop if you just accepted all the defaults on the DVD.  Not to mention they had at one point employed all the Ximian guys, and I think the SLED default desktop is GNOME.  I have found openSUSE to have top notch implementations of all 4 major DE's.  Even Yast is available in GTK and QT.

---

### Post by Utew on 2011-10-23
Don't get me wrong, OpenSuse has a lot of appeal... not the least of which is "geeko" ;) 
A cute mascot if there ever was one.

---

### Post by Glenn nl on 2011-10-24
I was told that with Opensuse it is just enabling some repo´s for full multimedia support, but with Fedora it is more complicated.
Is it with Fedora that hard or is it just a quick command in the terminal?

Thanks. :popcorn:

---

### Post by eagleton on 2011-10-24
It's very easy with Fedora - go to rpmfusion.org, click a few times, and you're done.

---

### Post by linuxyogi on 2011-10-27
I prefer openSUSE. YAST  is really unique.

---

### Post by cortman on 2011-10-27
Here's where I'm really torn. I've used both for a couple years each as my exclusive OS, and I must say I'm really torn between the two. I think if it would come down to it I would probably say openSUSE. The one deal-breaker for me with both SUSE and Fedora is that it did not support my wireless card, which of course also left me unable to download drivers for it (catch-22). Ubuntu supported it right away, so I opted for the easier way and went ubuntu.
One thing I didn't like about Fedora 15 was Gnome 3. I'm running Gnome 3.2 on my ubuntu and it is WAY superior in my opinion. Add a few extensions and it should be a very successful replacement for my old standby of Gnome 2.

---

### Post by BrokenKingpin on 2011-10-27
I also would just recommend Gnome3 with Ubuntu, but if you really want to run one of those two, go with openSUSE.

And why is Fedora not having mono a good thing, or a disto having mono a bad thing? There are some really good applications built with mono, and it is a damn good development platform in general. I am not saying every distro needs to include it out of the box, but I don't see how it would weigh into choosing a distro or not.

---

### Post by collisionystm on 2011-10-27
> **BrokenKingpin said:**
> I also would just recommend Gnome3 with Ubuntu, but if you really want to run one of those two, go with openSUSE.

And why is Fedora not having mono a good thing, or a disto having mono a bad thing? There are some really good applications built with mono, and it is a damn good development platform in general. I am not saying every distro needs to include it out of the box, but I don't see how it would weigh into choosing a distro or not.


Not having mono is part of the reason why Fedora loads so fast.

---

### Post by collisionystm on 2011-10-27
> **eagleton said:**
> It's very easy with Fedora - go to rpmfusion.org, click a few times, and you're done.


or install easylife

[http://easylifeproject.org/](http://easylifeproject.org/)

---

### Post by collisionystm on 2011-10-27
Opensuse offers Gnome 3. In fact the 12.1 is really nice.

My only pet peeve is Suse does not have Remmina Remote Desktop in its Repo's.

AND you have to install a lot of dependencies and even a patch when doing some like Vmware player.

Ubuntu and Fedora install it out of the box, no problem.

---

### Post by ibutho on 2011-10-27
Both are very good distros and I'd feel comfortable with anyone of them. I'd suggest you try both and then stick with the one that you like.

---

### Post by BigSilly on 2011-10-28
Gnome 3 is absolutely stonking on openSUSE. Can't speak for Fedora, but I used openSUSE for 6 months with Gnome 3.0 and it was stunning. Tried the openSUSE 12.1 Gnome 3 RC1 last night, and again it seems that it's going to be a stellar release. I'm using Ubuntu 11.10 with Unity, but I'll be switching back to openSUSE when the final's out.

---

### Post by sffvba[e0rt on 2011-10-28
> **BigSilly said:**
> Gnome 3 is absolutely stonking on openSUSE. Can't speak for Fedora, but I used openSUSE for 6 months with Gnome 3.0 and it was stunning. Tried the openSUSE 12.1 Gnome 3 RC1 last night, and again it seems that it's going to be a stellar release. I'm using Ubuntu 11.10 with Unity, but I'll be switching back to openSUSE when the final's out.

Cool, I am actually installing RC1 in VB to check out there KDE offering as what I have seen is pretty awesome...


404

---

### Post by BigSilly on 2011-10-28
> **not found said:**
> Cool, I am actually installing RC1 in VB to check out there KDE offering as what I have seen is pretty awesome...


404

Yeah, I mean, I don't mean it as a slight against Ubuntu or Unity. I'm loving 11.10, and it's so far been excellent. I don't really want to lose Ubuntu and Unity (Unity has proved its worth in 11.10 imho), but I don't want to miss out on openSUSE with Gnome 3.

Maybe I'll have to finally ditch the Windows install and have all three Linux DE's. Or just get a bigger hard drive. ;)

---

### Post by BrokenKingpin on 2011-10-28
> **collisionystm said:**
> Not having mono is part of the reason why Fedora loads so fast.
Um... no. Ubuntu loads just as fast as Fedora for me, if not faster. If you are that worried about boot times just don't have applications load on startup (this can be said for any applications, not just mono applications). And if this was the reason for someone not choosing a distro, they should consider professional help.

That unfounded mono hate is absurd. If it is because it is an MS technology, get over it... Java has more legal issues than Mono. If it is because the applications require a runtime then we should also hate all python apps with that logic.

---

### Post by aykoola on 2011-10-29
I'd suggest OpenSUSE, because i used it for a while and was very satisfied with it. I used the Gnome version.

---

