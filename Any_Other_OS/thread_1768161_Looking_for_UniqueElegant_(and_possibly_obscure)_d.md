---
title: "Looking for Unique/Elegant (and possibly obscure) distros"
date: 2011-05-26
forum: Any Other OS
---

### Post by manzdagratiano on 2011-05-26
Hi All,

I currently have a quintuple boot, with Ubuntu Natty, Arch, Debian Sid, Slackware-current, and Gentoo... I feel my thirst for messing with flavors of GNU/Linux has not yet been sated, and I am looking for more (more so now that summer is here and I have a ***little*** more time than normal). What I look for in a distro, before I install it, is:

1) if it is unique
2) if it is elegant

**Debian** was the first elegant distro I had seen (starting from a Knoppix LiveCD), and then came **Ubuntu**, which was Debian at the core, but was **not** merely a rebranding of Debian, contrary to what I used to believe in the early years. Ubuntu was the first distro I was able to tap all the powers of my laptop with, and I have stuck ever since. Its overall experience is very distinct from Debian to this day, as I can tell from the parallel Debian Sid install.

Then came **Arch**, elegant, simple, customizable, and offered me complete control. It's unique **pacman** was the first I saw that held its own against Debian's **apt**.

Then there was **Slackware** - simple, customizable, pretty much source-based if you wanted anything more than the plain Jane install. **pkgtools** and **Slackpkg** are very elegant.

Then there was **Gentoo** - a PITA to set up, but it was also very customizable, and **portage** is also very elegant.

Now it's time for more, considering I heard of **CRUX** GNU/Linux, which seems to be somewhere in-between Arch and Gentoo, and which Arch [s]derives[/s] inspires from. That is definitely getting a place.

I am at the moment looking at the following:

* **GoboLinux** (breaks away from the usual directory structure; elegant package manager)
* **Sorcerer/Lunar/Source Mage** (spells and a grimoire?!!! I am sold!)

I will soon also mess with FreeBSD in a VM, but definitely not as a dual install. Also, the time for Debian GNU/HURD and Arch GNU/HURD is coming near.

I would like to know if I am missing any supremely elegant distros, which have their own unique philosophy. Therefore, for such an OS, I would like to see the following criteria specified aside from the aforementioned (please sell me on it!):

1) The distro should have (at least somewhat of) an **active development** background at the moment - i.e., it should not be dead. I would like to **avoid derivatives** **that do not have their own unique experience** if the original still exists (for instance, Mint will always be a no-go for me. Same reason I use Blackbox instead of Fluxbox/Openbox).

2) The distro should have some kind of **package manager** + repository - I am **not** in the mood for ./configure and then hunting for dependency resolution. **OR**, it should have a tool, like sbopkg in Slackware, which is capable of hunting down the source from its original location, compiling it into a package, and installing. (GoboLinux's '**Compile**' is similar I believe).

3) **No rpm**-based distros please (respectfully to Fuduntu, which really seems promising). There is really no logical reason for this, except that I have had horrible past experiences with Red Hat and then Mandriva before Debian, and I disliked Fedora from the start. I thought I would like to try it again when Fedora 14 Laughlin was out, but there is nothing there that I found desirable for myself (my personal taste of course; I am sure it is excellent for those who like it). I have never tried OpenSUSE, and I don't think I ever will (again, ease of use is not what I am after). I do know things with rpm have changed humongously, but I still have the bad aftertaste in my mouth (Interestingly enough, the Wikipedia page for a [list of all Linux distros]("http://upload.wikimedia.org/wikipedia/commons/9/9a/Gldt1009.svg") lists Suse as deriving from Slackware - I wonder how).

Any takers? Also, could someone advise me which of the three - Sorcerer/Lunar/Source Mage I should consider? I thought Sorcerer was dead, but it has been resurrected and its homepage has a 2011 installer out.

I have tried **dyne:bolic** in the past. Very elegant, but not very customizable, and installing new stuff was not cool in it (trying to install hplip required me to hunt down some 20 dependencies!!!).

---

### Post by MBybee on 2011-05-26
I'd recommend you try PC-BSD (live CD or VM) and OpenBSD - definitely elegant.

FreeBSD is not. It's an amazing OS (one of my top faves), but elegance? Not really. It's a bulldozer with a tutu.

---

### Post by manzdagratiano on 2011-05-26
> **MBybee said:**
> I'd recommend you try PC-BSD (live CD or VM) and OpenBSD - definitely elegant.

FreeBSD is not. It's an amazing OS (one of my top faves), but elegance? Not really. It's a bulldozer with a tutu.

Thank you! I just had a few scraps here and there to pick one of the *BSD's, and FreeBSD seemed to be the most popular; but now I have a concrete opinion to pick one by!

---

### Post by MBybee on 2011-05-26
Have fun, let me know if you hit issues. It's quite a bit different from Linux.

---

### Post by el_koraco on 2011-05-26
Foresight Linux. It's a rolling release distro, with a unique and new package management system (rpm done right, as it's sometimes pointed out), and is obscure enough to satisfy the needs. The package manager, conary, i sussposed to have a very stable rollback feature, which I guess is the most useful thing when you do a rolling release model.

---

### Post by wolfen69 on 2011-05-26
> **el_koraco said:**
> Foresight Linux.

I tried it for a bit a while back and thought it was pretty good. I may have to revisit it in vbox.

---

### Post by boydrice on 2011-05-26
> **MBybee said:**
> I'd recommend you try PC-BSD (live CD or VM) and OpenBSD - definitely elegant.

FreeBSD is not. It's an amazing OS (one of my top faves), but elegance? Not really. It's a bulldozer with a tutu.

Curious, why would you recommend PC-BSD but not FreeBSD?  PC-BSD is just basically FreeBSD preconfigured.  I have found FreeBSD and its Ports system to be very clean and well implemented.

---

### Post by boydrice on 2011-05-26
I know the OP said no RPM distros but if you want obscure how about PLD Linux?  If I recall correctly one of the main Arch Linux guys ran it for a while before creating Arch.
[distrowatch.com/table.php?distribution=pld]("distrowatch.com/table.php?distribution=pld")

---

### Post by jeduffey on 2011-05-27
I would be very happy to see more work done on DreamLinux.  v3.5 was good, but v4 was looking to be much better. However the current downloadable ISO is flawed and it breaks to easily in its current beta version.

DreamLinux is meant to be as easy on the hardware like Puppy, easy on the user like OS X, and easy on installing new programs like Ubuntu. It would be my default OS for handing out older refurb hardware, if it weren't in full pause mode.

---

### Post by MBybee on 2011-05-27
> **boydrice said:**
> Curious, why would you recommend PC-BSD but not FreeBSD?  PC-BSD is just basically FreeBSD preconfigured.  I have found FreeBSD and its Ports system to be very clean and well implemented.

That's precisely why.

FreeBSD is my preferred distro - but it's not elegant. Especially not the atrocious 1990s era ncurses based installer, the obscure disk partitioning methods, and the fact that it dumps you at a CLI with no idea at all how to install a GUI. 8.2 is actually worse in these respects than 7.x was, since those at least had the X User package that gave you the option of an instantly usable machine.

Ports are completely alien to most Linux people, while pkg_add and PBI are much more intuitive. You tell me which is more elegant - "make install clean" KDE, wait 4 hours, answer random prompts that pop up in the middle asking truly obscure technical details (Multi-threaded Perl? Which audio subsystem? etc) or pkg_add -r kde4?

PC-BSD gives you a really nice graphical installer that works, disk partitioning that is intuitive, and a preconfigured KDE 4 desktop with Firefox that even has working Flash. Sound, video, it all works. No Xorg -configure mess, no figuring out OSS, none of that.
Even OpenBSD is better at it than FreeBSD. OpenBSD asks you one question about X, then just gives you a working (but spartan) X desktop.

---

### Post by manzdagratiano on 2011-05-27
Very excellent suggestions so far... I will definitely give Foresight Linux a shot! (Though not with Gnome/KDE/Xfce - have Ubuntu/Debian/Arch for those).

Out of the BSD's I am leaning at the moment towards FreeBSD - PC-BSD is derived from it, and even though it is easier to handle, it seems like FreeBSD will give me the true grit and grime of BSD, even if it is a little masochistic like Gentoo. OpenBSD seems like it is a little too secure by default for my taste (reminds me of Fedora's default SELinux policies); and moreover FreeBSD seems to be the best compatible with all kinds of software. But maybe I will install OpenBSD alongside as well. VMs never hurt anybody :)

PLD seems to be quite interesting - I did not know it existed. I will get to it if I can swallow my rpm allergy.

Anybody have any idea about Dragora? Paldo and SliTaZ seem interesting as well.

---

### Post by fuduntu on 2011-05-27
> **manzdagratiano said:**
> PLD seems to be quite interesting - I did not know it existed. I will get to it if I can swallow my rpm allergy.

As someone that spends a lot of time maintaining both, rpm > deb. ;)

---

### Post by boydrice on 2011-05-27
> **MBybee said:**
> That's precisely why.

FreeBSD is my preferred distro - but it's not elegant. Especially not the atrocious 1990s era ncurses based installer

Ports are completely alien to most Linux people, while pkg_add and PBI are much more intuitive. You tell me which is more elegant - "make install clean" KDE, wait 4 hours, answer random prompts that pop up in the middle asking truly obscure technical details (Multi-threaded Perl? Which audio subsystem? etc) or pkg_add -r kde4?



I think we have very different ideas of elegant.  I think ncurses installers like sysinstall and the Slackware installer are elegant.

I think typing "cd /usr/ports/x11/kde4 && make config-recursive install clean" is pretty cool.  This way all the options are able to be selected upfront before the compiling starts.

---

### Post by xaegis on 2011-05-27
[http://haiku-os.org/](http://haiku-os.org/)

I've been meaning to look in on this project os for a while now. Seems pretty elegant and it is based on BeOs.
I dont have any real experience with it though.

---

### Post by manzdagratiano on 2011-05-27
> **boydrice said:**
>  I think ncurses installers like sysinstall and the Slackware installer are elegant.


+1 :)

I actually loved the Debian curses installer, and I also love the Arch installer. In fact, a GUI installer kind-a makes me sweat. The best installers are the kind where the CD boots up into a working minimal Linux, and then you run a setup script to install stuff. The extreme is Gentoo - there is no such script; you boot the Linux, and then build the system step by step - awesome! This way, one has extreme flexibility and power while installing the system. A graphical installer just gets in the way.

---

### Post by MBybee on 2011-05-27
> **boydrice said:**
> I think we have very different ideas of elegant.  I think ncurses installers like sysinstall and the Slackware installer are elegant.

I think typing "cd /usr/ports/x11/kde4 && make config-recursive install clean" is pretty cool.  This way all the options are able to be selected upfront before the compiling starts.

I think we definitely do :)
I consider the OpenBSD installer elegant - even though it's very much so CLI. It's not GUI vs non-GUI, it's 'big ugly mess because there's no other way' vs 'big ugly mess because we don't feel like making it any better'.

---

