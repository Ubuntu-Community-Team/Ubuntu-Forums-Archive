---
title: "Some repositories not downloading"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by AlP36 on 2008-02-26
When updating with Synaptic I always get these messages:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
&
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)

I checked /etc/apt/sources.list and did not see a reference to this us.archive.ubuntu.com/ubuntu/dists/dapper/main/source or "-updates/main/source". Do I need to add or change something?

---

### Post by dcstar on 2008-02-27
> **AlP36 said:**
> When updating with Synaptic I always get these messages:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
&
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)

I checked /etc/apt/sources.list and did not see a reference to this us.archive.ubuntu.com/ubuntu/dists/dapper/main/source or "-updates/main/source". Do I need to add or change something?

Go into Synaptic and select a repository closest to you, just using the overloaded common sites is asking for problems.

---

