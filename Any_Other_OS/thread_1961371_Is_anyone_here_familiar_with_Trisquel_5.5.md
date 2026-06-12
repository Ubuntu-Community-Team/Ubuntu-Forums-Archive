---
title: "Is anyone here familiar with Trisquel 5.5?"
date: 2012-04-19
forum: Any Other OS
---

### Post by diablo75 on 2012-04-19
I was in a squeeze to find a distro that would still run on i686 architechture and I've managed to get Trisquel 5.5 installed on a really really old HP (it has a Windows ME sticker on the front of it).  Just now exploring the OS I'm realizing that its default selection of software is all non-proprietary I think.  So when I typed in "sudo apt-get install firefox" in just decided to install Abrowser instead.  So I was wondering if there is a way for me to add some extra repositories to the software sources that would gain me access to some more common software like firefox, etc.?

---

### Post by boydrice on 2012-04-19
> **diablo75 said:**
> I was in a squeeze to find a distro that would still run on i686 architechture and I've managed to get Trisquel 5.5 installed on a really really old HP (it has a Windows ME sticker on the front of it).  Just now exploring the OS I'm realizing that its default selection of software is all non-proprietary I think.  So when I typed in "sudo apt-get install firefox" in just decided to install Abrowser instead.  So I was wondering if there is a way for me to add some extra repositories to the software sources that would gain me access to some more common software like firefox, etc.?

Hi there, i686 is actually one of the most commonly supported architechtures by the majority of Linux distros.  Trisquel is a Libre distribution and one of the very vew Linux distributions endorsed by the FSF.  I think you will find that the distribution is setup to make it very hard for you to install non-free software.  I wouldn't be shocked if they have iceweasel instead of Firefox ala Debian, etc.  You may find that Trisquel does not meet your needs for a Linux distro depending on your feelings about non-free software.

[http://trisquel.info/en/faq]("http://trisquel.info/en/faq")

[http://www.gnu.org/distros/free-distros.html]("http://www.gnu.org/distros/free-distros.html")

---

### Post by diablo75 on 2012-04-19
Well one the reasons I selected Trisquel was because it was one of only two distros to return a search result on distrowatch for distros that are debian based and come with LXDE.  So I'm going to give UberStudent linux a try now.

---

### Post by uc50_ic4more on 2012-04-19
Trisquel is going to be awfully strict about the software being truly free.

Debian and darn near *every* Debian-based distro is going to feature LXDE in some form or another. Debian Stable (Squeeze, as of this writing) for example will have a slightly older LXDE than some others.

---

### Post by Version Dependency on 2012-04-19
> because it was one of only two distros to return a search result on  distrowatch for distros that are debian based and come with LXDE.

[http://wiki.lxde.org/en/Category:Linux_Distributions](http://wiki.lxde.org/en/Category:Linux_Distributions)

Looks like LXDE can be installed on pretty much any distro...including (the first two on the list) Debian and Ubuntu (and all their derivatives and respins).

---

### Post by Lemuriano on 2012-04-19
Hi,

Every day that pass I appreciate more the importance of controlling your software and not the other way around, but is a decision that comes with sacrifices but also with satisfactions. Is sad that many of us do not realize the end result of using non free software. 

When one look at adobe flash in accordance with Google, I have to contemplate the ideal of freedom and if it is morally correct that one or more companies affects the free will of millions.

The kernel that comes with Trisquel is Linux-Libre and it have the ideal of freedom behind it, so to install something the it is not free defeat it´s purpose .

Regards.

---

### Post by anejo on 2012-04-23
I was about to start a new thread for Trisquel and then found this one!
Although English is my mother tongue, I've been 'learning' Spanish as an  extra curricular activity to compensate for any mid-life crisis.

In that context then I recently discovered this distro and run it in Spanish--what hectic fun I'm having with that!
I have it installed in a vbox machine for now. What I like is that that  they use the fallback environment as default and as this is a GTK 3  version of GNOME  panel 2x, its very usable and has a  'classic' feel to it... amongst other things.
If you're really into using only free software--as in limiting or  eliminating proprietary software--then this is also worth a look-n-see!

More info at [https://trisquel.info/](https://trisquel.info/)

---

### Post by anejo on 2012-04-23
Sorry I didn't really answer your question... I was too focused on talking about this distro!

You can add whatever ppas you like to the sources.list
You could also download debs independently from a package source and install at your own discretion
If you used 'gdebi' for instance that would also highlight possible dependencies as well as installing a deb
You could download a specific app like 'firefox' from their website

---

### Post by anejo on 2012-04-29
OK here's two days worth of experience...
**Pros:** I like the desktop. As I said previously, they use the *fallback environment* as default  and as this is a GTK 3  version of GNOME  panel 2x so while its has familiar gnome 3 system settings... it definitely has that *classic* feel. If you want to work in old-gnome-2 methods while in gnome3 then this is better I think than what Cinnamon is trying to do.

**Cons:** this is VERY gnu-linux and they don't like proprietary stuff! That said it doesn't mean you can't add your own PPAs. I struggled to get my wireless enabled because it wasn't supported under the *free* banner. After getting it enabled and looking at the setup... I reconsidered this simple question: did I want to continue working as I did last year or did I want to use the new methods.. *ala-Unity-style?*

I've back to Unity! While the Trisquel distro is really great, Ubuntu has spoilt me and I've come to the realization that actually I do prefer the Unity DE and its methods of working the DE after all!

---

### Post by Lemuriano on 2012-04-29
For the past 3 weeks I have been using Trisquel 5.5 with Xfce 4.8 which is base in Ubuntu on a clean install with my laptop. 

Regarding my hardware, the wifi mini-pci-e (Intel Corporation Ultimate N WiFi Link 5300) wasn´t free and therefore didn´t work. Instead a usb wifi adpater was use as a temporary solution (Realtek Semiconductor Corp. RTL8187). This one happen to be free and of course works like a charm. Also the HP printer connected to our wifi print server was also free so it works perfectly.

When watching videos in youtube, gnash was use for flash. It play then nicely and was able see the videos without any advertisement, that´s a plus for me. My music is all ogg and the videos are all mkv/theora so no obstacle there.
In the Trisquel web site I enter the forums to learn first hand the significance about freedom regarding IT from users like me.

The transition was easy for me perhaps because of my software needs, and want to add that Trisquel 5.5 is very stable. So in conclusion I have been captivated by this OS so much that I just order a wifi mini-pci-e card that is free, to replace the Intel one and finally keep Trisquel for good.

Finally, you can add firefox even if Abrowser is firefox but free. But if you choose to use non free hardware and software that we are all entitle to, you could consider Lubuntu.

Regards.

---

### Post by ratcheer on 2012-04-29
> **Lemuriano said:**
> Hi,

Every day that pass I appreciate more the importance of controlling your software and not the other way around, but is a decision that comes with sacrifices but also with satisfactions. Is sad that many of us do not realize the end result of using non free software. 



Hear, hear!

Tim

---

