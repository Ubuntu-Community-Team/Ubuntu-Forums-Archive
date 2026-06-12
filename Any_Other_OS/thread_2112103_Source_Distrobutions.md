---
title: "Source Distrobutions"
date: 2013-02-03
forum: Any Other OS
---

### Post by Rukiri on 2013-02-03
For those that want to branch off into the realm of source there's really only 2 contenders in my book and that's Gentoo and Source Mage.

Source mage and Gentoo share a lot in common, there source distrobutions and both check for deps (sorcery imo is better than portage)  however bother are also different.  

Gentoo has global use flags where as Source Mage has local flags that you choose at the time of compiling your software (a much better choice here)  However portage also tracks live builds of the software and is thus named package-9999 but since sorcery is written in bash it wouldn't be too difficult to write a live build for source mage either.

Both have active communities, source mage has no forums but has an irc channel which is very active (just had a long discussion just 20 minutes ago from this post)

I've used both and will be reformatting my machine to use source mage,  the reason why I'm choosing source mage is that it's closer to linux from scratch where as... gentoo is a bit off and took a wrong turn.   

Both are great, but in the end if you want a more configurable system I'd choose source mage as you can't beat customizing a package locally and going through EACH package what you want built in.  Gentoo, it's use flags mean global configuration and will lead to bloat.  

If you do choose gentoo, have the minimal use flag enabled.

I'll also start the source mage google+ community, just so there's more interaction.
[http://wiki.sourcemage.org/](http://wiki.sourcemage.org/)
[http://wiki.sourcemage.org/FrequentlyAskedQuestions/DiffGentoo](http://wiki.sourcemage.org/FrequentlyAskedQuestions/DiffGentoo)

The lack of updates doesn't mean anything to a distro as it is source based remember, the github page is very active gilmuour os something like that.  

Source mage is probably the best distro for sysadmins as it offers a lot more control over gentoo, wish it was more popular but you know what they say if it's easy it get's popular fast.
Gentoo isn't an easy distro by any means but portage isn't the best package manager for linux, local configs will always be superior than global configs.

However what boiles down is that while source mage does offer a more local config per package version a global setup what matters is it's community and both are active.  But also, the install for source mage while source based is not like linux from scratch or gentoo but an install disk which atm uses linux kernel 3.0-r1  so while you can easily get an up to date system as it is source based and the packages are current but they don't offer live packages like gentoo does as it requires a live tarbal which git does not provide.

---

### Post by trent.josephsen on 2013-02-04
> **Rukiri said:**
> Gentoo has global use flags where as Source Mage has local flags that you choose at the time of compiling your software (a much better choice here)
Portage also supports per-package USE flags and the USE environment variable. Are you talking about something that can't be done with either of those? Nobody tries to set every USE flag globally.

---

