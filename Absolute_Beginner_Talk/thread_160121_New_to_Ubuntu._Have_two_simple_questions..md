---
title: "New to Ubuntu. Have two simple questions."
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by PaLoBo on 2006-04-14
Hi all,

I started using linux a few months ago so I'm relatively new to it but already have done away with my windows install (I got addicted...:) ). I've tried suse and opensuse, not much of a fan. I've tried Fedora and ended up using FC4 for the most time. 

But after having heard so much good stuff about ubuntu I decided to try it out. I ordered some Breezy CDs, and installed. Here is what I think and my questions.

All went well, I only didn't like the fact that I couldn't select which packages to install or not. I know this makes life easier for total newbies, but still I wouldn't mind having that option available. (After all... Linux is about choice right?)

So, since Ubuntu installed what I deemed appropriate, I then decided to get rid of the programs that I dont use or dont like. The first to go is Eye of Gnome, but when I try to uninstall I get a message saying I must use advanced to do so, using advanced I also unistalls ubuntu-desktop. 

My question is this. Is ubuntu-desktop needed. Is it important? Will ubuntu still check for and update my install without ubuntu-desktop? Will I be able to upgrade to the newer versions of Ubuntu when they come out without having ubuntu-desktop. And if so, will the upgrade reinstall the apps I removed.

WOW! Looks like it was more than two questions, but they are all tied to the same so I guess it's ok. Sorry for the long post and thanks for any feedback.

Cheers,
P.

---

### Post by gingermark on 2006-04-14
ubuntu-desktop is a metapackage, that is one that installs many other packages. Therefore, when you remove one part of it, the metapackage is also removed. Which is fine.

You might want to reinstall ubuntu-desktop before undertaking a large upgrade (ie to Dapper for example) though. It just makes things a hell of a lot easier.

---

### Post by sYs^ on 2006-04-14
Hi, about ubuntu-desktop: [http://ubuntuforums.org/showpost.php?p=920755&postcount=4](http://ubuntuforums.org/showpost.php?p=920755&postcount=4)

edit: too slow again :D

---

### Post by PriceChild on 2006-04-14
It is possible to do an "expert" ubuntu install where i think you can choose more options.

---

### Post by PaLoBo on 2006-04-14
[QUOTE=gingermark]ubuntu-desktop is a metapackage, that is one that installs many other packages. Therefore, when you remove one part of it, the metapackage is also removed. Which is fine.

You might want to reinstall ubuntu-desktop before undertaking a large upgrade (ie to Dapper for example) though. It just makes things a hell of a lot easier.[/QUOTE]

How does this make things easier...? Do you mean that I must install ubuntu-desktop any time I upgrade to a new release and then uninstall the packages that I don't want again. This doesn't make much sense! Counter productive if you ask me...

@ PriceChild: How does one go about doing an expert install?

Thanks all for your comments and help.

Cheers,
P.

---

### Post by gingermark on 2006-04-14
[QUOTE=PaLoBo]How does this make things easier...? Do you mean that I must install ubuntu-desktop any time I upgrade to a new release and then uninstall the packages that I don't want again. This doesn't make much sense! Counter productive if you ask me...[/QUOTE]

If you take upgrading to Dapper as an example, there will be new packages that exist in Dapper that aren't in Breezy. When you upgrade the metapackage (ubuntu-desktop) then you ensure you get the new packages, remove old ones, and upgrade the rest.

---

### Post by PaLoBo on 2006-04-14
Thanks for all the input. I guess I'll give it a try. Only time will tell if I become a ubuntu fanatic. I am however considering xubuntu for an old heap of a PC I have at home. Would be nice to get it going again. :)

---

### Post by steve.horsley on 2006-04-14
[QUOTE=PaLoBo]How does this make things easier...? Do you mean that I must install ubuntu-desktop any time I upgrade to a new release and then uninstall the packages that I don't want again. This doesn't make much sense! Counter productive if you ask me...
[/QUOTE]
ubuntu-desktop is a package with no actual contents but loads of dependencies on other packages like xorg, gnome, openoffice etc. It's an easy way of calling up all the standard install stuff.

If you uninstall ubuntu-desktop then nothing gets deleted. All its "dependencies" remain installed unless you choose to delete them. These packages are all packages in their own right, and get updated as normal when updates are available. You don't have to install stuff you don't want just to update pacakes that are already installed.

---

