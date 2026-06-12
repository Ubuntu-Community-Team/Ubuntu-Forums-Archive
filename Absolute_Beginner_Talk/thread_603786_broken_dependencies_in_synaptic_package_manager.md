---
title: "broken dependencies in synaptic package manager"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by drravshan on 2007-11-05
hi,
have been exploring ubuntu 7.10. now i am getting error msg whenever i access synaptic - says there are broken dependencies & to correct it first. searched a few posts on the subject but no success.
when i tried the following command ~$ sudo apt-get install -f, got the msg  E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
on command ~$ sudo dpkg --configure -a, the response is dpkg: status database area is locked by another process
ravi@ravi-desktop:~$ sudo dpkg -P --force-remove-reinstreq linux-headers-2.6.20-15
dpkg: status database area is locked by another process

looking for help
thanks
ravi

---

### Post by bump_ on 2007-11-05
Hello

Make sure you have closed synaptic before you try any "apt-get" or "dpkg" commands.

After you close synaptic, apt-get install -f should fix the problem.
Hope it helps.

---

### Post by drravshan on 2007-11-05
hi bump,
thanks for the reply.  deleted the broken file KDElibs. is it essential??
ravi

---

### Post by bump_ on 2007-11-05
I beleive it is since it contains all the core libraries needed by Kubuntu.

Does "sudo apt-get install kdelibs" work?

---

### Post by drravshan on 2007-11-05
hi bump,
the command gave the response - Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ravi

---

### Post by bump_ on 2007-11-05
Hmm... this happened to me a while back. I think i fixed it using 

"apt-get install -f"

Try using that again and post what comes up

---

### Post by squirage on 2007-11-06
Hi I am getting something similar,

  It appears that I have broken dependencies for kdenlive and ```
sudo apt-get install -f
``` just returns a list of failed attempts to overwrite mlt and mlt++ and finish with the line```
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

In synaptic the broken dependencies filter points straight to kdenlive, but it fails when I try to re-install or completely remove and gives the same mlt lib errors.

I'm going to try ```
sudo apt-get --purge remove mlt mlt++ kdenlive
``` and see what I get.

---

### Post by Linuxratty on 2007-11-06
Did it work?
My update manager also has died.
 I'm getting this message:


EDPKG was innurupted You must manually ryn dpkg config ar to fix the problem. Huh
E _cache >open () failed.please report.

This is my second day with Ubuntu and I'm at a loss as to how to fix this.

---

### Post by squirage on 2007-11-06
Hi Linuxratty,

  In a word yes. For me running synaptic and using the broken dependency filter verified that kdenlive was the issue.

Trying to remove through synaptic would only give similar errors about trying to re-write the mlt lib files.

```
sudo apt-get --purge remove {whatever you determine is the problem stuff}
```

In my case it was  mlt mlt++ kdenlive

I then rebooted and ran my update manager normally.

Now back to fixing the original problems, some of which I had fixed in Feisty that don't work again now in Gutsy.

Good Luck.

---

