---
title: "webupd8 on Debian?"
date: 2013-08-07
forum: Any Other OS
---

### Post by SlugSlug on 2013-08-07
Hi, am playing with Debian Wheezy and found a package I'd like to install not available (minitube)

Is it safe to add the webupd8 ppa for Ubuntu to my sources.list or can the screw me up down the line?

Maybe someone knows a better debian repo?

---

### Post by slickymaster on 2013-08-07
Well, I've been using a WebUpd8 PPA for some time now, and never run into any issues with it. The packages in the WebUpd8 PPAs are always tested and are usually well packaged, unlike packages available in many PPAs available on Launchpad.

---

### Post by SlugSlug on 2013-08-07
Do you mean you run it on Debian or Ubuntu? I was happily using it on Ubuntu just not sure if it will mess up Debian?

---

### Post by slickymaster on 2013-08-07
Not in Debian, just in Ubuntu, but the PPA I'm talking about, WebUpd8 Java 7 PPA, works on Debian too since the package is just an installer and all you have to do is manually add the PPA repository to the Software Sources. It's tested on Debian Squeeze, but it should work with any Debian version.

---

### Post by cortman on 2013-08-07
Debian and Ubuntu are not binary compatible. Therefore I would have to recommend against using PPA's in Debian.
Unfortunately, no PPA equivalent exists for Debian that I am aware of. This is a grave deficiency, and is ultimately why I am currently running Mint instead of my preference (Debian).

---

### Post by slickymaster on 2013-08-07
> **cortman said:**
> Debian and Ubuntu are not binary compatible. Therefore I would have to recommend against using PPA's in Debian.
Unfortunately, no PPA equivalent exists for Debian that I am aware of. This is a grave deficiency, and is ultimately why I am currently running Mint instead of my preference (Debian).

You're correct, but the PPA I was referring to, and according to WebUpd8, is compatible. See this: [HOW TO INSTALL ORACLE JAVA 7 IN DEBIAN VIA REPOSITORY]("http://www.webupd8.org/2012/06/how-to-install-oracle-java-7-in-debian.html") and [Install Oracle Java 8 (both JDK8 and JRE8) in Debian]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"), but as I've said I never have tried it.

---

### Post by oldos2er on 2013-08-07
Moved to Other OS/Distro Support.

---

### Post by SlugSlug on 2013-08-07
thanks guys

---

### Post by CharlesA on 2013-08-07
I wouldn't use any PPAs that are for Ubuntu on Debian unless they specifically say they support Debian.

As far as not having minitube in the repos, you could always just use the [tarball]("http://flavio.tordini.org/minitube/minitube-sources").

---

### Post by angryfirelord on 2013-08-07
Building from source isn't too hard. Someone on the Debian forums posted a mini tutorial: [http://forums.debian.net/viewtopic.php?f=16&t=51504&start=45]("http://forums.debian.net/viewtopic.php?f=16&t=51504&start=45")

---

### Post by monkeybrain20122 on 2013-08-07
Just go to minitube's website, click the apt link for Ubuntu, I think it would work for Debian.

---

### Post by buzzingrobot on 2013-08-08
Minitube is available in Debian's testing and unstable repos.  I'd try from testing before I added an Ubuntu repo to Wheezy. 

The real danger of adding a foreign repo to any distribution just to acquire a single paackage is that, if that repo is left enabled, any subsequent software update may install packages from the foreign repo, not the distro's repos, and that is probably not a good thing. You can, in theory, get into things like pinning in your repo list, but that's always seemed a bit arcane to me.

If you do add the Ubuntu repo, and minitube installs correctly, the safest thing to do is to immediately disable the Ubuntu repo listing.  You won't get updates for minitube automatically unless you re-enable it, though, if that's a consideration.

---

### Post by SlugSlug on 2013-08-08
Think I'll add the testing repo and just un-hash it as and when needed - thanks

---

### Post by SlugSlug on 2013-08-08
Just a question on that - if I switch to testing repo and hash out stable will I end up on the testing release?

---

### Post by buzzingrobot on 2013-08-08
> **SlugSlug said:**
> Just a question on that - if I switch to testing repo and hash out stable will I end up on the testing release?

Essentially, yes. The next "apt-get update" and "apt-get dist-update" will pull from the testing repo.  Any package installation prior to that update/upgrade will pull dependencies from testing.

Here is the package page for mintube on testing. It shows all its dependencies. At the bottom are links to debs for different architectures: [http://packages.debian.org/jessie/minitube](http://packages.debian.org/jessie/minitube)

You've come up against a common issue with Debain Stable.

---

### Post by SlugSlug on 2013-08-08
ok thanks. added the repo and it installed fine

---

### Post by monkeybrain20122 on 2013-08-08
> **SlugSlug said:**
> Just a question on that - if I switch to testing repo and hash out stable will I end up on the testing release?

Instead of hashing and unhasng the sources.list you should instead manipulate /etc/apt/preferences Depending on the repository's pin priority you may or may not be able to install/upgrade from it even though it may be unhased in the sources.list

I am on Debian Sid but I have installed gnome-shell 3.8 from experimental. So when I don't need it anymore just pin it to the lowest priority (-10 n my case) and it wouldn't upgrade from it next time (and those packages won't show up in synaptic). I give it a higher priority (1000) if I want to install other stuffs not in sid. You can do that with other releases as well. So if you have stable and want to install something from testing, give testing a higher pripority (say 900) and save,and then apt-get update (I prefer to use synaptic) and then after you have installed your package just pin it to -10 and save, the next update will only come from stable. 

See attached (the .txt extension was added or it wouldn't upload to this site)

BTW, minitube is very easy to compile, see the file INSTALL in the tar ball, you don't even need to install. untar the tarball, cd into the folder minitube, then do qmake, make and that's it, the binary is in the subfolder mimitube/build and just click it to start. If you want to install it continue with "sudo make install". It is easier than fiddling with ppas and sources lists.

I also think the Ubuntu 12.04 deb would work in debian.

EDITED: Oh, I forgot, the easiest and most obvious way would be to grab and  install the .deb from whatever debian releases' archive without actually adding the release's repository to your sources.
[http://packages.debian.org/unstable/main/minitube](http://packages.debian.org/unstable/main/minitube) 
Just click to download the i386 or amd64. This would work because minitube doesn't have very complicated dependencies.

---

### Post by SlugSlug on 2013-08-09
Thanks for the info, but for me a quick sudo vi /etc/apt/sources.list and adding a hash is much quicker :)

---

