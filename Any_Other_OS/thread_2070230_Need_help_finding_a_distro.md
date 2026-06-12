---
title: "Need help finding a distro"
date: 2012-10-12
forum: Any Other OS
---

### Post by DisappearingOak on 2012-10-12
Hello, Till I bought my new computer back in March, I've tried like 20 different distributions, but all of them have some sort of bug which prevents it from being usable. One of the main major problem many distros have is with sluggishness. I've tried Ubuntu, Mint, Fedora, Opensuse, PCLOS, Mageia and their derivatives but because of sluggishness, I hate to use them. Today, for example I tried SolusOS, and it has a problem on my hardware that I get lots of graphical artifacts all over the place, possibly beacuse of outdated drivers. And the graphics suck - Cardapio and window titlebars flashes a brilliant white everytime it loads, etc. It doesn't have compositing quite right. So SolusOS is the best distro in terms of looks, but in terms of user experience, the graphical issues make it the worst. I tried Chakra 2012.09 and I'm happy because I finally found a distro that flies on my hardware, even with the very heavy kde using open source drivers! It's the first distro I found that's actually very fast. But the problem is it's only available in KDE, which is a little too rich for me. So I'm on the search of a distro which is beautiful like SolusOS but without issues. I like Gnome Shell but I've found that it's annoying to do any useful work on it. I prefer a desktop like Cinnamon or a very polished one like Solus, but one that is never sluggish. So please find me a Cinnamon desktop or better that is as fast as Chakra because no other distro whether is Ubuntu or Suse or whatever runs well enough for me. All distros suck on my hardware. But Chakra is magical. I've not tried Arch based ones yet but would they be as fast as Chakara? I need a distro with gui installer and any package manager that has an interface. I don't care about rolling release as I'm not that experienced with linux to fix major breakages. so non-rolling will be fine also. Just I need something with such good hardware support like Chakra which is superfast because ubuntu and co don't cut it. Thanks. My hardwware is AMD 3.4Ghz x4, 4GB ram, on AMD 880G/Radeon 4250.

---

### Post by mips on 2012-10-12
Paragraphs make for easier reading and people will be more inclined to read your posts. I'm not reading that.

---

### Post by malspa on 2012-10-12
> **DisappearingOak said:**
> All distros suck on my hardware.

Just wondering: Do you have Windows on this computer? And if so, does Windows also "suck" on your hardware?

---

### Post by drawkcab on 2012-10-12
Maybe try CinnArch:  [http://www.cinnarch.com/](http://www.cinnarch.com/)

I guess you could also install Archbang and then add whatever dekstop you want.  It's getting easier to customize gnome shell via themes and extensions these days.

---

### Post by DisappearingOak on 2012-10-12
> **malspa said:**
> Just wondering: Do you have Windows on this computer? And if so, does Windows also "suck" on your hardware?

I had windows 7 for a while and it ran perfect. But I want to use Linux! Anyone have any experience with Manjaro, is it any good? The only thing I need is actually a gui package manager.

---

### Post by mips on 2012-10-12
> **DisappearingOak said:**
> I had windows 7 for a while and it ran perfect. But I want to use Linux! Anyone have any experience with Manjaro, is it any good? The only thing I need is actually a gui package manager.

I use Manjaro, it's still in beta stages though. It has no GUI package manager, the one they had got dropped because it was buggy. You can always install one from AUR if you want, [https://wiki.archlinux.org/index.php/Pacman_GUI_Frontends](https://wiki.archlinux.org/index.php/Pacman_GUI_Frontends)

---

### Post by malspa on 2012-10-12
If I was having those kinds of problems running Linux on my hardware, I'd either go to distrowatch.com, get info on a bunch more distros, and keep checking different ones out, OR start looking into some Linux-friendly hardware.

---

### Post by DisappearingOak on 2012-10-12
> **malspa said:**
> If I was having those kinds of problems running Linux on my hardware, I'd either go to distrowatch.com, get info on a bunch more distros, and keep checking different ones out, OR start looking into some Linux-friendly hardware.

I think there's also a problem with the open source drivers on 3d environments, at least on my gfx chip. It's not an uncommon chip though, I've seen a few laptops being sold with that chip. I bought this pc to run windows because I didn't know very much about linux back then. I think next time I'll be more careful. 

Ubuntu, Mint run on my computer, but there's this slight sluggishness at some places that's annoying. Fglrx is fast, but can be a little unstable at times, that's why I prefer not to use it. But I'm happy to see open source radeon run so fast with kde on Chakra, that must mean the new versions of the driver are very improved. I'm stuck on Solus's design though. It's very Windowsy in an XP-like way and I'm seeking support for the artifacts issue on their forums to see if it works out. Else, I'll try more bleeding-edge distros.

---

### Post by cpatrick08 on 2012-10-12
[http://distrowatch.com/search.php?ostype=All&category=All&origin=All&basedon=All&notbasedon=None&desktop=Cinnamon&architecture=All&status=Active](http://distrowatch.com/search.php?ostype=All&category=All&origin=All&basedon=All&notbasedon=None&desktop=Cinnamon&architecture=All&status=Active)

---

### Post by kiyop on 2012-10-13
If you hate sluggishness and if you want to use Cinnamon desktop, you can install Linux mint with Cinnamon desktop and remove unnecessary services.
[http://community.linuxmint.com/tutorial/view/114](http://community.linuxmint.com/tutorial/view/114)

---

### Post by cwsnyder on 2012-10-13
Your GUI which makes your desktop beautiful is also what makes your desktop crawl instead of run.  I would recommend #! (Crunchbang) or another OpenBox based distro, or Xubuntu or another Xfce based distro would be better than Cinnamon, Unity, MATE, or KDE.

---

### Post by Haghiri75 on 2012-10-15
have you tried Crunchbang Linux? a perfect debian with OpenBox. ;)

---

### Post by bklive on 2012-10-15
what you need is gentoo. I had the same artifacts on my X1270 netbook until I put gentoo on it but an Athlon64 1.2Ghz x1 processor is TOO SLOW for updates/anything. Surprisingly, even though my card isn't supported by fglrx, using ubuntu with fglrx solved the artifact problem and is surprisingly fast considering my hardware limitation. Your hardware specs should be lightning quick with any DE, so make sure your swap is activated and TRY before you BUY. run a liveCD for a few days first.

---

### Post by lykwydchykyn on 2012-10-15
If you're using Ubuntu or an Ubuntu derivative, you can always check if the Xorg-edgers PPA has a newer version of the video drivers you need.  You can also try a newer kernel from the kernel devs PPA.

You don't *have to* run a rolling release distro to get newer packages; most distros provide some means of obtaining bleeding edge versions of packages, you just have to learn how.

---

### Post by jj1two3 on 2012-10-20
I have installed Manjaro Linux and I love it. It is very quick and works like a charm. I would probably say that I will stick with it for awhile.

---

### Post by offgridguy on 2012-10-20
DisappearingOak; you are already getting a lot of advice here, I've got to admire anyone
who has tried as much stuff as you have. :)

---

### Post by black veils on 2012-10-22
you could use chakra, but install another gui (desktop environment) within, and see how it is. i would recommend xfce, its got options, and can be made to look like a lot of different things. but you could also try cinnamon etc too.

open the package manager or app centre that chakra has (dont know what it uses), and find the desktop environment you want to try.

---

### Post by mips on 2012-10-22
> **black veils said:**
> you could use chakra, but install another gui (desktop environment) within, and see how it is. i would recommend xfce, its got options, and can be made to look like a lot of different things. but you could also try cinnamon etc too.

open the package manager or app centre that chakra has (dont know what it uses), and find the desktop environment you want to try.

Chakra is geared towards KDE. If you want XFCE then look at Manjaro which is based on Arch with their own repos. They take the Arch stable repos and move them to their testing repos and once happy they move them to the Manjaro stable repos. Manjaro specialises in XFCE where Chara is focussed on KDE.

---

### Post by Old *ix Geek on 2012-10-24
Just a few days ago I installed [Bodhi Linux](http://www.bodhilinux.com) on an old laptop, and I'm THRILLED with its speed. This laptop was running KDE (Kubuntu 11.04) about as fast as frozen molasses, but now it's flying. :)

---

### Post by DisappearingOak on 2013-01-08
> **Old *ix Geek said:**
> Just a few days ago I installed [Bodhi Linux](http://www.bodhilinux.com) on an old laptop, and I'm THRILLED with its speed. This laptop was running KDE (Kubuntu 11.04) about as fast as frozen molasses, but now it's flying. :)

Hi guys,
It seems after a lot of searching, I've found why there's so much sluggishness and across so many distros even on my powerful hardware. It's beacuse of bugs. Apparently with KDE with desktop effects, there's a bug about a repaint issue that causes extremely jerky effects on my system. I reported it to the devs after finding out that with Show FPS effect on, animations were super-smooth but otherwise jerky. With Gnome Shell, 3.2 was fine, but in the newer Gnome Shells, there's a bug with the water animation that causes scale animation to be very jerky. That's been reported by others as well. I didn't want to use Enlightenment, it runs fast, but it has other problems with various bugs, even in the final release, which I have reported to devs. As for now, I'm using Linux Deepin 11.12.1 with 3d gnome shell, which runs absolutely smooth and fast. So I'm content for now and also waiting for their new version which features a brand new desktop environment which looks good from their preview videos.

---

### Post by arkanabar on 2013-01-08
I'm going to suggest ditching eye candy for functionality.  I like Ubuntu, but for the interface.  My preference runs towards ubuntu spins with lighter DEs or even just a window manager.  Right now, my recommendations for you are Xubuntu, Lubuntu, Madbox, or SalentOS, since you don't want to fool with e17 (truth be told, neither do I).  If Ubuntu and the like handle your hardware well, give those lighter interface spins a try.

---

### Post by leclerc65 on 2013-01-08
> **DisappearingOak said:**
> Hi guys,
It seems after a lot of searching, I've found why there's so much sluggishness and across so many distros even on my powerful hardware. It's because of bugs.
I had also been through this until my brother in law found out that my Motherboard's Bios was not up-to-date. My Quad-Core AMD 2200MHz per core show only 1100Mhz in the System Monitor.

---

### Post by fullmetalgerbil on 2013-01-09
I dunno, I saw some Distrowatch suggestions and that's always a good resource when you're poking around for distributions. You also might want to try [linuxquestions.org]("http://linuxquestions.org") as they have a pretty good review section and friendly forums.
I'm far from some kind of expert, however I've had great success with [AntiX]("http://antix.mepis.org/index.php?title=Main_Page") on machines with gronky hardware issues. Slackware, too is good in that way, but it's kind of a biting off a big piece to chew as far as configurimicating it all if you're just getting your flippers wet with Linux. But it gives you a lot of control over what you want in your installation.
Someone mentioned using Mint with the Cinnamon DE and stripping it out a bit, and that sounds good. I'd suggest that if you go with that, try the Mint 13 LTS, as 14 isn't their best release.
Sometimes, you know, it can all be a bit overwhelming-all the choices. There's a whole bunch of distributions, but (thankfully) NONE of them are going to give you an exact Windows user experience. The thing with Linux, and I'm sure there's like Authorities on The Subject who will disagree with me, but even in this day and age there's a certain degree of interplay-what used to be called "learning curve"-where it's like you can't just go out and "pick the perfect distro" all the time. You're not really supposed to be able to do that, exactly. It's still one of those things where you have to find what works well with your hardware...and then, you "make it perfect" by choosing what you want to use with it-KDE, MATE, Cinnamon, LXDE, Xfce, Fluxbox, Window Maker...like, whatever. Plus all the bijillions of packages and adaptations and tweaks and so forth you can take to it.
So, you know, you will find something that works well with your hardware. But beyond that it's on you to make it perfect for you.
Oh, and that person who was griping about your paragraph spacing...this is the first time in probably four or five years I've even been on this forum, and it's interesting that thay've let the grammar trolls suddenly run amok. For a second there I thought I was on the Debian forums.

---

