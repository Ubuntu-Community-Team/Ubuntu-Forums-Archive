---
title: "Add/remove programs hangs"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-05-20
I'm installing ubuntu on a co-workers desktop and all went well

I went to install ubuntu-restricted-extras via add/remove and it is hanging waiting to connect to macromedia to download flash (it must be being blocked by a firewall0

Now the problem is, i can't use add/remove for anything until it installs flash, as it tries this no matter what package i'm trying to install.

How can i make add/remove not check for this download and act as if ubuntu-restricted-extras was never checked to be installed.

I've tried sudo dpkg --configure -a, but that also tries to download it from macromedias site.

Any suggestions so I can finish installing software and have him install the restriced extras when he gets home (it won't be blocked by a firewall then)

thanks

---

### Post by Pragmatist on 2007-05-21
Edit /etc/apt/sources.list file and just comment out that one repository by putting a # in front of the line.

---

