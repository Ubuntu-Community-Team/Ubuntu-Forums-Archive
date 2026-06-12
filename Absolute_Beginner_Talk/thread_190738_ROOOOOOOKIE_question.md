---
title: "ROOOOOOOKIE question"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by ibtexn on 2006-06-06
I keep getting this eror whe aI try to update?  is there another repository   and where do i edit this address? 


[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (85.133.25.7), connection timed out

---

### Post by Mbuhrow on 2006-06-06
If you want to upgrade to dapper, open system>administration>update manager
click the button that checks for upgrades.
If it finds none go to system>administration>synaptec package manager
go to settings>repositories and click the 'add' button
in the drop down list there should be something like 'ubuntu 5.10 updates'
select it and click add. close synaptic, go back to the update manager and try again, it may download some updates and then you have to check *again* until it says that a new version of ubuntu is available.

---

