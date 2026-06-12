---
title: "Upgrading applications"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-04-28
I've got a genealogy program that I've installed using Synaptic. I'd like to upgrade it to the latest version, but the exact filename(s) given in the documentation don't appear on sourceforge, although there are two .deb files with "ubuntu" in the filename.

I'm planning to upgrade Ubuntu to Feisty soon - would I be better waiting to see if a later version is in the repositories?

And are software upgrades generally a complete re-install of the program, or does it vary according to the program?

TIA

---

### Post by orb9220 on 2007-04-28
> I've got a genealogy program that I've installed using Synaptic. I'd like to upgrade it to the latest version,


Always ask why to upgrade, Is it broken or has a new feature I need? Or makes it more stable?

I see people all the time in the windows and linux world updating all the time and breaking things. In fact it is a big chunk of my salary on having people to call me to undo their updating.

But this is the info on updating.

Well the packages in the Repo's are stable but usally of older versions.

Some go to the actual site to grab the latest versions which are .deb files and can be installed. And yes It will install over the old one.

If you go to their site and they only show a tarball .gz file than you have to do a manual install.

If it is a .rpm package than you will have to convert it to a deb package with a program called alien in the repo's. 

You will get vary degrees of success with converting a .rpm to .deb depending on dependecies and such as is generally not recommended.

Hope this has been helpful.

---

### Post by freesitebuilder on 2007-04-30
Thanks for that - I've updated now. My problem was that the tutorial is for the new version, so it was very difficult to follow as the older version was quite a lot different.

---

