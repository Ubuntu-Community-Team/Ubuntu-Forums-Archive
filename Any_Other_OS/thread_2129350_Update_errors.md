---
title: "Update errors"
date: 2013-03-26
forum: Any Other OS
---

### Post by Lupi on 2013-03-26
I get these errors when I try to update Linux Mint 13:

"Failed to fetch [http://ppa.launchpad.net/venerix/blug/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/venerix/blug/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/venerix/blug/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/venerix/blug/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/venerix/blug/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/venerix/blug/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead."

How can I solve this?

---

### Post by DuckHook on 2013-03-26
This simply means that the PPA doesn't exist. Go: Software Updater>Settings>Other Software and uncheck all boxes of the offending PPAs (in your case, anything having to do with "venerix"). Updates should now work.

---

### Post by Lupi on 2013-03-26
And it works. Thanks.

---

### Post by DuckHook on 2013-03-26
If new to Linux, in general, refrain from adding PPAs to your software sources except as a last resort for critical apps that you simply must have. Given the depth of the repos, PPAs are almost never necessary. PPAs are often the reason for broken/conflicting dependencies, download problems and security concerns. For example, PPAs owned by single individuals who don't have the time to maintain them will often break version upgrades. Once you are thoroughly familiar with how to fix broken dependencies, etc, then adding PPAs is less risky. And, as in all things dealing with security, be sure to read up on, Google, and ask on these forums before trusting a PPA and adding it to your sources list.

---

### Post by Perfect Storm on 2013-03-26
Moved to Other OS/Distro Talk. Marking thread solved.

---

