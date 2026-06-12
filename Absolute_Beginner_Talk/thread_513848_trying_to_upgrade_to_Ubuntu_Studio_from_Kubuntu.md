---
title: "trying to upgrade to Ubuntu Studio from Kubuntu"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-31
I want to upgrade my Kubuntu to Ubuntu Studio. I followed the directions on their website, but I got this when I ran the wget command. Any help?


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

---

### Post by shearn89 on 2007-07-31
are you sure the address is right? looking at debs.vorian.org, the last 4 links should be "amd64" not "binary-amd64"...

---

### Post by ukulele_ninja on 2007-07-31
Im not sure what you mean... how would I change that address? It does all that automatically when I run the get-edit command for it.

---

### Post by greybit on 2007-08-02
Could you please post the contents of your sources.list file?

```

sudo gedit /etc/apt/sources.list

```

and then post the output.  This would make it easier to diagnose the problem.

Also, to fix the "NO_PUBKEY" error you can do this, which will get and install the public key to use this repository:

```

sudo gpg --keyserver subkeys.pgp.net --recv 20F4742122130E65
sudo gpg --export --armor 20F4742122130E65 | sudo apt-key add -

```

---

