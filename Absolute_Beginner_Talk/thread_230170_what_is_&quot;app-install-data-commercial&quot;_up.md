---
title: "what is &quot;app-install-data-commercial&quot; update ?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-08-05
I see that the latest downloadable update that is now available for Ubuntu Dapper Drake is "**App-install-data-commercial**".

Can someone give an explanation as to what this update is for ?

The description as given on the download in update manager and also from a google search talks about data for available commercial gnome-app-install.

What does this mean ?

Is this simply an installer for software applications similar to the installer in M/S O/S ?  

And if so, is this something that would be automatically called from the Ubuntu O/S by an application executable that is written to use it ?

Thanks.

---

### Post by LinuxLemur on 2006-08-06
I have noticed this too.  I was going to start my own thread but wanted to see if I could search it out a little.  Sounds a little like data collection to me.  Anyone know?  Anyone just ignored and installed it?  Anyone feel uneasy about installing this update?

---

### Post by az on 2006-08-06
Canonical made (and is making more) some deals with thrid-party software vendors to include certain applications in Ubuntu repositories.  Since these packages are not distributed under free-libre licences (they are prorietary) and are not freely redistributable (so not in multiverse) they made a dapper-commercial repository. 

Commercial refers to the inclusion of a package into the repo - (I guess Canonical makes some money there) and not the software since most free-libre software can be used for commercial purposes (what web hosting provider doesn't use apache?)

So, in order to make this easily installed by end-users, the add-remove programs tool contains the entries for the new packages.  When you click to install the software, the dapper-commercial repo gets added to your sources.list (you are notified and have to agree to this).

Every time a new application enters the dapper-commercial repo, the add-remove programs data package gets reved.

---

