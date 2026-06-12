---
title: "Making sure I have all the repositories (repos)"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by billingsworld on 2007-01-20
I was asked if I had all the repo's and frankly, I have no idea :confused: 

I have:
/etc/apt/sources.list.d/edgy-multiverse.list  - which contains:

# automatically added by gnome-app-install on 2007-01-18 21:48:23.213061
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates multiverse

/etc/apt/sources.list.d/edgy-universe.list - which contains:

# automatically added by gnome-app-install on 2007-01-18 21:48:28.876113
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates universe


Should I have more?


Thanks.

---

### Post by taurus on 2007-01-20
Check your /etc/apt/sources.list!  That's where the main repos are located.

```
cat /etc/apt/sources.list
```

Here's an example you can compare with.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by braddcadd on 2007-01-20
Here are a few instructions from the Dapperguide:
[http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories](http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories)

Basically there is the main repository, the muliverse, and the universe.  Hope that helps.

---

