---
title: "understanding the update thingy ^^"
date: 2005-05-19
forum: Absolute Beginner Talk
---

### Post by Shin Natsume on 2005-05-19
does the updater just fix security issues within ubuntu, or does it also upgrade my programs, for example if a new version of gaim comes out, it'll update that, or will it only provide security updates for it?

thanks ^^

ciao

---

### Post by JonahRowley on 2005-05-19
Ubuntu doesn't stray far from the release versions.  Normally, you'll only get security updates until the next release.  If you want bleeding-edge programs (and less stability), upgrade to breezy.  But at that point, all bets are off until October.

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=Shin Natsume] for example if a new version of gaim comes out, it'll update that, or will it only provide security updates for it?
[/QUOTE]

The second one. The new version might make unstable things unstable. Plus, if the old version got the newest program there would be little incentive for people to use the development version (and report bugs from it).

---

### Post by jobezone on 2005-05-19
[QUOTE=Shin Natsume]does the updater just fix security issues within ubuntu, or does it also upgrade my programs, for example if a new version of gaim comes out, it'll update that, or will it only provide security updates for it?

thanks ^^

ciao[/QUOTE]

If you go and check the repositories you have, for example you can do this in synaptic, you'll see there is a repository called updates. I guess this would be for important updates other than security fixes, but so far it has not been used (I think).

There is a group of people who have sought to solve that need, and created the backports project, which will give you recent versions of Hoary's packages, and even extra packages not available in any of Ubuntu's oficial repositories.

I've added the backports repositories to my repository list, and they are very well tested. Also, they won't conflict when in the future you decide to upgrade to the next version of Ubuntu (+- 5 months) or if in the meantime Ubuntu developers start using the ubuntu updates line.

There is a forum section here in ubuntuforums.org called Backports, and their homepage is [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) .

To make it simple, if you want to get backports and extra packages (all stable and tested), you would add these two repositories:
```

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restricted
```

---

### Post by Shin Natsume on 2005-05-19
thanks for the replies guys ^^

jobezone,  those 2 sites, there are alot of files and folders, im unsure what to do, could i get help at that backports forum?


thanks everyone ^^

ciao

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=Shin Natsume]thanks for the replies guys ^^

jobezone,  those 2 sites, there are alot of files and folders, im unsure what to do, could i get help at that backports forum?
[/QUOTE]


Yes, please ask questions there. I consider backports to be out of the range of the beginner forum.

---

### Post by jobezone on 2005-05-20
[QUOTE=Shin Natsume]thanks for the replies guys ^^

jobezone,  those 2 sites, there are alot of files and folders, im unsure what to do, could i get help at that backports forum?


thanks everyone ^^

ciao[/QUOTE]
To answer your question,
these are repositories of packages to be acessed by apt-get in your system, not for you to be acessing them yourself :). apt-get is the underlying program Synaptic uses. Synaptic is ubuntu's package manager (which some other distributions also use). You can add these repositories to apt-get through Synaptic.

Open synaptic (Package Manager) and go to the repositories (there's a entry in a menu somewhere, can't remember where now).
In there you can add the repositories I gave you, without the "deb", sorry. The "deb" part is used only if you manually add the repositories, by editing the /etc/apt/sources.list file.

 Anyway, these are the ones :
[HTML]http://backports.ubuntuforums.org/ubp hoary-backports main universe multiverse restricted
http://backports.ubuntuforums.org/ubp hoary-extras main universe multiverse restricted[/HTML]


If you are more interested in these affairs try searching the forum, looking at the backports home page at [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) , search the ubuntu's wiki [http://www.ubuntulinux.org/wiki/](http://www.ubuntulinux.org/wiki/) or even search for it in google (using ubuntu as one of the search terms).

---

