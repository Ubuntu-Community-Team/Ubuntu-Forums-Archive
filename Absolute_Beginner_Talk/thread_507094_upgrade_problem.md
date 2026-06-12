---
title: "upgrade problem"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by waterspider on 2007-07-22
Hi please does anyone knows what this errors means............
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources                    
  404 Not Found
Fetched 6931B in 22s (304B/s)                                                  
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
:lolflag:

---

### Post by w4ett on 2007-07-22
You'll need to remove automatix before you upgrade:

```
sudo apt-get remove automatix2

sudo apt-get update
```

Then re-attempt your upgrade

---

### Post by waterspider on 2007-07-24
Thnx alot

---

