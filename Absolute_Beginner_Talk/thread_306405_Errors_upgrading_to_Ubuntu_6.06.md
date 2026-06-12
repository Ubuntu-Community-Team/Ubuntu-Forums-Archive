---
title: "Errors upgrading to Ubuntu 6.06"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by johndavidthacker on 2006-11-24
I have been trying to upgrade to Ubuntu 6.06 LTS from the Update Manager, but I keep getting the same error message:

Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz) Unable to fetch file, server said 'Failed to open file.  '
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz) Unable to fetch file, server said 'Failed to open file.  '

Any suggestions? I've been trying off and on for weeks.

---

### Post by taurus on 2006-11-24
I recommend you comment out by placing a # in front of that line (or those lines), [ftp://ftp.free.fr/pub/](ftp://ftp.free.fr/pub/), in your /etc/apt/sources.list first before you attend to upgrade to Edgy...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by johndavidthacker on 2006-11-25
That worked. And 14 hours later, 6.06 was installed. I like the faster boot up speed and I can finally play DVDs in Linux. One problem, though: I'm getting an error in the panel related to etc/apt/sources.list. When I try to run Add/Remove I am told:
> Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

When I browse to etc/apt/, I see that sources.list and five other files have their permissions set so that they cannot be read. When I try to change the permissions in Nautilus, I am told that I am not the owner and cannot change the permissions. Is this the result of editing the file before upgrading? What should I do next? I can open sources.list from the command line using sudo, but I don't know how to change its permissions.

---

### Post by johndavidthacker on 2006-11-25
After some trial and error, I was able to run nautilus with 'gksudo nautilus' and change the permissions that way. Problem solved. For now.

Thanks Taurus

---

