---
title: "Rewriting sources.list"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by mevets on 2008-04-21
I just found out my university hosts an apt-repository for ubuntu gutsy, dapper, and hardy. I figure they maintain this repo because they run ubuntu under vmware for 'C and UNIX' classes and for anyone who wants to... just use linux.

Its located at [http://itec-backup.radford.edu/ubuntu](http://itec-backup.radford.edu/ubuntu) . And yeah I realize it is only available from within our schools network.

I have a few questions. Is there a way for me to figure out if the repo they maintain is compete and up to date? I don't want old software. Secondly, how can I rewrite my /etc/apt/sources.list so I can receive blazing fast updates from a server on campus? The reason I have to ask this is because I believe they organized the server a little different than most apt repos.

```

Index of itec-backup.radford.edu/ubuntu
[ICO]	Name	Last modified	Size	Description
[DIR]	Parent Directory	 	-
[DIR]	security/	13-Nov-2007 07:03 	-
[DIR]	ubuntu/	13-Nov-2007 07:03 	- 
--------------------------------------------------------------
  Index of /ubuntu/security
  [ICO]	Name	Last modified	Size	Description
  [DIR]	Parent Directory	 	-
  [DIR]	dists/	23-Mar-2008 22:52 	-
  [DIR]	pool/	12-Nov-2007 17:09 	- 
-------------------------------------------------------------
    Index of /ubuntu/security/dists
    [ICO]	Name	Last modified	Size	Description
    [DIR]	Parent Directory	 	-
    [DIR]	dapper-security/	13-Nov-2007 07:03 	-
    [DIR]	feisty-security/	26-Dec-2007 23:15 	-
    [DIR]	gutsy-security/	13-Nov-2007 07:03 	-
    [DIR]	hardy-security/	23-Mar-2008 22:52 	- 

```
Index of /ubuntu/ubuntu as seen in Index of itec-backup.radford.edu/ubuntu (the first folder listed) is structured much the same, but instead of being security updates they are the rest of the the packages that should be in any repo.

Hopefully the above info can help someone suggest a rewrite of my sources.list. I can provide more info if necessary.

---

