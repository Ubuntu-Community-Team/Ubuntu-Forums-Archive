---
title: "Playing with OpenSuse 12.3"
date: 2013-03-15
forum: Any Other OS
---

### Post by oldos2er on 2013-03-15
So for fun I installed OpenSuse 12.3 on some spare hard disk space. I really like the way KDE looks "out of the box". The package manager's a bit of a challenge, but not too different from APT.

Overall seems like a nice OS.

---

### Post by QIII on 2013-03-15
I really like it.  The default KDE is pretty tasteful.

For updating via the terminal, zypper is really not that much different.

---

### Post by smellyman on 2013-03-15
Agreed.  Always want to give Openssue a good look.

but YAST for package management is drives me nuts.....

---

### Post by carl4926 on 2013-03-15
KDE is really the best option IMO
I already been using it over a week
And done several installs of Gnome and XFCE too. But I still prefer KDE

---

### Post by carl4926 on 2013-03-15
If anyone hits the know network bug, this might help
[https://forums.opensuse.org/english/get-technical-help-here/install-boot-login/484160-12-3-network-fix-post-install-announcement-sticky.html](https://forums.opensuse.org/english/get-technical-help-here/install-boot-login/484160-12-3-network-fix-post-install-announcement-sticky.html)

Another tip in KDE I find is don't install fetchmsfonts
It degrades the font quality
I use droid fonts and full hinting

---

### Post by oldos2er on 2013-03-15
> **QIII said:**
> For updating via the terminal, zypper is really not that much different.

Thanks, I will check that out. I prefer to do package management via terminal, if only because it's fast and efficient.

---

### Post by oldos2er on 2013-03-15
> **carl4926 said:**
> If anyone hits the know network bug, this might help
[https://forums.opensuse.org/english/get-technical-help-here/install-boot-login/484160-12-3-network-fix-post-install-announcement-sticky.html](https://forums.opensuse.org/english/get-technical-help-here/install-boot-login/484160-12-3-network-fix-post-install-announcement-sticky.html)


Yeah, I was surprised when my wired connection wasn't automatically picked up, but some futzing around in network manager fixed it.

Thanks for the tips.

---

### Post by BigSilly on 2013-03-15
Been trying out this release for the last few hours. Very much enjoying it so far. Had a couple of problems in the beginning. Got the aforementioned wireless problem that was easily fixed thanks to posts on their forum. Also had a problem with the touchpad synaptics module missing from the KDE System Settings. Didn't want to be stuck with tap to click, but luckily a zypper install synaptiks fixed that and the module now appears in System Settings. Thank God. I hate tap to click! Bit disappointed that these issues are in a final release, but I'll forgive it if the rest is solid. Which based on my probing so far it seems to be. On a pure cosmetic level I'm loving the new themes and effects, really swish and uniquely openSUSE. No problems with fonts here, but did have to tweak the settings a little bit. I was very pleased to find it mounted my Nexus 7 easily, which I was never able to do with past Ubuntu's (probably kernel related though).

But openSUSE seems to have all the software we need. If it isn't in the repo, it's in the OBS. I'm decided. It's going on the laptop over the weekend, and my desktop later on. Very nice release, but I'd like to see them polish the rougher edges for the final next time. But I won't complain. :)

---

### Post by carl4926 on 2013-03-15
Re: Nexus 7

See: [https://forums.opensuse.org/blogs/caf4926/using-android-mtp-device-nexus-7-kde-opensuse-12-3-128/](https://forums.opensuse.org/blogs/caf4926/using-android-mtp-device-nexus-7-kde-opensuse-12-3-128/)

---

### Post by orb9220 on 2013-03-16
Tempted to give it a whirl. But happy with my Mint 14 KDE backported to KDE 4.10.1 and running great. 
And no need for learning new package management? As standard synaptic & Ubuntu back-end.

So Is it Worth the effort for me to download and give it a whirl? Something given over my present KDE setup?
.

---

### Post by BigSilly on 2013-03-16
Well I can only tell of my own experience. I would say if you're happy as you are then there's no point switching. It can take time for you to get things set up as you like them, and can be often just be running to stand still.

However, it was a pressing matter for us to replace Ubuntu 12.04 on this laptop with another distro (lots of hangs and freezes sadly), and I'm happy to report that openSUSE 12.3 fits the bill so far. Got it all installed and set up, and so far so good. Got all the software installed that we need, and this is indeed a fast setup on the metal. Lovely quick boot and shutdown too. Very polished. The devs loved this one clearly, and I would recommend it to anyone. :)

Unless you're happy with what you got already. :D

---

### Post by carl4926 on 2013-03-16
> **BigSilly said:**
> Well I can only tell of my own experience. I would say if you're happy as you are then there's no point switching. It can take time for you to get things set up as you like them, and can be often just be running to stand still.

However, it was a pressing matter for us to replace Ubuntu 12.04 on this laptop with another distro (lots of hangs and freezes sadly), and I'm happy to report that openSUSE 12.3 fits the bill so far. Got it all installed and set up, and so far so good. Got all the software installed that we need, and this is indeed a fast setup on the metal. Lovely quick boot and shutdown too. Very polished. The devs loved this one clearly, and I would recommend it to anyone. :)

Unless you're happy with what you got already. :D

Yes
Boot and shutdown is rapid
Rock solid ATM

---

### Post by kurt18947 on 2013-03-16
Someone must be interested.  I downloaded via torrent and the uploads haven't stopped for several hours.

---

### Post by oldos2er on 2013-03-16
> **orb9220 said:**
> Tempted to give it a whirl. But happy with my Mint 14 KDE backported to KDE 4.10.1 and running great. 
And no need for learning new package management? As standard synaptic & Ubuntu back-end.

So Is it Worth the effort for me to download and give it a whirl? Something given over my present KDE setup?
.

There's a LiveDVD/USB option similar to Ubuntu's: [http://software.opensuse.org/123/en](http://software.opensuse.org/123/en)

---

### Post by BigSilly on 2013-03-17
> **carl4926 said:**
> Re: Nexus 7

See: [https://forums.opensuse.org/blogs/caf4926/using-android-mtp-device-nexus-7-kde-opensuse-12-3-128/](https://forums.opensuse.org/blogs/caf4926/using-android-mtp-device-nexus-7-kde-opensuse-12-3-128/)

Well it seems I spoke too soon with the Nexus. It mounted and presented it as an option in Dolphin, but you cannot move files to the device. It just hangs or gives you errors. However, following the comments on the blog you link to I've installed go-mtpfs and now it works great. Thought it worth mentioning here. I picked the package by polyconvex from the openSUSE Build Service, my only reasoning being the other package on OBS is listed as HTC. I'm sure there's nothing between them, but hey.

---

### Post by carl4926 on 2013-03-17
> **BigSilly said:**
> Well it seems I spoke too soon with the Nexus. It mounted and presented it as an option in Dolphin, but you cannot move files to the device. It just hangs or gives you errors. However, following the comments on the blog you link to I've installed go-mtpfs and now it works great. Thought it worth mentioning here. I picked the package by polyconvex from the openSUSE Build Service, my only reasoning being the other package on OBS is listed as HTC. I'm sure there's nothing between them, but hey.

Thanks for that
I'll look in to it

---

### Post by carl4926 on 2013-03-17
> **BigSilly said:**
> Well it seems I spoke too soon with the Nexus. It mounted and presented it as an option in Dolphin, but you cannot move files to the device. It just hangs or gives you errors. However, following the comments on the blog you link to I've installed go-mtpfs and now it works great. Thought it worth mentioning here. I picked the package by polyconvex from the openSUSE Build Service, my only reasoning being the other package on OBS is listed as HTC. I'm sure there's nothing between them, but hey.

OK
Just double checked the function of this on a machine which has followed the blog (not adding the file you suggest)
And it's working fine for me
Umm...

---

### Post by iamkuriouspurpleoranj on 2013-03-17
Just out of interest, why does OpenSUSE not have Eclipse and/or NetBeans in the repos? It must be the only mainstream Linux distribution for which this is the case. To have neither is quite remarkable. Is it not much used by programmers or something?

---

### Post by carl4926 on 2013-03-17
Netbeans is in the OBS

[http://software.opensuse.org/package/netbeans](http://software.opensuse.org/package/netbeans)

---

### Post by iamkuriouspurpleoranj on 2013-03-17
But isn't that like Arch's AUR? i.e. it's packaged by a member of the community or am I mistaken?

---

### Post by BigSilly on 2013-03-17
> **carl4926 said:**
> OK
Just double checked the function of this on a machine which has followed the blog (not adding the file you suggest)
And it's working fine for me
Umm...

Umm indeed! How odd. I wonder if you have a particular package or program installed somewhere else that is making the difference? Oh well, I'm just glad it's working OK now.

Does your other machine have the option to safely remove the Nexus available and working too? I don't have that on this laptop, in either Dolphin or the system tray.

---

### Post by carl4926 on 2013-03-17
> [COLOR=#000000]Does your other machine have the option to safely remove the Nexus[/COLOR]
No
Something needs working on I guess

---

### Post by kurt18947 on 2013-03-19
> **oldos2er said:**
> There's a LiveDVD/USB option similar to Ubuntu's: [http://software.opensuse.org/123/en](http://software.opensuse.org/123/en)

But be sure to download the correct .iso.  There is a dvd .iso that only offers install.  The .iso including a 'live' option is separate.

---

### Post by screaminj3sus on 2013-03-21
I just switched to opensuse 12.3 gnome recently, really liking it so far. Seems very polished and stable. My favorite thing is definitely the package management, zypper took a while to get used to but its the most robust package manager I've used, its dependency resolution and handing of upgrades from different repos and such is very impressive. I also love the OBS, there seems to be a lot of software available via OBS and community repositories, and the "one click install" is a nice touch. 

My issues with it are:

Quality control in the repositories could be a little better. There seems to be several "broken" packages in the repos. for example I installed smuxi (my favorite irc client) and either mono or the smuxi package in the repo is very broken, the application simply doesn't launch, and if I try and launch it via the terminal I get a mono error. I also had an issue with the gtk3-engine-unico package from the repo, it would cause gnome to crash when using a theme that used the unico engine. Strangely enough I've had no issues with packages from the OBS/community repos, only those packages from the official repos.

Policykit/permissions/groups could be configured better by default. by default you aren't even in the printer group, doing some tasks in opensuse like adding a printer will ask your password way too many times.

---

### Post by BigSilly on 2013-03-21
I've had more than my fair share of broken packages in the Ubuntu repos over the years, so I won't hold that against openSUSE! All you can do is report it and hope someone sees it.

I've seen quite a lot of criticism from new users of the package management. I think a lot of people add some extra repositories, and then panic a bit when the "de-installation" warnings hit. I can definitely understand this, as I've been in the same position and gone "huh?". It's actually a really robust approach and you just have to learn how it works. I tend to add a repo like Packman, and then perform a switch in Yast, so that the system knows I prefer packages from that repository. That way, the system doesn't throw up the errors, and if I decide to remove the repo I can just revert all the packages to the standard repositories and remove the offending one easily. I found that I couldn't do that with Ubuntu if I'd added a PPA or two. I had lots of problems a while ago when I added a Gnome 3 PPA and then tried to remove and revert it later.

It's horses for courses, but I've found that much like when I first started with Ubuntu, I have begun to learn a different way and am enjoying it. :)

---

### Post by MadmanRB on 2013-03-21
I am giving this a major shot, and overall pretty good.
The only issue is that I had loads of issues getting netflix working on it, sure converting wine-compholio is easy via alien and does work, but the links it creates often fail.
Dont know why, I had to manually make my links to windows firefox.

---

### Post by screaminj3sus on 2013-03-21
> **BigSilly said:**
> I've had more than my fair share of broken packages in the Ubuntu repos over the years, so I won't hold that against openSUSE! All you can do is report it and hope someone sees it.

I've seen quite a lot of criticism from new users of the package management. I think a lot of people add some extra repositories, and then panic a bit when the "de-installation" warnings hit. I can definitely understand this, as I've been in the same position and gone "huh?". It's actually a really robust approach and you just have to learn how it works. I tend to add a repo like Packman, and then perform a switch in Yast, so that the system knows I prefer packages from that repository. That way, the system doesn't throw up the errors, and if I decide to remove the repo I can just revert all the packages to the standard repositories and remove the offending one easily. I found that I couldn't do that with Ubuntu if I'd added a PPA or two. I had lots of problems a while ago when I added a Gnome 3 PPA and then tried to remove and revert it later.

It's horses for courses, but I've found that much like when I first started with Ubuntu, I have begun to learn a different way and am enjoying it. :)

Yeah at first I actually didn't like the package management, and thought I did something wrong when zypper presented me with dependency "conflicts". The "vendor change" stuff with opensuse's package management did confuse me a bit at first in particular, but after understanding how it works I've come to love it, zypper handles 3rd party repos and upgrades much better than apt. Its very nice to be able to do a "vendor change" to your preferred repo, so even if the 3rd party repo has older packages you can easily make the package manager prefer them. It also makes it very easy to "revert" packages from a 3rd party repo back to official packages, and works far better than ppa-purge in ubuntu. Zypper is very intelligent and its nice how it always presents you with multiple options to handle dependency "conflicts". I've really come to like it more than any other package manager I've used.

---

### Post by carl4926 on 2013-03-22
It's generally considered best to keep to a minimum the adding of repos above and beyond the standard + Packman, libdvdcss, (and either ATI/nVidia).
At least until you have some experience.
The OneClick experience is best avoided (It's not the best IMO)
If in doubt... ask first.

---

### Post by oldos2er on 2013-03-24
A bit off-topic, but I just learned today that the Opensuse forums can be accessed with a newsreader (NNTP). I've never seen this feature for any other Linux based web forums. Pretty cool.

---

### Post by carl4926 on 2013-03-24
> **oldos2er said:**
> A bit off-topic, but I just learned today that the Opensuse forums can be accessed with a newsreader (NNTP). I've never seen this feature for any other Linux based web forums. Pretty cool.
Quite correct
All forums actually: openSUSE, SUSE, Novell.....
It's very useful

---

