---
title: "KDE on PPC"
date: 2008-06-11
forum: Apple Hardware Users
---

### Post by anurse on 2008-06-11
Hi,

This is more of a question than anything else. Can one upgrade to KDE 4 (4.1?) on Kubuntu (8.04) on PPC (iMac G5)? If so, is there any special process one should use?

---

### Post by ssam on 2008-06-12
packages in ubuntu releases do not get updates (apart from security and bug fixes), so there wont be official KDE4.1 packages for hardy.

intrepid will have KDE4.1 (though i am not sure if it is in yet), but intrepid is in early stages of development [https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule) . probably not a good idea to upgrade yet.

there is not much chance of a KDE4.1 backport to hardy.

next choice would be find someone who has built packages for hardy. There is a personal package archive for KDE4.1 [https://launchpad.net/~kubuntu-members-kde4/+archive](https://launchpad.net/~kubuntu-members-kde4/+archive) but it does not have powerpc.

so it looks like you may have to build it yourself. one method would be to get all the source tar.gz files, build and install them. but i think it would be better to try to build deb packages.

[https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu) is a handy tool for build packages for your current distribution, using source packages from elsewhere. I suggest that you use the above PPA as the elsewhere. so you will need to add the source line
```

deb-src http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main

```
to your source.list. and then use prevu to build the packages you need from the list at [https://launchpad.net/~kubuntu-members-kde4/+archive](https://launchpad.net/~kubuntu-members-kde4/+archive)

---

