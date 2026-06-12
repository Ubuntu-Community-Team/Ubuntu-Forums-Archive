---
title: "Planning ahead for Feisty"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-04-05
Hey guys,

Not long now till Feisty comes out officially!
I'm planning ahead for install - as I'm still not particularly fluent with Ubuntu yet I figured I'd plan ahead and get some upgrade advice before I take the plunge and do it.

I've read I can use the following command:   gksu “update-manager -c -d”

According to the poster this will display a prompt to upgrade, et voila, it'll be done.
Is this the case?

Also, will upgrading cause any incompatibilities with documents/software? I've heard upgrading the linux core can cause software to stop working and numerous other niggles. 

Thanks!
G

---

### Post by Nechi on 2007-04-05
Looking forward for Feisty? So am I.
But I'm planning to do a completely fresh install of it, since there were so many issues related to upgrading from Dapper to Edgy.
Anyway, I'm allready trying the beta release on my laptop (an Acer Aspire 5043) and it seems to be working quite smoothly, except for one thing: I lost all system sound after an update. and all programs having to do with sound simply won't work. Amarok, Totem, etc, freeze at start. I hope that will be fixed in the final release.
It was so exciting to see the screensavers running on their best after installing the drivers for my ATI Radeon 200 card, though!
I think I'll wait till April 19 to try Compiz.
Anyway, I can't wait for it.

---

### Post by houstonbofh on 2007-04-05
'sudo update-manager -c -d' will upgrade you to the **development** release.  Once Feisty is official (14 days from now) a 'sudo update-manager -c' will upgrade you to the latest stable distribution.
You will also be able to download the 'alt-install' version of feisty, and run a script to upgrade without downloading everything.  (Handy for places with more than one system)

As to the stability of a development release...  Yes, it can be fun. :)  However, it is not called a 'stable' version for a reason.

---

### Post by insane_alien on 2007-04-05
just to be extra safe you could make backups of your important documents and files (if your a good computer user you'll already have this) but thats getting a bit paranoid. i upgraded using that a few weeks back and everything went fine. There should be no incompatabilities with any documents as formats don't change with every upgrade.

---

### Post by j2satx on 2007-04-05
> **houstonbofh said:**
> 'sudo update-manager -c -d' will upgrade you to the **development** release.  Once Feisty is official (14 days from now) a 'sudo update-manager -c' will upgrade you to the latest stable distribution.
You will also be able to download the 'alt-install' version of feisty, and run a script to upgrade without downloading everything.  (Handy for places with more than one system)

As to the stability of a development release...  Yes, it can be fun. :)  However, it is not called a 'stable' version for a reason.

If 6.10 was updated to 7.04 using this method..............what updates are downloaded from the update manager.......stable or development.

Thank you.

---

### Post by houstonbofh on 2007-04-06
'sudo update-manager' downloads patches for your current version.  Repositories are chosen in "Software Sources" by you.
'sudo update-manager -c' takes you from an early version to a later version if it is out.  Right now, if run from Edgy, it will do nothing more than just 'sudo update-manager.'
'sudo update-manager -c -d' will take you to a development version, if it is out.  If you are on an old version (Like Dapper) choosing -c or -c -d will still just take you up one version (to Edgy) at a time.
On April 19th, Feisty will go from development to stable.  There will be no development branch for a short time.

---

