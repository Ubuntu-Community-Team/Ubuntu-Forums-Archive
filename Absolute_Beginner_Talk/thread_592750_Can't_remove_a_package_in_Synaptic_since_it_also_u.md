---
title: "Can't remove a package in Synaptic since it also upgrades it"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by erm4gh on 2007-10-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/156607](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/156607) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had recently upgraded from Thunderbird "2.0.0.6+nobinonly-0ubuntu1 (gutsy)" to "2.0.0.8~pre070122+nobinonly-0ubuntu07.10" . The latter version causes problems and I uninstalled it. However, it turns out Synaptic re-installed it because its the latest version. I then tried using force version to tell it to switch to the old version, but when I look at the details it says:
 
"mozilla-thunderbird will be downgraded
thunderbird (version 2.0.0.6+nobinonly-0ubuntu1) will be upgraded to version 2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10"

which defeats what I'm trying to do. I can't just completely remove all versions without nasty side effects such as breaking ubuntu-desktop. **How do I get force version to really work?**

The description of the mozilla-thunderbird package says: 
"[I]Transition package for mozilla-thunderbird rename. Package to ease upgrading from older mozilla-thunderbird package to the new thunderbird package.

This package can be purged at anytime once the thunderbird package has been installed[/I]." 

How do I purge it? Its real confusing since Synaptic lists mozilla-thunderbird as having a installed version of 2.0.0.8~pre070122+nobinonly-0ubuntu07.10  while stating the latest version is 2.0.0.6+nobinonly-0ubuntu1 (gutsy) and thunderbird is listed as having a installed version of 2.0.0.6+nobinonly-0ubuntu1 (gutsy) while having a latest version of 2.0.0.8~pre070122+nobinonly-0ubuntu07.10. When I run Thunderbird it states its version 2.0.0.6 (20071008) (the later date is used by the 2.0.0.8 package - there is a bug report about its version number).

---

### Post by caffienefree on 2007-10-26
removing ubuntu-desktop isn't a nasty side effect... you can safely remove it without negative side effects.

---

### Post by erm4gh on 2007-10-26
Can you elaborate? I know if I removed it I'd still have a working system but my impression is that it wouldn't look much like Ubuntu anymore.

---

### Post by SunnyRabbiera on 2007-10-26
nono, but you will have to upgrade packages manually though.

---

