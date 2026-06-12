---
title: "Hardy Heron Issues with MacBook Pro 3,1 Santa Rosa"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by abhisheknk on 2008-04-26
I have been unable to install the madwifi from the pre-r3403 tars. I was unable to find the 3403 snapshot from the madwifi, and used 3402. Also, I get many errors after execution of make and sudo make install.

I'm using the x64 version of Ubuntu on my MacBook Pro 2.2 Santa Rosa C2D. In the Hardware Test, Ubuntu shows me the Atheros 5418 Wireless(b/g/n) chipset on the network card list but it doesn't appear on the Network Configuration. I only see one Wired Connection and Point to Point connection.

I've chosen to virtualize Linux in the past, but would like to use it with full functionality for which I can't use VMware. The wireless isn't currently working for me and until it does, Ubuntu is just another Linux distro that's failed to work.

Also, I'm on a shared wireless connection without access to the ethernet interface, which is why I have to download all the tarballs on OS X and put it in my pen drive to use it on Ubuntu. I assume the apt-get requires network access, and I wonder how people have got it to work if they aren't even connected to the internet.

---

### Post by cyberdork33 on 2008-04-26
> **abhisheknk said:**
> I have been unable to install the madwifi from the pre-r3403 tars. I was unable to find the 3403 snapshot from the madwifi, and used 3402. Also, I get many errors after execution of make and sudo make install..
you really need to connect to an ethernet interface for a limited time.

you need to install the build-essential package to have all the utilities for compiling. Are you following this:
[https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927](https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927)

---

