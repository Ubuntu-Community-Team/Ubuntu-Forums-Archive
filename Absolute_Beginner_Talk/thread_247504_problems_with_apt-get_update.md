---
title: "problems with apt-get update"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by fragman204 on 2006-08-30
Yes, I read the post explaining what happened on 08-21-06.

Well I don't have the Xserver problem, but I can't get any of my computer to update.

The reply is the same “unable to reach the host “or it will ignore some of the repositories completely.

I have checked all my connections and all of my configurations. All of them check OK.

Maybe I'm missing something, any help will be appreciated.:-k

---

### Post by thephantomlinguist on 2006-09-28
Just browsing around and came across your post...

I had a similar problem a while back. Turned out my apt repositories were all set to pull via ftp. I changed them all to http and things went peachy. Not real sure where the problem came from in the first place...

Hope that helps. If not, post your sources.list (/etc/apt/sources.list). Maybe someone will see something you've missed.

---

