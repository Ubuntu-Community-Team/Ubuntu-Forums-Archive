---
title: "Why are certain version packages available as a DEB file, but they aren't repositortd"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2006-08-03
Howdy,

This is a newbie thing to ask (Hence the forum), but why are certain versions of software available as .DEB files and not on the repositories.  

I am trying to install Mythtv version 0.19, but 0.18 is the only easyily installed program in the repositories.  I went to the MythTV page and they have DEBs for 0.19 --- and there are many Ubuntu tutorials on installing those DEBs, using dpkg I assume, but hell if the bastard is on the repos.  

Is is just because no one has packaged it yet (it's been out for months)?

Will the Texan

---

### Post by Estariel on 2006-08-03
After a version of Ubuntu gets released (in this case Dapper), all software in its repositories only gets security updates. Newer software versions will be in the next version of Ubuntu.

This is implemented to prevent newer versions of package A from breaking package B that might depend on the older version of A.

If you need (or want) to live on the bleeding edge, you have to install the packages manually.

Alternatively, a very few packages get backported from the development version of Ubuntu (edgy eft) to be compatible with Dapper, and they are in the Dapper backports repository. You may want to enable that and check whether it has what you want.

If that is too much trouble for you, you could try another distribution that keeps all packages as up to date as possible, for example gentoo or debian unstable. However, keeping these up and running (and stable) is also a lot of trouble, which is why I am using Ubuntu and just compiling lots of .deb files myself from scratch (there is a great manual for this around on these boards, but you should become comfortable with linux itself, before you start this) if Dapper does not have the newer version I want.

Hope I could help you!

---

### Post by Dr. Nick on 2006-08-03
It is probably due to the fact that it is not a "official" build, on a default install the only repos that are used are those that have been sufficiently tested and are relatively error free. I looked at myth tv and it is coming from the multiverse repo which is not a official repo, Each package in their has a maintainer that is responsible for adding updated versions of software. Maybe the maintainer just hasnt got around to repackaing it yet.

Thier are a ton of repos out thier that are not easily found, alot of people who make the programs will also make a repo that users can add to help keep up to date

for myth tv thier is a good link provided on this site
[http://www.mythtvtalk.com/forum/archive/o_t/t_3243/mythtv_.19_ubuntu_repo.html](http://www.mythtvtalk.com/forum/archive/o_t/t_3243/mythtv_.19_ubuntu_repo.html)

look at the 2nd or 3rd post. I have never used it but just saw it on searching.

To simply answer your question though for all programs in general, 
It could be the package maintianer has failed to realize a new version

Maybe the new version causes some problems and they dont want to be responsible for screwing somones computer up

Or maybe they have just quit maintaing it, in that case usually someone else takes over after a while

---

### Post by willz06jw on 2006-08-03
OK Thanks I think I gotya, 

But then why would Edgy not include the newest version, 0.19 MythTV?  From what I hear MythTV is one of the major current driver of Linux machines and the 0.18 SOB doesn't work with the current repository version of MySQL(v5).

I know that it lists 0.18 right now in Edgy, but I'm sure someone has requested this in the new version.  How can I be sure that someone has requested it, or how would I request it myself?

Thanks,
Will the Texas

BTW:  I am interested in that DEB tutorial ... i am learning Linux faster than a sponge --- I already had to recompile the damn kernal to install the IVTV drivers.

---

