---
title: "[SOLVED] Update Ubuntu?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Baby Boy on 2007-08-10
I am still new to Ubuntu so bear with me even if this question may sound silly. After doing some search on the forums and reading on Dell Inspiron 1501 blog I noticed people saying 'beryl doesn't work after kernel update' or 'downgrade the ______ package'. Does that mean it's not advisable to do an allround update of ubuntu with update manager and only update the selected few programs? <Also how can I update java? - I do a search in synaptic for it and get loads of packages, how do I know which ones do I need? Same goes for all other packages>

---

### Post by SOULRiDER on 2007-08-10
Thos eproblems might be for specific kernel upgrades or something, you dont need to worry about it. 
It is safe to do a full system upgrade! Java will get upgraded when there is an update. I think the package you might be looking for is ```
sun-java6-jre
```

You should look at package descriptions, some packages that appear that are actually dependencies of the main package so they will be installed automatically. when in doubt you can ask on IRC, someone will surely answer you right away.

---

### Post by ThrobbingBrain66 on 2007-08-10
It is very rare for updates to break packages, but it does happen.  That being said, there's no reason for you NOT to update because you'll be missing important security updates and bug fixes if you don't.

To install java you need sun-java6-jre and sun-java6-plugin (for Firefox).  If you already have these installed, you won't be able to update Java.  Once an Ubuntu version is released, the packages in the repos are frozen except for bug and security fixes.

---

### Post by Baby Boy on 2007-08-10
> **SOULRiDER said:**
> 
It is safe to do a full system upgrade!


> **ThrobbingBrain66 said:**
> It is very rare for updates to break packages, but it does happen.  That being said, there's no reason for you NOT to update because you'll be missing important security updates and bug fixes if you don't.


I'll take your word for it, I hope I won't have to reinstall again ;). Makes sense to update though, just wanted to make sure.

---

### Post by SOULRiDER on 2007-08-10
Updates are tested before being uploaded, no unless all the planets int he solar system align, i highly doubt youll have a problem with any updates that cannot be easily fixed.

---

### Post by Paul133 on 2007-08-10
Sometimes updates break packages; it's rare though. As far as your specific point with Beryl, you do need to downgrade Beryl-core so it will work with XGL. A good guide is here: [http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html) It's a bit off-topic, but why are you still using Beryl? Compiz-Fusion is the one being actively worked on. A good CF guide is here: [http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html)

---

### Post by Seisen on 2007-08-10
I think that the last time we had a major break is when a kernel update broke a lot of people's computer's but a the problem was fixed in about a day.

---

### Post by Paul133 on 2007-08-10
I just remember the update from last year that broke everyone's X.

---

