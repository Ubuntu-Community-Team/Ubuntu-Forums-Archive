---
title: "How do you run programs/install new software?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by KYhillbilly2006 on 2006-10-05
I donwloaded flash for firefox but can't figure out how to make it install.  What do I do to make programs i've downloaded install/run?

---

### Post by aysiu on 2006-10-05
Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Or this:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Jagot on 2006-10-05
Read this with regards to installing:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I relation to Flash, you need to enable the multiverse repo.  See here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then, in terminal:

```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

---

### Post by aysiu on 2006-10-05
Whoops! I didn't read the post carefully.

For Flash, try this:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

