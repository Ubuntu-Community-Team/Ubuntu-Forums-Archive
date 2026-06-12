---
title: "Linux distributions."
date: 2012-12-27
forum: Any Other OS
---

### Post by ArminasAnarchy on 2012-12-27
Hi all!

I've been using Linux for some time now, and have experimented with different distributions. At the moment, I'm running Kubuntu 12.10, but have tried Debian, Mint and Fedora.

I don't consider myself anywhere near "expert" level, but I have got a fair amount of experience with hardware and different OSes. I would love to be able to run Fedora, but what put me off was the RPM package manager. I like to think of Fedora as a little more advanced than Ubuntu, and consequently a little more powerful - which of course is appealing! Having the latest and greatest is also important, and Fedora does display that.

Specifically, moving to Fedora was a pain for the following reasons:

1) Pretty much all my more "in depth" experience is with Debian-based distros. Faced with a new syntax when it came to using the terminal, and new commands to learn to use yum, it was just too much of a bother. Plus, there's no purge command, and since I'm a little OCD, the idea of config files just sitting around gets under my skin.

2) The repository seems much smaller. I understand the whole free software thing, and actually, I really am supportive of it. I do however believe that I have to be pragmatic to get things done - and sometimes that means using proprietary software. You seem to be (largely) out in the cold if you want to use this, there's no handy scripts for installing Java (like the Duinsoft one), and in order to add flash, you're given the choice of three repos, (rpmfusion etc) with no reference to which you should pick and/or why.

So here's what would be ideal for me. I want to continue learning with Linux, and since I've started with Debian-based distros, I might as well continue to build on that foundation. Kubuntu suits my needs for the time being, but I've run out of things to play with in it, and I'd love to feel I had the power and functionality under Fedora, but in something based on Debian. I know there are various tools too, in order to install .deb files on Fedora, but it'd be nice to be able to use stuff like this natively - it seems a little messy just to lump something on top of an existing OS when there's probably a suitable alternative that's a little more stream lined.

What are people's suggestions? Also, since we're on the Ubuntu forums, I guess it makes sense to ask...why are you here, presumably running Ubuntu, and not utilising your suggestion? I'm looking for the pro's AND the con's folks!

---

### Post by MadmanRB on 2012-12-27
Well there are several families to consider for linux, there is debian based which Ubuntu is apart of.
Debian based linuxes use apt, though PClinux which is based on RPM uses apt too.
Redhat/fedora/fuduntu all use YUM, Yet another update manager as its backend and there are many fedora based distros.
YUM for me has always been slow compared to apt.
Then there is Mandriva/ROSA/Magia all using urpmi as the backend, urpmi seems okay but Mandriva packagers are over the place thanks to the fall of Mandriva.
Then there is openSUSE with zypper, and to be honest its the closest one to apt I have found to apt in terms of speed and ease of use.
Then there is slapt get, and porthole and many others.
Linux is very diverse and has no real universal standard for packaging, both a good and bad thing.

---

### Post by eternalnewbee on 2012-12-27
I've been using Ubuntu since 2005. I've tried several other variants and derivatives of Ubuntu as well as other distributions such as Bridge, Arch, Mageia, Manjaro, and Sabayon, but somehow I always go back to Ubuntu. I guess it's most familiar and easiest to configure for my needs.
The next Fedora will be released next month. I'd say keep experimenting until you settle down! ;)

By the way there's a very handy application called Remastersys, which enables you to make an iso file of your current system, so you won't have to reinstall all your favorite applications again.

Good luck.

---

### Post by sffvba[e0rt on 2012-12-28
If you are comfortable using Ubuntu (or a derivative) and it is working well for you stick with it for a while and become more proficient with it.

In the mean time install any of a number of virtualiztion solutions and play with as many distro's as tickles your fancy.  This way you will find more things you like as well as learn as you go and still have a system you understand for day to day usage.


404

---

### Post by offgridguy on 2012-12-28
In the short time i have been here, i have tried other distro's as well, but keep
coming back to ubuntu, as a newcomer i find it the easiest to use.
   I also like the unity desktop.  This is not to imply that ubuntu/unity is "the best"
simply my preference.

---

### Post by BBQdave on 2012-12-28
> **not found said:**
> If you are comfortable using Ubuntu (or a derivative) and it is working well for you stick with it for a while and become more proficient with it.

+1

Ubuntu 12.04 is a solid work horse that is reliable.

If you want the bleeding edge play of Redhat's Fedora project, check out Debian *Testing* and *Sid*  :)

---

### Post by UltimateCat on 2013-01-06
Hi:

Debian is a very solid and stable distro. Runs great for me!
You may not want to go with Debian /Sid as Sid is experimental and is unstable so I have heard from a few of the Debian men I talk to in Testing.

You could give Linux Mint a try. Most folks that like Ubuntu usually like Mint too-

Fedora is cutting edge if that's what you want just keep in mind that every few months you will have to do a fresh install of the next Fedora (18) or run the process of a 'preupgrade' 

Good luck!;)

---

### Post by drawkcab on 2013-01-06
It's good to play around with other distros.  Just run them on a separate partition or machine that you keep for testing.

A distro you might want to check out is Fuduntu which is Fedora Ubuntuized.  That way you can get a sense of what the developer has done in order to make Fedora more accessible.  

Another good project to play around with is arch.  Install Chakra, Bridge or Archbang if you want an easier installation at first.

I've never found SUSE, Slackware or Mageia all that great but again, if you want to learn, there's no harm in playing around with them to learn.

I keep coming back to Ubuntu and Debian mostly because it's really easy to find a solution to all the weird issues.

---

### Post by kiyop on 2013-01-06
> **ArminasAnarchy said:**
> Plus, there's no purge command, and since I'm a little OCD, the idea of config files just sitting around gets under my skin.
10 seconds searching with google gave me the following URL:
[http://unix.stackexchange.com/questions/8191/what-is-fedoras-equivalent-of-apt-get-purge](http://unix.stackexchange.com/questions/8191/what-is-fedoras-equivalent-of-apt-get-purge)
```
rpm -e NAME_OF_PACKAGE_TO_BE_PURGED
```By the way, about package managements, the following may help you.
[http://distrowatch.com/dwres.php?resource=package-management](http://distrowatch.com/dwres.php?resource=package-management)

> So here's what would be ideal for me. I want to continue learning with Linux, and since I've started with Debian-based distros, I might as well continue to build on that foundation.If you want to stick to debian-based distribution and if you need latest software, how about aptosid and siduction (although arch seems to have newer packages) ?

I do not think "latest" is "best".
If you want to learn and if you have tough possitiveness to learn by yourself, breakage (corrupt) of OS may teach you. ;) Good luck!

---

