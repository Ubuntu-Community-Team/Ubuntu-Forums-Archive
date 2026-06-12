---
title: "Questions on updating"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Xamindar on 2007-03-14
I am thinking on moving to Ubuntu coming from Gentoo.  I just have a couple of questions on updating packages.  

Is it easy to update to the most recent versions of software when it is available?  Are there things like the overlays that gentoo has where people have set up certain experimental packages?  Also, is there a way that xgl and beryl SVN are made available so that the daily updates can be applied?

Thanks for any info.

---

### Post by mcduck on 2007-03-14
When new versions of packages are available for the Ubuntu version you are using they are updated automatically through the Update Manager. (But because of the way Ubuntu versions work, you do not always get the latest and greatest versions until you upgrade to the new Ubuntu version).

There are third party repositories that allow you to manage extra software just like all officially supported software is handled. If you add repository for SVN beryl packages you will get automatic updates when the files in the repository are updated (which in case of Beryl SVN pretty much means daily updates)

---

### Post by Xamindar on 2007-03-15
> **mcduck said:**
> (But because of the way Ubuntu versions work, you do not always get the latest and greatest versions until you upgrade to the new Ubuntu version).

Is that very hard to do?  When the new version is available, can I just upgrade to it without much trouble and then be on that version?

Thanks for your response, I think I will switch soon.

---

### Post by mcduck on 2007-03-15
> **Xamindar said:**
> Is that very hard to do?  When the new version is available, can I just upgrade to it without much trouble and then be on that version?

Thanks for your response, I think I will switch soon.

It should only take 1 command ("gksudo update-manager -c") + some time :)

Some people have had troubles when upgrading to new versions, but for most it works fine. I've also understood that it's possible to download the installer CD and then use that to do the upgrade.

---

