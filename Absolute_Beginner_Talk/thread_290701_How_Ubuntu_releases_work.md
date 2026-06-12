---
title: "How Ubuntu releases work"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by felixnine on 2006-11-01
I've been scouring the Ubuntu site but I can't seem to find a definitive answer to my question or set of questions:

1) The way I understand it (maybe) is that once a new version of Ubuntu is released, it's a freeze of Debian unstable (or testing?), which means that post-release, no new packages are added unless they're available through backports. Is this true?

2) I'm one of those "break my distro" idiots who always needs the latest version of a package (Gaim 2.0 Beta 4, for example). Are there "unstable" repositories for Ubuntu or do I just need to upgrade to Feisty Fawn?

Thanks.

---

### Post by RjBanker18 on 2006-11-01
1) When a new ubuntu is released (every 6 months by the way) it is a stable release.
2) Feisty Fawn is not out yet, if you want newer versions of apps then you can usually goto the app-makers website and there are usually instructions on how to install the latest version.  As far as I can see with Gaim beta 4, you would have to compile it from the source files they have. gaim-2.0.0beta4.tar.gz is the file you would get from [http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=456679]("http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=456679")

Look at the section named "Source Package (.tar, .tar.gz, .tgz, ...)"
[http://monkeyblog.org/ubuntu/installing.html#source]("http://monkeyblog.org/ubuntu/installing.html#source")

:note: If a gaim icon does not show up in your "Applications>Internet" they just goto a terminal and type in "gaim".

Good luck! :D

---

### Post by felixnine on 2006-11-01
Thanks for the quick reply, but that doesn't really answer either of my questions.

I'm aware that Edgy is a "stable" release, but does that mean no new packages are, from this point on, going to be added to the tree?

I'm aware that Feisty Fawn isn't out yet, but is that the development version in which new  packages are added regularly? (I currently have Feisty as my main repository)

---

### Post by aysiu on 2006-11-01
Sometimes people will "backport" Feisty packages to Edgy or Edgy packages to Dapper, but, yes, for the most part, Ubuntu releases are feature-frozen and version-frozen on release date. Any further updates are security patches only.

---

### Post by Joe_CoT on 2006-11-01
Released versions are generally in what is called a "feature freeze". New packages might be added and updated in universe, but generally the only changes to main are bug fixes and security fixes. For example: if a new version of Firefox comes out that is 2.0.1, which is minor fixes and security patches, it'll be put in main almost immediately; if a Firefox 2.5 is released, that will go in Feisty (I use Firefox as an example, as it's never updated to a new version on the current stable, because of how many packages depend on it). Same thing if there's a Gaim 3, etc.

New development generally goes in Ubuntu+1, in this case Feisty. Once Feisty has new versions of programs which people want to use, they might make their way into the backports.

I admire your enthusiasm and courage for using the Feisty repos :-D In case you're not aware, the unstable Ubuntu release generally breaks in large ways and very often, as new things are added and configurations conflict. Unless you're a seasoned Ubuntu user and plan on being very active in the ubuntu-dev mailing list and the #ubuntu+1 irc channel, you might want to consider sticking with Edgy right now -- if this is your main computer, you do **not** want to run feisty. In the past changes in unstable have sometimes killed systems for days. Your mileage may vary.

---

### Post by felixnine on 2006-11-01
Thanks again, that was definitely the answer I was looking for.

I've been running Debian unstable for the past year (and Gentoo before that); am I correct in assuming that Feisty in Ubuntu is the analog of Debian's unstable?

---

### Post by Joe_CoT on 2006-11-01
> 
I've been running Debian unstable for the past year (and Gentoo before that); am I correct in assuming that Feisty in Ubuntu is the analog of Debian's unstable?

In that they're the unstable version, yes; whether or not Ubuntu+1 breaks more or less than Debian unstable, someone else would have to attest to. All I know is that in the past it's broken **a lot**. If you're used to dealing with the Debian nitty gritty, and you like I are a Gentoo survivor :cool:, you should be alright. Just don't go running anything life critical on a Ubuntu+1 system.

---

### Post by az on 2006-11-01
> **aysiu said:**
> Sometimes people will "backport" Feisty packages to Edgy or Edgy packages to Dapper, but, yes, for the most part, Ubuntu releases are feature-frozen and version-frozen on release date. Any further updates are security patches only.

For the LTS release (Dapper) many new package version have been added post-release using the Dapper-updates repo.

So, some new versions and some new features do make it in.

---

