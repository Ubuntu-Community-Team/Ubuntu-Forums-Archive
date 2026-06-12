---
title: "Synaptic update?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-08
How to update synaptic manager?
Just reload button in the left corner?
For ex. in web,pidgin launched 2.3.1 version.
But in synaptic version is 2.2.1.
How to see latest programs?

---

### Post by nrfool on 2008-01-08
My understanding is that Synpatics searches the repositories it's aware of (user can that list of repositories). If the last version is one of the repositories, it will show up on synaptic. Otherwise, it will not. There might be a lag between a application releases a new version and the new version is added to one of your repositories.

---

### Post by LowSky on 2008-01-08
ubuntu repositories are locked at the release date, which means programs are stuck at whatever version is availible at the time, except for major security patches.
If you want the newest version then you will have to compile the program for its source.

---

### Post by hyper_ch on 2008-01-08
or you could add more updated repositories like the backports.

---

### Post by rhc on 2008-01-08
> **hyper_ch said:**
> or you could add more updated repositories like the backports.

Can you open that a little?

---

### Post by hyper_ch on 2008-01-08
Open up synaptic and study its possibilities...

---

### Post by mcduck on 2008-01-08
> **rhc said:**
> Can you open that a little?

Go to System/Administration/Software Sources, and on the Updates-tab enable "Unsupported updates (gutsy-backports)". This will give you more up-to-date packages, ported from the current development version of Ubuntu.

Even enabling backports doesn't mean that you would always get the latest and greatest versions of every piece of software. Only those packages that are fairly easy and problem-free to backport get in this repository. And even those don't get there immediately after the new program versions are released.

---

### Post by rhc on 2008-01-08
> **mcduck said:**
> Go to System/Administration/Software Sources, and on the Updates-tab enable "Unsupported updates (gutsy-backports)". This will give you more up-to-date packages, ported from the current development version of Ubuntu.

Even enabling backports doesn't mean that you would always get the latest and greatest versions of every piece of software. Only those packages that are fairly easy and problem-free to backport get in this repository. And even those don't get there immediately after the new program versions are released.

Thank you very much.

---

### Post by mcduck on 2008-01-08
> **rhc said:**
> Thank you very much.

No problem :)

By the way, here's a nice place to find .deb packages for those programs that don't get updated in Ubuntu repositories: [http://www.getdeb.net/]("http://www.getdeb.net/")

(actually there's even some programs that are completely missing from Ubuntu's repositories)

---

### Post by rhc on 2008-01-08
> **mcduck said:**
> No problem :)

By the way, here's a nice place to find .deb packages for those programs that don't get updated in Ubuntu repositories: [http://www.getdeb.net/]("http://www.getdeb.net/")

(actually there's even some programs that are completely missing from Ubuntu's repositories)

And i wanna ask something.
What is the third party software setting?
Should i enable them,archive.canonical.com?

---

### Post by mcduck on 2008-01-08
> **rhc said:**
> And i wanna ask something.
What is the third party software setting?
Should i enable them,archive.canonical.com?

It contains some commonly used and free-of-cost software that isn't open-source, like Opera browser and WMware Server. Enable it if you need those programs.

---

### Post by rhc on 2008-01-08
Thanks.

---

### Post by icechen1 on 2008-01-08
getdeb.net has some newer version of some app.

---

