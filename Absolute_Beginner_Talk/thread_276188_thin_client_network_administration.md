---
title: "thin client network administration"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by san983yfah10fnj0ujsa0 on 2006-10-12
I've just set up a thin client lab using edubuntu.  It's working great: fast and without problems.  I'm now looking for a way to easily maintain the lab.

What I'd like to do is wipe all the student work from the previous day clean.  I imagine I'll be setting up a cron job to do this, but actually figuring out how to do this is a little beyond me.

I thought I'd just tar the i386 folder and replace the working i386 folder each day with it, but I'm running into permission problems.  I've run chown and chmod (from root), but there are still files that will not change ownership.  When I try to tar (or even copy) the i386 folder, it either gives me a permissions message or, in the case of copying it, only gives me a portion of the folder hierarchy.

I'm I way off track?  Certainly this is possible and much easier than I'm making it.

thanks!

btw, I've tried for two days to come up with a username, and everything I came up with was rejected because 'a user with that name already exists' (ie dsafjhgafuifbeiw), which must be incorrect.  This one finally worked for whatever reason.

---

