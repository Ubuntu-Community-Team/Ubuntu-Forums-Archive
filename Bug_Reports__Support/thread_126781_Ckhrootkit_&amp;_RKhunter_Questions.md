---
title: "Ckhrootkit &amp; RKhunter Questions"
date: 2006-02-07
forum: Bug Reports / Support
---

### Post by Oceola on 2006-02-07
This is more questions than requests.

I have the Chkrootkit 0.44 from the hoary security repository.
I searched the packages available for Hoary/Breezy and Dapper and noticed Dapper had the latest release 0.46a. I DL'd this package a while ago from [www.chkrootkit.org](www.chkrootkit.org) and using the Makefile installed it and it seems to be running fine.
My question on this is why isn't 0.46a avaialble in the Hoary Backports, it works fine, records into the logs. I have been using it as a standalone but it actually does a more in depth job than 0.44.

Second question:
I looked around to see if Rkhunter was available in the Repositories and in the Backports and came across a post here where it was in a staging area, that post was in June or July. I searched to see if it was a closed or deferred request and it didn't regester as a post. A couple of months ago I DL'd RKhunter, an rpm package which was on a free Slackware disc I pulled off a Linux Magazine and placed it in it's own directory. I used archive manager to open it and ran the install script. Aside from telling me I needed root priveledges it installed fine after the login.  I went to RKhunter's site and uploaded the newer version and placed it in the original directory and it installed even better than the first time and corrected an update error. I've also been able to update the definitions since this install.This was also commented in the same thread and is supposed to be in the repositories for Hoary but I can't find it, I have all the repositories listed including the backports, they all show the little update stars in synaptics and almost every installation has been proper.

What is going on, am I being redirected to dormant repositories or are all these posts I'm seeing in error? It makes no sense to me if Hoary is functioning properly to go through literally days of dial up transmissions for a complete upgrade to Breezy for an older package or wait for Dapper which may not even run on my harware. Have I missed something here about the openess of how this is supposed to work?

It seems a lot of packages are reserved for the newer versions like Breezy and Dapper with little regard for making something which works up to date. I knoe this is the goal of Backports but there seems to be something screwy going on as far as the logical progression and upgrade of single packages.

:confused:

---

### Post by Mez on 2006-02-09
if you see something that needs backporting and we've missed - please feel free to email [email]ubuntu-backports@lists.ubuntu.com[/email]

Other than that - well - we cant keep an eye on everything.

Hoary-backports is now closed - it gets to a point where we cant backport things easily - and backporting from dapper to hoary is pretty much a brick wall at the mo

---

### Post by Oceola on 2006-02-11
@Mez - 
Thanks for an answer. I know folks are busy with other things. The version of Checkrootkit is 0.46, the same one in Dapper, I looked at the packages for the distribution. 

Thanks again and keep this in mind when the Backports open up again.
I'd think the updates for small files like this would be worthwhile.
:)

---

