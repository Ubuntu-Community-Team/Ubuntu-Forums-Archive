---
title: "[SOLVED] How do I install Wine 0.9.48?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by yhack on 2007-10-26
Hi, wine 0.9.48 is out and I was wondering how to install it on 7.10 because it's not on the Synaptic manager.

Cheer,
Paul

---

### Post by Incense on 2007-10-26
Check this page, load the repo, and WINE should auto update.

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

### Post by misfitpierce on 2007-10-26
add the top key on that page in terminal
then enter and add gutsy line in terminal and enter
then sudo apt-get update
sudo apt-get install wine

Done deal

---

### Post by yhack on 2007-10-26
It seems 0.9.48 isn't on the thingy yet, but I'll wait until it is.

Thanks both of you.

---

### Post by [MD5]Hash on 2007-10-26
Yeah, I'm gonna have to confer, it's still installing 0.9.47, even after adding the key, updating the repository list.  Tried manually installing it through the Terminal and through the Add/Remove programs GUI.  Guess it's just not available yet.

Tried compiling it earlier but meh, errors and problems galore, I'll just hang tight for the repository to pick it up.

Hoping this lets me get Steam working...

---

### Post by Incense on 2007-10-26
It was just released today... so you got to give them a second.

> October 26, 2007: Wine 0.9.48 Released

    Wine 0.9.48 was released today, with the following main changes:

        * Still more fixes for regression test failures.
        * Much more complete cryptnet implementation.
        * WIDL is now able to generate the oleaut32 proxy code.
        * Lots of bug fixes.

   ** Binary packages are in the process of being built and it may take a few days for them to appear,** but the source is available now. You can find out more about this release in the announcement. Check out our download page for packages for your distribution.


---

### Post by superyounan1 on 2007-10-28
I still cant update to 0.9.48, maybe they forgot to make the deb?

---

### Post by nbound on 2007-10-28
> **'[MD5]Hash said:**
> Hoping this lets me get Steam working...
Steam has worked for ages, but make sure you follow the howto on the AppDB. (it needs an extra installed)

> **superyounan1 said:**
> I still cant update to 0.9.48, maybe they forgot to make the deb?
Packages are maintained by volunteers, they make new packages when they get around to it, usually its the day of release or the next. Sometimes longer, and very rarely a week or so. They'll get around to it when they have a chance :)

---

