---
title: "[SOLVED] Can't Install anything. (Broken Package: Virtual Box)."
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by b15h0p7 on 2007-10-06
k, well I guess since I closed Package Manager when it was installing Virtual Box the package is now broken.

I cannot install anything but I managed to get Synaptic running but I get this error message when trying to remove the broken package:
```
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory
```

sudo apititude update output:
```
Get:1 http://www.virtualbox.org feisty Release.gpg [189B]
Ign http://www.virtualbox.org feisty/non-free Translation-en_US
Get:2 http://www.virtualbox.org edgy Release.gpg [189B]
Ign http://www.virtualbox.org edgy/non-free Translation-en_US
Get:3 http://www.virtualbox.org dapper Release.gpg [189B]
Ign http://www.virtualbox.org dapper/non-free Translation-en_US
Get:4 http://www.virtualbox.org etch Release.gpg [189B]
Ign http://www.virtualbox.org etch/non-free Translation-en_US
Get:5 http://www.virtualbox.org sarge Release.gpg [189B]
Ign http://www.virtualbox.org sarge/non-free Translation-en_US
Get:6 http://www.virtualbox.org xandros4.0-xn Release.gpg [189B]
Ign http://www.virtualbox.org xandros4.0-xn/non-free Translation-en_US
Hit http://www.virtualbox.org feisty Release
Hit http://www.virtualbox.org edgy Release
Hit http://www.virtualbox.org dapper Release
Hit http://www.virtualbox.org etch Release  
Hit http://www.virtualbox.org sarge Release 
Hit http://www.virtualbox.org xandros4.0-xn Release
Get:7 http://www.virtualbox.org feisty Release [556B]
Get:8 http://www.virtualbox.org edgy Release [339B]
Get:9 http://www.virtualbox.org dapper Release [341B]
Ign http://www.virtualbox.org feisty Release  
Ign http://www.virtualbox.org edgy Release    
Ign http://www.virtualbox.org dapper Release  
Get:10 http://www.virtualbox.org etch Release [554B]
Get:11 http://www.virtualbox.org sarge Release [340B]
Ign http://www.virtualbox.org etch Release     
Ign http://www.virtualbox.org sarge Release    
Get:12 http://www.virtualbox.org xandros4.0-xn Release [348B]
Ign http://www.virtualbox.org xandros4.0-xn Release
Ign http://www.virtualbox.org feisty/non-free Packages
Ign http://www.virtualbox.org edgy/non-free Packages
Ign http://www.virtualbox.org dapper/non-free Packages
Ign http://www.virtualbox.org etch/non-free Packages
Ign http://www.virtualbox.org sarge/non-free Packages
Ign http://www.virtualbox.org xandros4.0-xn/non-free Packages
Hit http://www.virtualbox.org feisty/non-free Packages
Hit http://www.virtualbox.org edgy/non-free Packages
Hit http://www.virtualbox.org dapper/non-free Packages
Hit http://www.virtualbox.org etch/non-free Packages
Hit http://www.virtualbox.org sarge/non-free Packages
Hit http://www.virtualbox.org xandros4.0-xn/non-free Packages
Fetched 3612B in 1s (1942B/s)
Reading package lists... Done
W: GPG error: http://www.virtualbox.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: GPG error: http://www.virtualbox.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: GPG error: http://www.virtualbox.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: GPG error: http://www.virtualbox.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: GPG error: http://www.virtualbox.org sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: GPG error: http://www.virtualbox.org xandros4.0-xn Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 390EC3FF927CCC73
W: You may want to run apt-get update to correct these problems

```

EDIT: I'm not interested in installing Virtual Box, just so I'm able to install other .debs w/o problem I'm fine.

---

### Post by Pumalite on 2007-10-06
You might want to try:

sudo dpkg --remove --force-remove-reinstreq virtualbox

---

### Post by b15h0p7 on 2007-10-06
I can't thank you enough ^^

*bows down*

---

### Post by Pumalite on 2007-10-06
You are welcome. Happy Ubuntuing!

---

