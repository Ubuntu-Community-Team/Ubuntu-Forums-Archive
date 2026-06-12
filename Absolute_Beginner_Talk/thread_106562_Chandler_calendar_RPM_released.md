---
title: "Chandler calendar RPM released"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Books on 2005-12-20
Hi, all!

The long-awaited [Chandler]("http://chandler.osafoundation.org/") calendar/email has been [released]("http://wiki.osafoundation.org/bin/view/Journal/WeeklyStatus20051220") in it's first usable version! Chandler is the PIM that is being funded by Mitch Kapor's Open Source Applications Foundation (OSAF) and was announced with some fanfare in about 2002. Development was delayed but this release -- version 0.6 -- is now experimentally usable. This is their "dogfood" release, and while young it's now ready for cutting-edge users and testers.

My question:  The Linux download is an RPM. :???:  I'm trying not to take this as a slight against the growing and spectacular Ubuntu community...  As a newbie, I'm not sure of the proper channels to request that Chandler 0.6 be added to the packages being prepared. 

I know I'm not the only one that has been following Chandler development. There was a lot of excitement when the project started, and the developers have some good ideas. I think this calendar/email package will be something that the Ubuntu community will want to take a look at.

Any advice? Thanks!

Books

---

### Post by Rumor on 2005-12-24
[QUOTE=Books]Hi, all!

My question:  The Linux download is an RPM. :???:  I'm trying not to take this as a slight against the growing and spectacular Ubuntu community...  As a newbie, I'm not sure of the proper channels to request that Chandler 0.6 be added to the packages being prepared. 

[/QUOTE]

I downloaded it today as a tar.gz file. After I unarchived it to its own little directory, I was able to launch it fine. I am just now starting to play around with the features, but it looks ***very*** promising.

---

### Post by GTvulse on 2005-12-24
[QUOTE=Books]
[snip]

My question:  The Linux download is an RPM. :???:  I'm trying not to take this as a slight against the growing and spectacular Ubuntu community...  As a newbie, I'm not sure of the proper channels to request that Chandler 0.6 be added to the packages being prepared. 

[snip]
Any advice? Thanks!

Books[/QUOTE]

```

sudo apt-get install fakeroot alien

[chug, chug]

fakeroot alien -d --fixperms chandler-blah.rpm

[chug, chug]

sudo dpkg -i chandler-blah.deb

```

This may or may not work, depending on how badly built is the original rpm....

---

### Post by justinjstark on 2006-01-05
Has anybody gotten this to work?  I converted the rpm to a .deb and installed it with dpkg but cannot figure out how to run it...if it even installed properly.

EDIT: Nevermind...it installed itself into /usr/local/chandler!?!?

---

