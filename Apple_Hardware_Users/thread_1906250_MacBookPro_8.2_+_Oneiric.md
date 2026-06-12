---
title: "MacBookPro 8.2 + Oneiric"
date: 2012-01-08
forum: Apple Hardware Users
---

### Post by mpodroid on 2012-01-08
I recently been able to install succesfully Oneiric on my MacBookPro 8.2

I had to dig quite a lot on internet before being able to have it running with all required support.

Documented here what I've done:
[LIST]
[*]Created page [Ubuntu Documentation]("https://help.ubuntu.com/community/MacBookPro8-2/Oneiric")
[*]Created repository [ppa:mpodroid/mactel]("https://launchpad.net/~mpodroid/+archive/mactel") with packages for wireless and fan control
[*]Short [blog post]("http://marpoz.blogspot.com/2012/01/ubuntu-on-macbook-pro-82.html")
[/LIST]

---

### Post by Double.J on 2012-01-08
> **mpodroid said:**
> I recently been able to install succesfully Oneiric on my MacBookPro 8.2

I had to dig quite a lot on internet before being able to have it running with all required support.

Documented here what I've done:
[LIST]
[*]Created page [Ubuntu Documentation]("https://help.ubuntu.com/community/MacBookPro8-2/Oneiric")
[*]Created repository [ppa:mpodroid/mactel]("https://launchpad.net/~mpodroid/+archive/mactel") with packages for wireless and fan control
[*]Short [blog post]("http://marpoz.blogspot.com/2012/01/ubuntu-on-macbook-pro-82.html")
[/LIST]

Thank you for taking the time with this mpodroid - really good job. I noticed you didn't mention rEFIt, did you dual boot?

---

### Post by mpodroid on 2012-01-09
You're right: I forgot to mention that I'm dual booting using rEFIt, booting ubuntu in BIOS mode.

I had to create free space on disk for ubuntu partitions. I wasn't able to do it using "DiskUtility" in OSX due to an issue with volume umounting. 

I've been successfully under OSX with command line "diskutil", which resized my OSX partition on the fly, while still mounted.

Marco

---

