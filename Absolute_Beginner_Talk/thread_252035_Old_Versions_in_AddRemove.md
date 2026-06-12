---
title: "Old Versions in Add/Remove"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by tunisay on 2006-09-06
I am completely new to this so I've just been installing packages using the Add/Remove feature under Applications.  I've noticed that many of the packages under Add/Remove are older versions thatn ones I have found while browsing the net (Amarok and OpenOffice for example).

Is there any way to update the list in Add/Remove to fetch those new versions or do I have to do something more complicated?

Thanks for the help!

---

### Post by slibuntu on 2006-09-06
I've noticed that aswell. Its pretty annoying so if theres a solution, I'd like to hear it!

---

### Post by monktbd on 2006-09-06
> **slibuntu said:**
> Its pretty annoying 

why is it annoying?
doesnt the version in the repos work properly?

what can be done is

a) download the current version and compile and install it
b) make a .deb out of it and give it back to the community
c) find someone who made a+b already. 

(there is someone who makes always a bleeding edge rythmbox version i use)

drawbacks for a) you need to keep it updated yourself, no automatic updates for it.
same goes for c) unless it is in a repo you can add to your sources.list.

when a version of ubuntu is done the ubuntu team fixes security holes and bugs in that version of the software but does not put new versions into the repositories simply becaue it would take a lot of testing if these new version work properly.

then i am not sure but with the 5 years lts of ubuntu maybe some version updates will be done. anyone knows anything whether that is planned?

---

### Post by az on 2006-09-06
You mean that the versions inthe repositories are not as new as the versions from upstream?

Before release, there is a version freeze.  The version of the packages stay frozen so that they can be thouroughly tested for release.  With Dapper, there is an updates repository that includes less severe bug fixes and some new package versions.

They have been pretty liberal about including new versions of some apps in it, but there recently was a problem with an Xorg release that prevented some people from being able to log in.

I think until they get a better procedure for quality control (like a proposed-updates repo) the packages will not be updated as much.

As ususal, if you want something to work, stay with the stable version.  If you want cutting-edge, use the develpmental version (currently Edgy)

---

