---
title: "error message: wine update not authenticated"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by malnitz on 2007-01-01
Hi

Ubuntu tells me that one update is ready, but when I try to install I receive the following error message (see also the attachment):

"You are about to install software that can't be authenticated! Doing this could allow a malcious individual to damage or take controll of your system."

Is it wise to continue ?

I have installed wine via automatrix

Thank you in advance.

Malnitz

---

### Post by pseudonym on 2007-01-01
Software sources often (but not always) have a unique 'key' which lets Ubuntu know that the package being downloaded is actually the one available at the place where your system is getting it from (I've never heard of any bogus packages being distributed, though, but this 'signed repository' system was introduced to counteract the possibility).

You can safely add software sources to your system that don't use these keys if you consider them to be trustworthy nonetheless. Is this what you've done? did you add the wine repository to your list of software sources because you wanted to install a more recent version of wine than the one which ships with Ubuntu?

I just checked the [wine download page]("http://www.winehq.com/site/download-deb") and (tsk, tsk) they don't appear to have a security key for their repository (someone correct me if I'm wrong). But you can still go ahead and install their software - you just need to answer 'yes' to the question being asked.

One more thing - I don't use wine much these days but I always *uninstalled* any existing version first before updating to a newer one (leave your ~/.wine directory intact, though). When the newer version is installed, you should run 'wine-prefix create' in a console to tell your exisitng applications in ~/.wine that a newer version of wine has been installed.

---

### Post by oliverb on 2007-01-01
I'd just like to thank you guys for the reminder that there is a newer version of Wine than the one distributed with Dapper.

I'd previously tried a schematic CAD program and found the toolbars broke so badly it was close to unusable. The newer version fixes that.

---

