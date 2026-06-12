---
title: "Looking for Gnome Shell 3.8 desktop with ease-of-use and polish as Ubuntu"
date: 2013-05-31
forum: Any Other OS
---

### Post by DisappearingOak on 2013-05-31
Hi, I had Gnome 3.8 installed with Xorg 14 on Ubuntu-GNOME (13.04) but it was missing features like pressure sensitivity and the lead dev told me that will only be available in Saucy Salamander as custom patches conflict with that feature. I'm going to try Saucy daily but I need something stable for everyday use also. I specifically need Shell with version 3.8 or higher as older releases had bugs that would make my system ultra-laggy. So is there any Ubuntu-like distro with great ease-of-use, just-as-good fontset, and easily installable multimedia support? Thanks.

---

### Post by monkeybrain2012 on 2013-05-31
Try Debian 7, comes with gnome-shell 3.4 but unlike the ubuntu implementation, it is very fast and smooth.

---

### Post by DisappearingOak on 2013-05-31
I did not want version 3.4. As I mentioned I specifically need 3.8 or higher due to bugs that are present in older releases of Gnome.

---

### Post by benerivo on 2013-05-31
> **DisappearingOak said:**
> I did not want version 3.4. As I mentioned I specifically need 3.8 or higher due to bugs that are present in older releases of Gnome.

Probably the [beta release of Fedora 19]("http://fedoraproject.org/get-prerelease"), that comes with 3.8.2. Not so much distro polish as Ubuntu, as it is more of a vanilla Gnome experience. You can add the [rpm -fusion repo]("http://rpmfusion.org/") for multimedia support, and the [infinality patches]("http://www.infinality.net/blog/infinality-repository/") for high quality font display.

---

### Post by r-senior on 2013-05-31
The [Ubuntu font](http://font.ubuntu.com/) can be installed on Fedora but you need the rendering tweaks that benerivo refers to to get it looking good.

---

### Post by buzzingrobot on 2013-05-31
3.8.2 is the latest, and last, release before 3.10.  You won't find newer that is also stable and Ubuntu-esque. 

You could go to the 3.9 developmental release.  Fedora Rawhide is probably the best bet for that, but it's sharp-edged testing.

---

### Post by Cheesemill on 2013-05-31
Arch has gnome-shell 3.8.2 in its standard repositories.

---

### Post by monkeybrain2012 on 2013-05-31
You can install G shell 3.8.2 in Debian sid using the experimental repo (then pin it afterwards and only check occasionally for missing pieces). But it is not very stable and not all the pieces are there. If you don't mind putting up with some inconsistencies and occasional dependency problems you can give it a try, but be careful about updates, if you check all the boxes like in Ubuntu something is almost guaranteed to break. But if you pin both experimental and unstable repos after installing gshell you are basically dropped down to testing, which is quite stable, probably better than Fedora 19 (beta)

---

### Post by benerivo on 2013-05-31
> **monkeybrain2012 said:**
> ...if you pin both experimental and unstable repos after installing gshell you are basically dropped down to testing, which is quite stable, probably better than Fedora 19 (beta) Debian testing is quite stable, but using experimental packages is a rough ride for the user - no polish at all and expect a few problems, especially with installing/upgrading. Fedora 19 beta is v close to what will be released as '19 stable', and should be fine. I've nothing against Debian (I use it everyday and haven't got Fedora installed) but it's rubbish for getting the latest desktop experience such as Gnome 3.8. I would also give some thought to Arch, which always gives the latest packages, but would require some setup and if anyone is looking for out-of-the-box 'polish' then i wouldn't recommend it -- although it's only an hours work to get an Arch desktop at least as good as any that is available.

---

### Post by monkeybrain2012 on 2013-05-31
> **benerivo said:**
>  Fedora 19 beta is v close to what will be released as '19 stable', and should be fine. I've nothing against Debian (I use it everyday and haven't got Fedora installed) .

I use F18 but with kde. One thing about Fedora is that some of the updates are pretty fresh (kernel 3.9.4 now from official updates comparing to raring still on 3.8.0.XX) , It may be possible to get gnome 3.8 in F 18 by enabling the rawhide repos.

---

### Post by buzzingrobot on 2013-05-31
F18 beta has been out for a couple of days.  I haven't noticed any problems with 3.8.2; works well here.  As always, read the release notes and the "Common Bugs" page.

If you install the beta, run "yum update" 'cause more than 300 updates will be waiting for you. Fedora is like that.

---

### Post by monkeybrain2012 on 2013-05-31
Don't know which version of gnome-shell Fedora 19 comes with, but just checked from Fedora 18 and found that gnome-shell 3.9.2 is in rawhide. I think rawhide is where packages from the next release will come. Would 3.9 be in Fedora 19 instead of 3.8? I don't know if installing that in Fedora 18 will break anything because my Fedora 18 is on KDE.

---

### Post by Cheesemill on 2013-05-31
3.9 is the next development release, I don't think it will be in the stable repositories of ***any*** distro.

The next stable version of gnome-shell after 3.8 will be 3.10.

---

### Post by BBQdave on 2013-05-31
As mentioned before, Fedora 19 with Gnome 3.8 is what you are looking for :)

A friendly warning: usually it takes a month, sometimes two, before all the bugs shake out of a new Fedora release - if you need stability. That said, Fedora is rock solid, if you install 2 months after release :D

You can cruise along nicely with Fedora, and have a fresh system, if you keep the above in mind.

---

### Post by kevdog on 2013-06-01
Ah -- gnome 3.8!!! Happy days --- so much that it makes me want to puke all over myself!!! Gnome 3.8 is terrible in my opinion,  I'm just wondering why you would want this version compared to 3.6?

---

### Post by BigSilly on 2013-06-01
Though I'm currently using KDE with it, I have in the past run openSUSE with Gnome 3 and found it to be way more stable and enjoyable than the Fedora equivalent. I don't know why openSUSE gets overlooked with its Gnome edition, but it seems to me to be the best. I recently tried out 12.3 with Gnome and its pretty awesome still.

---

### Post by benerivo on 2013-06-01
> **monkeybrain2012 said:**
> Don't know which version of gnome-shell Fedora 19 comes with, but just checked from Fedora 18 and found that gnome-shell 3.9.2 is in rawhide. I think rawhide is where packages from the next release will come. Would 3.9 be in Fedora 19 instead of 3.8? I don't know if installing that in Fedora 18 will break anything because my Fedora 18 is on KDE.

Every odd numbered gnome release (ie. 3.5, 3.7, 3.9) is a development version so won't get released by gnome as stable version -- and so won't turn up in distro releases. As Fedora 19 is already in beta, the software versions are frozen so it's going to get the [version listed in the repo database]("https://apps.fedoraproject.org/packages/gnome-shell").

---

### Post by BBQdave on 2013-06-03
> **DisappearingOak said:**
> ...I need something stable for everyday use... is there any Ubuntu-like distro with great ease-of-use, just-as-good fontset, and easily installable multimedia support?

Just a thought: bleeding edge usually includes a few bugs, so stability can be rough; Ubuntu Unity 12.04LTS is stable, smooth and fast :D

I was running F18 Gnome 3.6 happily until recent Linux Kernel update that crippled my hardware - 3 weeks on, and still no fix.

Thought I would give that old Ubuntu Unity 12.04LTS disk a try. Installed on my hardware, updated, and pleasantly surprised. A year later, and Unity 12.04LTS is rock solid and fast. I needed a good daily driver and it has the nice Ubuntu polish.

---

### Post by buzzingrobot on 2013-06-03
> **BBQdave said:**
>  Unity 12.04LTS is rock solid and fast... 

That's certainly been my experience. I find myself jumping in and out of Fedora. But, it does change often and significantly.  If someone's focus is on the *process* of staying current with a moving target, it's great (much like Arch or Sid). 

I'm not a Unity fan, so I put MATE and Plank on 12.04.  

I happen to be using Debian Wheezy at the moment.  As advertised, it's boringly stable. MATE works fine, but I find myself liking its implementation of Gnome 3.4.2. Sooner or later, something will annoy me and I'll move on.

(BTW, MATE fans really ought to look at the new Mint 15 release.  I'd likely be using it if only its default kernel wasn't panic happy on my hardware.)

---

### Post by DisappearingOak on 2013-06-04
I kinda like Unity (not the dash or global menus so much, but it's mostly fine.) Except for the fact that it is intolerably slow and buggy on my hardware. There was a time when I had problems in Gnome Shell and KDE also. But those desktops were fixed and the current versions run fine. But Unity is intolerably unusable. The dash takes half an hour to open (seemingly). It refuses to close if there is any video or anything behind it. The default animations make windows get stuck midway when minimizing, and the whole desktop hangs. This is not something that I want to use. Maybe when Unity 8 rewrite is here, it will be better, who knows. I've given up on the Gnome Shell paradigm also. It was starting to annoy me greatly and not being so much of a workspaces user, coming from windows, I found that it was not a very good DE for me. I'm using cinnamon on Mint 15 now, and I like it very much, especially with Void panel theme and Faience-mod window theme, it looks pretty neat. Unity will have to get it's act together, especially on performance issues.

---

### Post by BigSilly on 2013-06-04
Am now running openSUSE 12.3 64 bit with Gnome 3.8 from the stable repo. Have to say so far, despite a couple of known bugs, it's really really lovely. I'd have to recommend it to anyone looking for a great Gnome Shell experience. :)

---

### Post by monkeybrain2012 on 2013-06-04
> **buzzingrobot said:**
> That's certainly been my experience. I find myself jumping in and out of Fedora. But, it does change often and significantly.  If someone's focus is on the *process* of staying current with a moving target, it's great (much like Arch or Sid). 

I'm not a Unity fan, so I put MATE and Plank on 12.04.  


Not sure about Arch (will give it a trial soon), but I would say Fedora is much more usable and stable than Sid. All upgrades have been handled fine, except once when upgrading Nvidia driver killed my graphic because there was a version mismatch between akmod-nvidia and the driver, but that was from rpm-fusion rawhide (not enabled by default) and I should have read carefully before upgrading. Finally dropped to command lines and fixed it and everything was good again. But in sid I keep on getting into dependencies issues like upgrading package x will remove packages a, b, c, d--- z on an almost daily basis.Also if you use the free graphic drivers Fedora is a lot more up to date than Sid (but less bleeding edge than xorg-edgers) I used that in Fedora 17 for a whole year and never had any issue. I am quite impressed with Fedora actually, it manages to combine usability and bleed edge nicely. Also, since the packages in Fedora are usually so fresh there is no need to install many ppas just to get up to date like in Ubuntu.

Now that Ubuntu is going semi -rolling, I sure hope that it will handle updates more like Fedora than sid!

---

### Post by Mikeb85 on 2013-06-06
> **BigSilly said:**
> Am now running openSUSE 12.3 64 bit with Gnome 3.8 from the stable repo. Have to say so far, despite a couple of known bugs, it's really really lovely. I'd have to recommend it to anyone looking for a great Gnome Shell experience. :)

A week ago I tried to install Gnome 3.8 on openSUSE, but I couldn't get it working (X would crash every time).  Glad to hear they fixed it.

I'm currently on Fedora 19, which to my surprise (after hearing stories of Fedora crashing) is as stable as any version of any distro I've ever used, despite it's beta status.  Gnome 3.8 really is my favourite DE, by far.  I love the extensions, mission-control, the integration with various apps, etc...  Never understood the Gnome-Shell haters...

---

### Post by cincinnatus13 on 2013-06-06
^^ A lot of that was when it first started. Same with KDE 4 really. Just so much that was new and not a whole lot of things to take advantage of it.

I agree though. I'm running 3.8 on 13.04 and it is stellar. Much more fluid than 3.6 and despite missing one or two extensions, it is far and away better.

---

### Post by BigSilly on 2013-06-07
> **Mikeb85 said:**
> A week ago I tried to install Gnome 3.8 on openSUSE, but I couldn't get it working (X would crash every time).  Glad to hear they fixed it.

Hi. All I would say to that is, did you do the vendor switch to the stable repo in YasT? On the last openSUSE (12.2) I remember trying to update to a newer version of Gnome only to end up with a borked system because I didn't do the switch. Don't want to be teaching grandma to suck eggs, but if you weren't aware of it it's worth checking. :)

---

### Post by Mikeb85 on 2013-06-07
> **BigSilly said:**
> Hi. All I would say to that is, did you do the vendor switch to the stable repo in YasT? On the last openSUSE (12.2) I remember trying to update to a newer version of Gnome only to end up with a borked system because I didn't do the switch. Don't want to be teaching grandma to suck eggs, but if you weren't aware of it it's worth checking. :)

I did, and I also tried downloading a daily image as well.  Maybe I'll try again tonite...

---

