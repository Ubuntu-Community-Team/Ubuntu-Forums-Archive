---
title: "vmware error unable to power virtual machine the operation ended in an error end....."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by sirab on 2007-05-28
of error message... the most helpful error message ever!

Anyway how can I fix this?

---

### Post by Orion2014 on 2007-05-29
Yeah, I am also having this problem. If anyone finds or knows of a fix please post.

---

### Post by starcraft.man on 2007-05-29
Just a question, but did you two recently upgrade to the new kernel (x.x.20.16)?

I ran into the same trouble (I think) where my VMware workstation refused to launch (it loaded the minimized app and then the busy icon appeared on my cursor and then dissapeared). I thought I had messed up my install for it, so I reran my install and overwrote it, I realized half way through that I had forgotten VMware configures itself for your specific kernel (thusly, refusing to run on the new kernel due to changes I assume). So its really easy, just rerun the install script and overwrite your install, all your config files will be preserved as will the virtual machines. Theres probably a command to just recompile/config it for the new kernel, but it eludes me now.

That should do it... hope it works out for ya both. Have fun :).

---

