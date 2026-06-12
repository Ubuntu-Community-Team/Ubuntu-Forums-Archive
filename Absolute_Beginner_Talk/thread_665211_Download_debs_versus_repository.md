---
title: "Download debs versus repository"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by scamper_22 on 2008-01-12
Hi,

I've installed ubuntu and its running fine.  For the most part, I've used the repositories.

But I really want to get the latest versions of certain software (freeciv, pigdin...).

I've seen various deb downloads on the internet...how does this conflict with the repositories?
Suppose I have free-civ installed from the repro.
Then I go out an download a newer version from an internet deb.
What happens in terms of future upgrades and what not.

Or how about if i don't have pidgin installed from the repro
i download a deb for it and and install it
if an update is available from the repo, will it still update?

How often does ubuntu update its repos to pick up these newer versions?

Thanks,

Y

---

### Post by wolfen69 on 2008-01-12
i dont know how often they update the repos, but once an app makes it into the repos, you will recieve updates. you can always just download the updated .deb and do it yourself.

---

### Post by scamper_22 on 2008-01-12
Yes, I know I can download the debs myself, but how does that affect the repositories.

I don't want to screw up my system :)
My basic question is how does manually installed a deb affect the debs in the repository.

Maybe there is no problem, but I need confirmation of that.

---

### Post by wolfen69 on 2008-01-12
ive installed many .debs without it screwing up anything. you have no worries. i promise.

---

### Post by erginemr on 2008-01-12
> **scamper_22 said:**
> Yes, I know I can download the debs myself, but how does that affect the repositories.

I don't want to screw up my system :)
My basic question is how does manually installed a deb affect the debs in the repository.

Maybe there is no problem, but I need confirmation of that.

Don't worry! As long as the the site whence you download the deb files is reliable, you can safely install them. The installed version will show up in Synaptic and you can later unistall them as usual if you wish.

For a very good site with programs and games in Ubuntu debian packages, check out:

[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by ugm6hr on 2008-01-12
If you install with a reliable .deb, there should be no problem.

Even if a version of the same software exists in the repo - it will just tell you that when you run GDebi to install the .deb, and say something about recommending you stick to repo versions.  You can safely ignore that.

If an updated version becomes available in the repo (which is unlikely in Ubuntu), you can just uninstall the .deb (with Synaptic), and install from the repo.

So - to sum up: just do it.

---

### Post by SunnyRabbiera on 2008-01-12
just be careful where you get them from and cross your fingers they dont have some insane dependency issue

---

### Post by nowshining on 2008-01-12
when an ubuntu  version is released u will get NO updates on features on any programs in the repos, u'll only get security updates if any, so installing a deb from the the net and installing the updated one in the repositories will get u back to the same features u had before, sometimes they may have bugs and well some don't get fixed until a newer ubuntu version is out.

So if u want a newer version than in the repos, u'll have to install them urself or wait and upgrade to the next ubuntu version once it is officially out. :)

some programs require complation - easy if it goes right.

./configure
make
sudo make install

if u choose to make a debian file it's easy with checkinstall then the commands will go

./configure

make

sudo checkinstall -D make install

:)

yes the warning when installing deb files can be ignored

packages.ubuntu.com - defaults to latest ubuntu version when searching is the main site for the packages in the repository.

if u want the latest pidgin u can go to my website to find out how to easy upgreade to it, :) and newer rythmbox, and so forth..

---

### Post by scamper_22 on 2008-01-12
Thanks guys.

I've installed freeciv from getdeb
I think I'll stick with that.  

Too bad the repos won't check for updates of 'manually' download versions. that would be tops :P
In any case, everything seems to be working fine.  

Anyone know of a repo that keeps the latest versios of applications (things you don't really care about)  games, IM... that way I can just attach to a repository?

---

### Post by nowshining on 2008-01-16
by the way if u do update/download from a new source url and put it in the sources then yeah it should check to see if there is an updated version and update it for u if ur on auto. :)

---

### Post by nikoPSK on 2008-01-16
> **wolfen69 said:**
> ive installed many .debs without it screwing up anything. you have no worries. i promise.

I promise too. :) The deb will get updated (oops, I mean software) once it's installed. No worries. :D

---

