---
title: "Question about Gimp version in repositories"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by acl123 on 2008-01-02
Hi, I found an annoying bug in Gimp so I posted a bug report about it. But it looks like the version in repositories is quite far behind the latest version available.

Why is this?

What do you think I should do - upgrade gimp without using the repositories or just forget about it and wait for Ubuntu to catch up?

Or am I missing something - is there a way to upgrade gimp without going outside of the repositories?

---

### Post by hyper_ch on 2008-01-02
as every 6 months there is a new release of Ubuntu the versions in the repos will not get upgraded but security patches will be applied... so either you use the backports or you use other repositories with more up-to-date versions or you compile it on your own.

---

### Post by erginemr on 2008-01-02
The Gimp version in the Ubuntu Gutsy repositories has been updated a few days ago to 2.4.2, which is almost the latest version (2.4.3) the the Gimp home page offers:
[http://www.gimp.org/downloads/](http://www.gimp.org/downloads/)

So, if you are using Gutsy, you don't need to bother.

---

### Post by dmuir on 2008-01-03
Then how come I'm still using Gimp 2.4.0 RC3?
How do I update to the latest in the repository? I thought Ubuntu's software updates was supposed to do this for me? (yes, I'm running Gutsy with backports ticked in software sources)

---

### Post by erginemr on 2008-01-04
Please check out the attached screenshots, which should be self-explanatory.

---

### Post by dmuir on 2008-01-06
Thanks. Worked a treat.
Didn't have "Pre-release Updates" ticked.

Any caveats?

---

### Post by mcduck on 2008-01-06
> **dmuir said:**
> Thanks. Worked a treat.
Didn't have "Pre-release Updates" ticked.

Any caveats?

Well, pre-release updates are still in testing phase and not actually released yet, so they might sometimes have small problems. But generally they work just fine.

If you don't want them, just disable that, and as long as you have backports enabled you'll get the same updates after they've been a while in pre-release updates without any problems.

I think it usually takes a week or two for packages to move from pre-released to backports.

---

