---
title: "Interrupted Software Update"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by gblakeman on 2006-09-24
Hi, a while ago I accidentally interrupted the software update process. My computer can boot up and operate just fine, but when I try to update software through the update software utility I get the following error:

"Only one software management tool is allowed to run at the same time
Please close the other application e.g. 'aptitude' or 'Synaptic' first."

I don't think I have anything else open, but the system think I do. Any ideas how to get Software Update working again?

Thanks!

---

### Post by LookTJ on 2006-09-24
try "sudo aptitude update && sudo aptitude dist-upgrade" but don't open Software update

---

### Post by Zyzzyx on 2006-09-25
I had a similar problem for awhile. As I remember, I tried doing aptitude from the command line, got the same message. Waited for awhile and let it be, and then the Upgrade Manager came up from somewhere deep in the backgroud with the rest of its goodies to install. Finished that off and it was fine. So, it could be that the update manager IS running, you just can't get to it yet. Give it some time to settle out.

---

### Post by Marsolin on 2006-09-25
You may need to remove the /var/lib/dpkg/lock file. You will need to use sudo to do it. A lock is created so only one package manager can update the system at a time.

---

### Post by gblakeman on 2006-09-25
Thanks so much! This did the trick.

---

