---
title: "apt-get error"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by kokyun on 2007-07-01
can anyone share the ubuntu default source list with me ? cos i think i have mess up mine (/etc/apt/sources.list)

i got this error. dont know how to fix it o 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages                  
  Sub-process gzip returned an error code (1)
Fetched 9B in 7s (1B/s)                                                        
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/...386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/...386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/...386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by rocknrolf77 on 2007-07-01
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories) :)

---

### Post by kokyun on 2007-07-01
> **rocknrolf77 said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories) :)

Yes, before i started posting this thread, i have tired to copy and paste the source list provided from that website and tried to update with sudo apt-get update. still cannot work:(

---

