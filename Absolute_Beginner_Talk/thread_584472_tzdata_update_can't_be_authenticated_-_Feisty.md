---
title: "tzdata update can't be authenticated - Feisty"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by HunterSBuntu on 2007-10-21
I had a software update notification today for tzdata (update to version tzdata2007h) but when I try to begin the installing it says the update can't be authenticated.

Should I be worried about this? I have not installed the update yet.  If it is an actual update I'd like to go ahead with it if I'm not putting myself at risk of anything harmful.

---

### Post by Lightstar on 2007-10-21
I've been having a bunch of 'NOT AUTHENTICATED' updates for the last week or so, I've accepted them all and my system is as good as it was before.  Might want to wait for more opinions though, I'm still a newbie

---

### Post by chewearn on 2007-10-21
This things sometimes happened.  I have seen the authentication errors now and again, after using ubuntu for more than a year.

I'm not 100% positive here, but I guessing that this error occurred when a new update is not uploaded at the same instance as the authenticaltion info to the server.  Sometimes, the files take awhile to sync across all the mirror servers.

In any case, it is not something to worry about.  Myself, I choose the safer route of not updating when I see this error (because you never know what's is going on).  Usually, the error will clear up in a day or so.  Sometimes, clicking the [Check] button in the Update Manager helps (equivalent to sudo aptitude update).  The worst I have seen this was a while back, when the updates stuck for almost a week, but eventually the error is resolved by itself.

---

### Post by birdbrain on 2007-10-31
It happened to me ```
apt-get update
``` seemed to work.

---

