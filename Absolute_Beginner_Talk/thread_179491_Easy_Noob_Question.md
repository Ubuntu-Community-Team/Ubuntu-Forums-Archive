---
title: "Easy Noob Question"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-05-20
What is the differance between a backport and a normal package?

---

### Post by aysiu on 2006-05-20
A backport is more up-to-date.

---

### Post by JNowka on 2006-05-20
Not going to argue, but why is a back port more up to date, doesn't back mean behind?

Argh just gotta love the people who name things :)

---

### Post by aysiu on 2006-05-20
I may be pulling this out of ***, but I believe the newer version is usually to be included in the upcoming release of Ubuntu, so when it is made available early to the current release it is back-ported (back from upcoming to current).

Someone else more knowledgeable than I can probably confirm that.

---

### Post by JNowka on 2006-05-20
I believe you. :)

---

### Post by Basu on 2006-05-20
From what I understand, a backport is a package meant to be in a future or later version of the OS release, but then some guys decide that they want it in an older or current release as well, so they fiddle around a bit until it works fine in the current and you get a backport. 
Example: Breezy has OOo 1.9.129 while Dapper has 2.0.2 (or something close) if OOo 2.0.2 was brought into the Breezy repos, it would be a backport

---

### Post by steve.horsley on 2006-05-20
And backports exist because when a version of Ubuntu is released, it is feature-frozen. New versions are not officially allowed - security updates (and bug fixes? I'm not sure) only. So the next whizzy version of your favourite app is not allowed in. The backports repo takes the whizzy new versions from the latest development release (Dapper at the moment) and ports them backwards into earlier (e.g. Breezy) releases. They are never officially part of the release.

---

