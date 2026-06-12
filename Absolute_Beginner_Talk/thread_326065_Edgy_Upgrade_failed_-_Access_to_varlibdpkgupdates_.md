---
title: "Edgy Upgrade failed - Access to /var/lib/dpkg/updates denied to root"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by OldSeaDog on 2006-12-26
When I try to upgrade to distro to edgy, or upgrade the existing distro, or even install or delete an app,  It fails.  The error message says that permission to access to /var/lib/dpkg/updates is denied.  The directory does not exist and I can't even create it (permission denied).  I have rebooted into maintenance mode and tried it - same result.  In fact I have tried just about evrything I can think of in the 'simple' category, including creating another directory and renaming it, creating a directory in my home directory and soft linking to it.  At that point I just wanted to create it, or even fake it - same result.

Without trying to flower up my request for help I figure a simple question mihjt suffice.  Does anyone have an idea of what I can try next?  This is immensely frustrating.

I  am running it on an Acer Aspire 3003WLMI and have set it up dual boot (but at one point the windoze partition stopped being shown in the boot screen and I haven't bothered rewriting it _ I have had other priorities.  The division is pretty much 50/50 on a 60 GB hard drive.  83% is in use.  It has 1 GB of RAM.

The specific message is:
'dpkg: Cannot scan updates directory 'var/lib/dpkg/updates': Permission denied.
E: Sub-process /usr/bin/dpkg returned an error code (2).

OldSeaDog, The Geekasaur

---

