---
title: "Mint KDE to be Based on Debian"
date: 2011-07-11
forum: Any Other OS
---

### Post by CraigPaleo on 2011-07-11
I was just reading [here]("http://distrowatch.com/weekly.php?issue=20110711&mode=67#news") that the next Mint KDE edition will be based on Debian rather than Ubuntu. It appears they've been having trouble with the Kubuntu based edition. Interesting.

---

### Post by el_koraco on 2011-07-11
With their changes to the update methods in the Debian editions, I think that the project maintainer will have an easier time, since he'll be able to collaborate with the guys maintaining LMDE and the XFCE edition. I guess that would be like the prime motivation.

---

### Post by neu5eeCh on 2011-07-11
Is it possible to use PPA's with Debian? I've seen that it's possible, but not without fiddling, faddling and some breakage. At this point, the only reason I stay with Ubuntu (Xubuntu in my case) is because of the PPAs.

---

### Post by Noz3001 on 2011-07-11
> **VTPoet said:**
> Is it possible to use PPA's with Debian? I've seen that it's possible, but not without fiddling, faddling and some breakage. At this point, the only reason I stay with Ubuntu (Xubuntu in my case) is because of the PPAs.

Yeah, it is possible. All you have to do is import the keys

---

### Post by neu5eeCh on 2011-07-11
> **Noz3001 said:**
> Yeah, it is possible. All you have to do is import the keys

I thought there were other issues involved. Sometimes it's compatible, sometimes not... [Here's a sample]("http://blog.anantshri.info/howto-add-ppa-in-debian/") of the kind of help one finds...

---

### Post by Shpongle on 2011-07-11
Possible but not advised . Too many sites have debian /ubuntu packages when in fact they are only ubuntu packages. The dependencies they list are not available in debian or are not the same names so you have to go digging yourself. My point is they obviously dont check for debian compatibility and assume that ubuntu's packages will work.

---

### Post by BrokenKingpin on 2011-07-11
> **VTPoet said:**
> Is it possible to use PPA's with Debian? I've seen that it's possible, but not without fiddling, faddling and some breakage. At this point, the only reason I stay with Ubuntu (Xubuntu in my case) is because of the PPAs.
Same here. Even when you get the PPA installed, sometimes the packages are not compatible with pure Debian.

I also wish LMDE would create a mini.iso similar to the Ubuntu one. I love the core changes to LMDE, but the default install (of the Gnome or Xfce) is just too bloated and would prefer to build up my own desktop.

---

### Post by snowpine on 2011-07-11
I think Mint's done a huge dis-service to their user base by basing LMDE on Debian Testing instead of Stable. I've seen a lot of reports of update problems (to be expected with a Testing repo) and the latest rumor is LMDE is moving to a weird system of delaying updates by up to a month...

---

### Post by NightwishFan on 2011-07-11
> Is it possible to use PPA's with Debian? I've seen that it's possible, but not without fiddling, faddling and some breakage. At this point, the only reason I stay with Ubuntu (Xubuntu in my case) is because of the PPAs.

I would not recommend this at all. The software is compiled for Ubuntu library versions. The optimal solution is to grab the sources and recompile the packages yourself on Debian.

---

### Post by neu5eeCh on 2011-07-11
> **NightwishFan said:**
> I would not recommend this at all. The software is compiled for Ubuntu library versions. The optimal solution is to grab the sources and recompile the packages yourself on Debian.

Which is why I stick with Ubuntu derivatives. The beauty of the PPA is in having ones software automatically updated (if one cares about that sort of thing).

---

### Post by NightwishFan on 2011-07-11
> **VTPoet said:**
> Which is why I stick with Ubuntu derivatives. The beauty of the PPA is in having ones software automatically updated (if one cares about that sort of thing).

Certainly but PPAs have no guarantee of being around long or even working unless they have some dedicated or official maintainers. I found that it is best to only use one or two and only grab what you need from them. I would not explain the PPA as a feature to someone new to GNU/Linux.

---

### Post by CraigPaleo on 2011-07-11
I would think PPAs would be even harder to keep updated when trying to keep up with a rolling distro.

---

### Post by el_koraco on 2011-07-11
You can pin packages to Sid and experimental if you're into keeping up with the most recent versions in the book.

---

### Post by craig10x on 2011-07-12
> **snowpine said:**
> I think Mint's done a huge dis-service to their user base by basing LMDE on Debian Testing instead of Stable. I've seen a lot of reports of update problems (to be expected with a Testing repo) and the latest rumor is LMDE is moving to a weird system of delaying updates by up to a month...

It's not a rumor it is true...it's an option one can set up in the new version of mint update that was just designed to work better with debian (the original version is tweaked to work best with ubuntu based versions of mint)....

The idea is that the community using LMDE and Clem get to sort through the monthly updates first, find any problems, fix or provide solutions for any update that might have problems....

This way, the one's that like to tinker and experiment get to work the updates over first, and those who are less technically proficient (like myself) can install them after they have been checked over so we get a much more STABLE EXPERIENCE... 

Doesn't sound so bad now does it??? :)

---

### Post by snowpine on 2011-07-12
> **craig10x said:**
> It's not a rumor it is true...it's an option one can set up in the new version of mint update that was just designed to work better with debian (the original version is tweaked to work best with ubuntu based versions of mint)....

The idea is that the communtiy using LMDE and Clem get to sort through the monthly updates first, find any problems, fix or provide solutions for any update that might have problems....

This way, the one's that like to tinker and experiment get to work the updates over first, and those who are less technically proficient (like myself) can install them after they have been checked over so we get a much more STABLE EXPERIENCE... 

Doesn't sound so bad now does it??? :)

Re-inventing the wheel... there is already a branch of Debian that is very "stable." :) Respect to Clem, but he's going to burn out if he thinks he can do in one month, every month, what normally takes the entire Debian team 2 years.

---

