---
title: "what does this mean?"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-03-21
Im new to linux and I get this whenever I try and apt-get install any packages....

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
 any ideas?

Thanks

---

### Post by seoatway on 2006-03-21
Are you using Apt with sudo to get root privileges ? try sudo apt-get and give it the root password.

---

### Post by trent dillman on 2006-03-21
I bet you're trying to use dpkg or apt-get while synaptic is open. Close synaptic and try again.

---

### Post by tommy1987 on 2006-03-21
im now getting this: 

Reading package lists... Done
Building dependency tree... Done
Package nvidia-settings is not available, but is referred  to by another package.
This may mean that the package is missing, has been obsol eted, or
is only available from another source
E: Package nvidia-settings has no installation candidate

im following an installation guide here: [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Swab on 2006-03-21
most likely you dont have all the right repositories enabled..

---

### Post by tommy1987 on 2006-03-21
how do i go about enabling the right repositories, for someone who doesnt even know what one is, excuse my ignorance!

---

### Post by Swab on 2006-03-21
I think the process is explained on the web site you linked to.

Edit:  Keep in mind that ubuntuguide.org provides insturctions for hoary, a previous Ubuntu release.   So, don't go adding hoary repositories, replace the word hoary with breezy.

---

### Post by trent dillman on 2006-03-24
or try [http://ubuntuforums.org/showthread.php?t=149510](http://ubuntuforums.org/showthread.php?t=149510)

---

