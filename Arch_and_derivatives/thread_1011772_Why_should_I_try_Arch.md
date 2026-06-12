---
title: "Why should I try Arch?"
date: 2008-12-15
forum: Arch and derivatives
---

### Post by Bachstelze on 2008-12-15
I've been happily running Ubuntu (with only a few Gentoo breaks) for a bit more than three years now. I keep hearing about Arch and how good it is, but I really can't think of any reason I would use it: my Ubuntu already does everything I want/need it to.

So, Arch users, enlighten me. :) Why do you like Arch? What does it have that Ubuntu doesn't?

---

### Post by kpkeerthi on 2008-12-15
pacman, light & fast, vanilla packages, binary + rolling release, easy to compile from source.

---

### Post by handy on 2008-12-15
For some it is what Arch does not have that Ubuntu (& others) do.

Simplicity too.

---

### Post by mips on 2008-12-15
First you could probably setup Ubuntu in a similair manner to Arch by using the miniISO or Alternate iso.

Rolling release is cool (for me) so you don't have to wait for a new release of the distro to get the new packages. Pacman, yaourt & AUR (then there is also ABS which I have never used) is the dogs you know what. Building packages is childs play compared to building debs if you ever have to go that route.

The simplicity is another bonus. The few config files Arch uses are very easy to get your head around. For me everything I ever tinkered with was in rc.conf. The few other files you basically only touch during setup and that is minimal editing.

Speed, for me Arch flies compared to Ubuntu.

It's one of those things where it just feels right, fits me like a glove. It's not for everybody as we all have different preferences as to what an OS should be like.

If you can do Gentoo then you will find arch very easy and I have used Gentoo before. If you like creating optimised installs you can even recompile your whole system from scratch with your flags and stuff.

All I can say is that you should give it a try, you never know as you might just like it and if you don't so what.

---

### Post by Bachstelze on 2008-12-15
Thanks for the answers, I guess I'll give it a go during the winter holidays... Are official KDE 4 packages readily available, by the way? The fact the KDE 4 is still hard-masked in Gentoo, which makes it a reall PITA to install it, is pretty much the only reason I'm running Ubuntu instead of it. Also, how is 64 bit support? Once again something that is sub-par in Gentoo...

---

### Post by Rumor on 2008-12-15
> **HymnToLife said:**
> I've been happily running Ubuntu (with only a few Gentoo breaks) for a bit more than three years now. I keep hearing about Arch and how good it is, but I really can't think of any reason I would use it: my Ubuntu already does everything I want/need it to.

Usually when someone asks this question, stating that what they are currently using is working fine for them or that they "can't think of any reason they would use it" I tell them not to switch. Certainly go ahead and try Arch in a virtual box session or on a spare computer, but don't switch.

I switched to Arch from Ubuntu back during the time of Dapper Drake. I switched because I use the proprietary nVidia drivers and each time the restricted headers updated on Ubuntu, I had to reinstall the drivers from a vc in order to boot. it was frustrating me and I went looking for something else. For me, it was compelling enough a reason to go looking for something else.

> **HymnToLife said:**
> So, Arch users, enlighten me. :) Why do you like Arch? What does it have that Ubuntu doesn't?

1. Arch is a rolling release. I always dreaded the release dates for the next Ubuntu. The upgrade process was not always smooth and I didn't enjoy re-installing the OS and spending the next couple hours tweaking settings and preferences. I like the small incremental steps in Arch and the ability to have my system be as bleeding edge as I want.
Arch has no defaults. There is no default web browser, no default desktop environment or window manager, no default music player, etc. After the base install, you build your system using the applications you choose, running the daemons you choose and nothing more.

2. Arch's community is great as well. The Ubuntu community is very nice, but it is so big and so active that it is easy to get lost or feel overwhelmed. The Arch community is considerably smaller but the users are friendly, knowledgeable and every bit as helpful.

3. The package manager, pacman, coupled with the Arch build System and makepkg is simply wonderful. With the tools Arch gives you, you can make your own packages if something is not in the repositories or in the Arch User Repository. Pacman will then install and maintain it for you, and you can share your PKGBUILD with other Arch users.

4. I think the biggest thing Arch gives me that i felt Ubuntu did not is control. Ubuntu was a great transition for me from Windows to Linux. It was sort of like a training ground where I learned to walk. When I was ready to drive, Arch was there to put the keys in my hands.

Try Arch in a virtual box session. If you like the customizability of Gentoo, you'll appreciate the simplicity of Arch.

---

### Post by mips on 2008-12-15
> **HymnToLife said:**
> 
Are official KDE 4 packages readily available, by the way?

Also, how is 64 bit support?


KDE 4.1.3 is in the repos. Not sure about KDE 4.2 but i'm 100% positive it is there somewhere. KDEmod 4.1.3 & 4.2(unstable repo) are in the kdemod repos. Keep in mind the unstable version does not have the locale files at the moment.

64bit support is good. All my stuff works with no effort. Flash is fine and I havent even tried the 64bit version yet. Also running bin32-skype & bin32-wine without hassles. There is icedtea for java browser plugin.

Edit: KDE4.2 beta see,
[http://bbs.archlinux.org/viewtopic.php?id=59759](http://bbs.archlinux.org/viewtopic.php?id=59759)
[http://bbs.archlinux.org/viewtopic.php?id=44507](http://bbs.archlinux.org/viewtopic.php?id=44507)

To search for binary packages look at: [http://archlinux.org/packages/](http://archlinux.org/packages/)
To search for pkgbuilds look at: [http://aur.archlinux.org/](http://aur.archlinux.org/)  Use Yaourt for these as the syntax is the same as pacman and it will do everything automatically for you. Read AUR guide first for globally setting your flags & stuff if you want to.

---

### Post by Nepherte on 2008-12-15
The primary reason for me to switch to arch is the rolling release model. I didn't want to reinstall ubuntu every six months (or update it, come to the conclusion something is broken and that I still have to reinstall. This doesn't always have to be true for other users of course).

---

### Post by handy on 2008-12-15
The new 64bit Flash is working really well.

---

### Post by crimesaucer on 2008-12-15
> **mips said:**
> 64bit support is good. All my stuff works with no effort. Flash is fine and I havent even tried the 64bit version yet. Also running bin32-skype & bin32-wine without hassles. There is icedtea for java browser plugin...


The new 64bit version of the flashplugin is SOOOOOOOO much nicer than the nspluginwrapper. I don't use skype and wine so I'm not sure about anything with those apps..... 


..... but if there isn't a reason why you have kept your old nspluginwrapper, then you should upgrade to the new: [http://aur.archlinux.org/packages.php?ID=21601](http://aur.archlinux.org/packages.php?ID=21601)

---

### Post by smartboyathome on 2008-12-15
The primary reasons for me are:

1. makepkg is such a breeze to make packages for from a package maintainer's perspective. If you got some basic knowlege of scripting and compiling, then you can create a package on Arch. Debian requires a lot more work to be invested into trying to package for it.

2. AUR offers a very extensive list of packages which you can use. Many of these packages are maintained by the community, and packages can be "adopted" or "orphaned" easily so others can maintain them.

2. Rolling release keeps me up to date. I like that Arch is up to date, but not as unstable as, say, the development versions of Ubuntu.

---

### Post by Dr Small on 2008-12-15
The rest of the ArchLinux users here at Ubuntu Forums have given very good reasons for switching to Arch. But for me, it was just meerly for the adventure.

I had been running Feisty Fawn with IceWM and XDM, but still didn't feel light enough or that I was learning anything further about my system. I had heard alot about Arch from K.Mandla, so I could give him the credit for introducing me to Arch.

My previous system "just worked" but felt bloated and unorganized. So I installed Arch and actually began learning more of linux by starting from scratch and building the system up. Really, it wasn't difficult as others had foretold it to be. I followed the Beginners Guide and it was a very fun experience.

So here is another user that had a desktop that "just worked" the way I wanted it to, and then jumped on the Arch bandwagon for the adventure and ride. Now, I can't say that I would ever use Ubuntu again.

---

### Post by crimesaucer on 2008-12-15
I switched to Arch over a year ago (Duke/Don't Panic versions) because I had heard about how fast it was and because I wanted to see what i686 felt like compared to i386. I also wanted to challenge myself to the install. (which seemed a bit more difficult then..... maybe it was the old xorg and my old crappy Intel Celeron M...... it's so much easier now with my AMD Turion 64X2 and nvidia GeForce 7150M nForce 630M)


Then after installing it and configuring everything, I had learned so much more about Linux than I had been required to know when using xubuntu for the previous year..... plus it really was faster.


The funny thing about Archlinux is that I still am learning more about Linux everyday..... and I really appreciate the things like FTP installs, AUR/ABS PKGBUILDS, pacbuilder using C[XX]FLAGS/MAKEFLAGS, and the very well written Arch Wiki pages and AUR/Forum posts.

---

### Post by chucky chuckaluck on 2008-12-15
it's what all the cool kids are using.

---

### Post by crimesaucer on 2008-12-15
> **chucky chuckaluck said:**
> it's what all the cool kids are using.

it'll make you feel good good good good........

---

### Post by smartboyathome on 2008-12-16
> **chucky chuckaluck said:**
> it's what all the cool kids are using.

I thought all the cool kids were off using BSDs? :p

---

### Post by mips on 2008-12-16
> **crimesaucer said:**
> 
..... but if there isn't a reason why you have kept your old nspluginwrapper, then you should upgrade to the new: [http://aur.archlinux.org/packages.php?ID=21601](http://aur.archlinux.org/packages.php?ID=21601)

No reason really, just lazineess I suppose :) My flash works fine so I'm not to bothered to upgrade to the 64bit version. Part of my laziness stems from the fact that I will be doing a fresh install soon, I want to install Chakra when it comes out which is hopefully soon, I just hope there is a x86_64 version else my waiting will be in vain. Alternatively I will just rearrange my HD's and reinstall Arch + KDEmod 4.2 as my pc is full of crap right now :)

---

### Post by crimesaucer on 2008-12-16
> **mips said:**
> No reason really, just lazineess I suppose :) My flash works fine so I'm not to bothered to upgrade to the 64bit version. Part of my laziness stems from the fact that I will be doing a fresh install soon, I want to install Chakra when it comes out which is hopefully soon, I just hope there is a x86_64 version else my waiting will be in vain. Alternatively I will just rearrange my HD's and reinstall Arch + KDEmod 4.2 as my pc is full of crap right now :)

I was lazy for a while after they first announced the release of the 64bit flashplugin. Then I finally did it and it took about 1 minute to un-install the old nspluginwrapper and then install the new flash64 plugin.


Before I installed the new 64bit flashplugin I had thought that the web-designers of certain sites had written their pages like crap, but it really was the nspluginwrapper that made sites like NBA.com look broke.

Try this link with your nspluginwrapper and see what I'm talking about: [http://www.nba.com/](http://www.nba.com/)


Notice the navigation bar at the top where it says "Teams" "Players" "Scores" etc..... with the old lib32's and nspluginwrapper the drop down menus would appear behind the NBA scoreboard that's underneath the navi bar. I noticed other sites with similar things fixed.


Even if you don't change to the new plugin until you do a new install, check out that site and see if it also has broke menus for you.

---

### Post by meho_r on 2008-12-16
"Rolling release" was enough for me. I just installed Arch in VBox and it was kinda fun :) Man, what a tabula rasa :D I like it. Not sure if it will become my main OS (which is Ubuntu at this time), but I definitely will tinker with it and learn. And then... well, who knows ;)

---

### Post by RiceMonster on 2008-12-16
> **kpkeerthi said:**
> pacman, light & fast, vanilla packages, binary + rolling release, easy to compile from source.

Sums it up perfectly.

But really, if Ubuntu works perfectly for you, you don't *have* to switch. That said, trying Arch is always a good idea :).

---

### Post by SomeGuyDude on 2008-12-16
1) The "bottom up" approach really makes the system "feel" different. Instead of installing the system and then purging what you don't want, all that's there is what you install. It feels very intimate and you end up with the feeling that your system is your system, period.

2) Rolling release is pretty dang awesome. Not just for convenience in general, but because if something snaps (see my thread) it's quite obvious what the culprit is. No more "Intrepid is a step down", you know exactly what package has problems, you can downgrade a single package and not worry about it for a while.

3) AUR, specifically Yourt, is just magic. If you ever got annoyed with finding stuff on getdeb or installing various independent repos, AUR will be your saviour. I have not compiled ANYTHING from source in Arch so far, whereas with every other distro I had a few things that needed compiled from the get go.

It'd be nice if Arch has a synaptic-like GUI for things instead of using the web interface, but that's really the only complaint I have.

Yes, I was horrendously angry at the broken Xorg and I maintain that letting that package into testing was a bad idea considering the havoc it wrought on things seemingly by design (as opposed to malfunctioning code). Updates shouldn't necessitate a complete re-do of configuration files because syntax and parameters have changed, but mad as I was it's a minor thing considering the overall experience, even if it did briefly inspire me to try Intrepid. :lol:

---

### Post by chucky chuckaluck on 2008-12-16
> **smartboyathome said:**
> I thought all the cool kids were off using BSDs? :p

[IMG]http://mandatemedia.typepad.com/photos/uncategorized/2007/07/10/homer_doh_2.jpg[/IMG]

---

### Post by meho_r on 2008-12-16
> **RiceMonster said:**
> 
But really, if Ubuntu works perfectly for you, you don't *have* to switch. That said, trying Arch is always a good idea :).

The thing is it doesn't work perfectly. It works, but here and there are glitches. It takes about half of a minute to get from login screen to usable desktop (not sure if it's Gnome or Ubuntu issue; with or without Compiz it's same), there is a dozen of broken packages in repos (that can't be removed or repaired, so one needs to edit some .postinst, .preinst. postremove... files manually which, at the end, doesn't solve the problem, just removes annoying warnings), instability in some cases etc. Although I like Ubuntu very much, I wouldn't mind "switching" to more stable and faster distro :) Maybe Arch is answer. We'll see...

BTW, which DE Arch users prefer/recommend? Is Gnome faster than with other distros?

---

### Post by smartboyathome on 2008-12-16
> **SomeGuyDude said:**
> It'd be nice if Arch has a synaptic-like GUI for things instead of using the web interface, but that's really the only complaint I have.

That was one of my problems, too, before I started using yaourt -Ss. I can search both the repositories and AUR with it, all easily.

---

### Post by mips on 2008-12-16
> **SomeGuyDude said:**
> 
It'd be nice if Arch has a synaptic-like GUI for things instead of using the web interface, but that's really the only complaint I have.

One word, Shaman!

I'm sure there are other GUI's out there but Shaman compares to Synaptic.

---

### Post by namegame on 2008-12-16
> **meho_r said:**
> 

BTW, which DE Arch users prefer/recommend? Is Gnome faster than with other distros?

Generally a fresh install of Arch + anything will be faster than most other Distros such as Ubuntu or Fedora.

What usually bogs a system down is all of the services/daemons running in the background that a lot of people don't know about and therefore don't use or even need. 

In most cases, it's hard to recommend a DE, as it really comes down to personal preference. Personally, I love plain Openbox. But almost any WM/DE in existence can be run on Arch quite well.

---

### Post by cardinals_fan on 2008-12-16
Some reasonably objective pros and cons:

+ Large, well-maintained repos
+ Minimal base system
+ Superb package manager
+ Excellent documentation and community
+ Vanilla packages

- Very up-to-date, which can lead to some breakage (if you time your updates it's usually no big deal)
- You really do have to update to the next version in the repos (unless you use a custom repo), since the rolling release model leaves older apps in the dust with no security updates

---

### Post by RiceMonster on 2008-12-16
> **cardinals_fan said:**
> - Very up-to-date, which can lead to some breakage (if you time your updates it's usually no big deal)

See, that's interesting, because to me, being very up to date is a plus. I like using the latest version of software. You're right that breakage can happen, but I don't mind. It's worth it, IMO. I've never experienced any huge breakage.

> **SomeGuyDude said:**
> I have not compiled ANYTHING from source in Arch so far

You sure? PKGBUILDS automate the ./configure && make process, so when you use the aur/yaourt, you're compiling from source 98% of the time ;).

---

### Post by Dr Small on 2008-12-17
> **RiceMonster said:**
> You sure? PKGBUILDS automate the ./configure && make process, so when you use the aur/yaourt, you're compiling from source 98% of the time ;).

That's what I was going to say. I do alot of compiling from the AUR :)

---

### Post by sujoy on 2008-12-17
one more plus is that making packages is really easy, so any package not in repo or AUR can be packaged right away and installed with the package manager. this kinda keeps the system clean since you can share it with others and uninstall it gracefuly too

---

### Post by smartboyathome on 2008-12-17
> **mips said:**
> One word, Shaman!

I'm sure there are other GUI's out there but Shaman compares to Synaptic.

Another word, gtkPacman!

Its a nice, light, GTK pacman frontend similar to Shaman, but it has a few less features (still really good and easy to use, though).

---

### Post by mips on 2008-12-17
> **smartboyathome said:**
> Another word, gtkPacman!

Its a nice, light, GTK pacman frontend similar to Shaman, but it has a few less features (still really good and easy to use, though).

I have Shaman installed but I only use it to browse packages on the odd occasion if I'm not sure what I'm looking for. Majority of the time I just use Yaourt.

---

### Post by SomeGuyDude on 2008-12-20
> **RiceMonster said:**
> You sure? PKGBUILDS automate the ./configure && make process, so when you use the aur/yaourt, you're compiling from source 98% of the time ;).

:lolflag:

I meant manually. I haven't downloaded any tarballs and run config scripts.

---

### Post by Xiong Chiamiov on 2008-12-21
> **kpkeerthi said:**
> pacman, light & fast, vanilla packages, binary + rolling release, easy to compile from source.

Well said.  While some people don't like the approach, because they feel that packages that haven't been tested thoroughly together won't work together, I've had many fewer problems using up-to-date vanilla packages.  Let the ones who know the program do all of the monkey-patching.

> **Dr Small said:**
> I had heard alot about Arch from K.Mandla, so I could give him the credit for introducing me to Arch.

And you were the one I heard about it from.  Since I really respect you, it got me to try it out during my distro-hopping.  No turning back now.

OP:
Pacman is quite amazing (featureful **and** fast!), and even more so with my chain of yaourt + powerpill + pacman-color.  Portage is pretty much the only thing that can compare, from what I've seen.

---

### Post by SomeGuyDude on 2008-12-21
The heck is powerpill and pacman-color?

---

### Post by namegame on 2008-12-21
> **SomeGuyDude said:**
> The heck is powerpill and pacman-color?

I got curious so I started looking around...

Powerpill looks to be a wrapper for pacman:

[http://xyne.archlinux.ca/info/powerpill](http://xyne.archlinux.ca/info/powerpill)

And pacman-color is in the AUR, looks like it does exactly what it says it does...give pacman colors...

[http://aur.archlinux.org/packages.php?ID=11827](http://aur.archlinux.org/packages.php?ID=11827)

---

### Post by Xiong Chiamiov on 2008-12-21
> **namegame said:**
> I got curious so I started looking around...

Powerpill looks to be a wrapper for pacman:

[http://xyne.archlinux.ca/info/powerpill](http://xyne.archlinux.ca/info/powerpill)

And pacman-color is in the AUR, looks like it does exactly what it says it does...give pacman colors...

[http://aur.archlinux.org/packages.php?ID=11827](http://aur.archlinux.org/packages.php?ID=11827)
Correct.  More specifically, powerpill uses a download manager called aria2 to allow you to download packages from multiple mirrors simultaneously.  It makes things quite a bit faster if you're downloading a decent amount of updates, and the developer is quite active, and very open to suggestions.

---

### Post by gjoellee on 2008-12-24
[COLOR=Red]You can install that following window/desktop managers:
[COLOR=Black]GNOME
KDE
Xfce
Openbox
Blackbox
Fluxbox
Dwm
Xmonmad
Ratpoison
Awesome
Enlightment
FVWM
After Step
Sawfish
Amiwmrc
The Common Desktop Environment
MWM
Window Maker
[/COLOR][/COLOR]WM2
SCWM[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]

---

