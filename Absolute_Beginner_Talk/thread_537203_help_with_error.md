---
title: "help with error"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Caton420 on 2007-08-28
i get this error or atleast somthing close everyday when installing apps ect...
```
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
caton420@caton420-laptop:~$ 


```

---

### Post by deadgobby on 2007-08-28
Are you installing a  tar ball package or deb package? This package can be found in synaptic. Are you getting the same error in the script when installing  from synaptic?
Gobby

---

### Post by Caton420 on 2007-08-28
im sorry about the last post it was unfullfilled with any info, that is my wirless card yet it works... but i get the error ALL THE TIME
im tring to get firestarter via command line

---

### Post by TerranFury on 2007-08-31
I had been having the same problem, and I think I just fixed it.

First, my educated guesses about what's going on are as follows:

 1 - The fwcutter package configuration scripts, which are supposed to be run automatically by dpkg, fail because of a 404 error (they try using wget to download some firmware, but the URL in the install script is bad).  Because the fwcutter configuration fails, it is left in the dpkg database as "half-configured."

 2 - Whenever you try to install another package, dpkg tries to configure any half-configured packages that exist in its database.  So what happens is, every time you install something, dpkg tries again to run the dpkg configure scripts, and, because of #1 above, it stays "half-configured," so that, the next time you try to install something, you'll get the same problem.

So all you need to do is tell dpkg, "Hey, don't worry about configuring fwcutter.  I've done it myself; consider it installed."  The way I did this was to edit /var/lib/dpkg/status by hand (make a backup first).  Find the line that says "Package: bcm43xx-fwcutter."  It will look something like this:

```

Package: bcm43xx-fwcutter
Status: install ok **half-configured**
--other stuff--

```

Change that to,

```

Package: bcm43xx-fwcutter
Status: install ok **installed**
--other stuff--

```

I wouldn't be surprised if there's a way to do this with dpkg, and if there is, I'd probably prefer that (Let programs manipulate their own data whenever possible!  It's a basic abstraction sort of principle).  Nevertheless, my solution probably does whatever dpkg would have done if I'd known how to use it, and it seems to fix the problem.

Cheers.

---

### Post by zachalekos on 2007-08-31
Great, Your solution is flawless.

---

