---
title: "Ubuntu Studio Help"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-31
Im trying to upgrade to Ubuntu Studio from Kubuntu but when I followed the steps on their website I got this....

Err [http://debs.vorian.org](http://debs.vorian.org) feisty/deb Packages
  404 Not Found
Err [http://debs.vorian.org](http://debs.vorian.org) feisty/http://archive.ubuntustudio.org/ubuntustudio Packages
  404 Not Found
Err [http://debs.vorian.org](http://debs.vorian.org) feisty/feisty Packages
  404 Not Found
Err [http://debs.vorian.org](http://debs.vorian.org) feisty/main Packages
  404 Not Found
Fetched 178kB in 27s (6541B/s)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://debs.vorian.org/dists/feisty/deb/binary-amd64/Packages.gz](http://debs.vorian.org/dists/feisty/deb/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://debs.vorian.org/dists/feisty/http://archive.ubuntustudio.org/ubuntustudio/binary-amd64/Packages.gz](http://debs.vorian.org/dists/feisty/http://archive.ubuntustudio.org/ubuntustudio/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://debs.vorian.org/dists/feisty/feisty/binary-amd64/Packages.gz](http://debs.vorian.org/dists/feisty/feisty/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://debs.vorian.org/dists/feisty/main/binary-amd64/Packages.gz](http://debs.vorian.org/dists/feisty/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://debs.vorian.org](http://debs.vorian.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 20F4742122130E65
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.



I noticed that Studio is only available as 32 bit but I have a 64 bit machine, is that going to make a difference?

---

### Post by MetalMusicAddict on 2007-07-31
Looks like you have a connection issue with the other errors. Only some of the packages will work on 64 bit. I think just the themes.

---

### Post by ayenack on 2007-07-31
OK now someone has replied to this I'll chip in. If you ask me you should consider [64 Studio]("http://64studio.com/") very good Distro and 64Bit compatable both AMD and Intel 64BIT chip sets are supported. Check out the link above for details. It's also based on the Debian distro.

Best of luck. ayenack.

---

