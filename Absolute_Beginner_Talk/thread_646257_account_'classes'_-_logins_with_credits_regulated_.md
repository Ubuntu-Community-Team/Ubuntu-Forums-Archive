---
title: "account 'classes' - logins with credits? regulated login accounts?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by nicknormal on 2007-12-21
hypotheses:

i have some kids. they're smart enough to access the Ubuntu box. on the Ubuntu box I store lots of movies and videos for them to watch, tv shows, etc.

I want them to only be able to access the Ubuntu box in exchange for doing chores, homework, taking baths, etc.

SO, is there any way to limit an account to a sort of 'credit' system? where each credit is equal to one hour run-time, or something to that effect?

I know this sounds really far-fetched, and I don't even have kids, I'm just using that as an example of something I'm trying to implement on an Ubuntu machine for an experiment of sorts.
Any ideas?
a login system with regulated user accounts that get access in exchange for some other service or controlled by admin?

cheers!
Nick

---

### Post by [S|G] on 2007-12-21
Greetings!

Well, you can do that, but its implementation is somewhat non-trivial. You can implement it by having a radius server and using a pam module to authenticate together with the radius server. 

To read more about radius: [http://www.freeradius.org/](http://www.freeradius.org/)

I never implemented radius to control logins on a linux server myself, but I believe it would be possible, since radius is aimed exactly at keeping user accounting.

---

