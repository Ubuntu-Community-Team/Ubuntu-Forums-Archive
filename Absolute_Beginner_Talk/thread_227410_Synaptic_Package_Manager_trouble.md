---
title: "Synaptic Package Manager trouble"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by John Inman on 2006-08-01
Hi I am having the following problem with the Synaptic Package Manager(spm).
When I reload I get this message.

[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release:) Unable to find expected entry  universe///source/Sources in Meta-index file (malformed Release file?)

I can't figure out how to solve this problem, and will be greatful for help.

Thanks.
John:D

---

### Post by deadgobby on 2006-08-01
> **John Inman said:**
> Hi I am having the following problem with the Synaptic Package Manager(spm).
When I reload I get this message.

[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release:) Unable to find expected entry  universe///source/Sources in Meta-index file (malformed Release file?)

I can't figure out how to solve this problem, and will be greatful for help.

Thanks.
John:D
 I click on the link you provided and there is no such URL. However, if you take out the : at the end of the link. The link works. So you may have to edit your /etc/apt/sources.list and edit the link and take out the : at the end of the link. The link should look like this. 
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release)

Gobby

---

