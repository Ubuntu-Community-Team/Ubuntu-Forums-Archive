---
title: "#Apt-Get Update errors"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-10-31
Could anyone please advise me why I am getting the below errors when I use #Sudo apt-get update and how I can rectify the problem. It does not seem to be affecting the op system in any way but is aggravating in that it appears to not be functioning properly. The code below is the bottom of the terminal printout. All other repositories are functioning ok.
I am using Dapper 6.06 LTS and have not had this problem before the past few days.
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [59.6kB]
99% [7 Sources gzip 0]                                              21.2kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Sub-process gzip returned an error code (1)
Fetched 7B in 7s (1B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

