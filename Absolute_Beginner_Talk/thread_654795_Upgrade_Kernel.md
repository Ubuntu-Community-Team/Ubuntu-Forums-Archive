---
title: "Upgrade Kernel?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-12-31
In a bug report that applies to me and is very important, someone wrote this:

"All I did to get it working was fully upgrade the kernel. There was an update to 2.6.22-14 a couple weeks ago, and I decided to try it again and it worked this time."

How can I check to see which kernel I am using?

Is it easy/safe for me to upgrade mine being a novice?

---

### Post by (((X))) on 2007-12-31
Upgrading kernel is typical for servers, You will lose the ability to update ubuntu as far as I know. Why do you want to upgrade your kernel?

code:
$ uname -r

---

### Post by brandoncolorado on 2007-12-31
There is a bug that causes my laptop to freeze when connecting to a secured network, and I am worried about leaving my router unsecured (which I am doing for the time being).  Someone put that in the comments.  With that code, it shows I am running the same kernel though, so now I don't understand why the problem if fixed for him.

---

### Post by The Tronyx on 2007-12-31
> **brandoncolorado said:**
> There is a bug that causes my laptop to freeze when connecting to a secured network, and I am worried about leaving my router unsecured (which I am doing for the time being).  Someone put that in the comments.  With that code, it shows I am running the same kernel though, so now I don't understand why the problem if fixed for him.

I'm no expert on the matter, but there are 2 things to consider. Well there's actually more than 2 but I am referring to 2 in particular.  Updating your kernel can actually be automated, but it isn't just a simple update, you need to know what modules you want and a whole lot of other stuff.  I personally do not reccomend this for a beginner.  The automated service I am referring to is KernelCheck and you can read about it here:
[http://ubuntuforums.org/showthread.php?t=618563&highlight=update+kernel](http://ubuntuforums.org/showthread.php?t=618563&highlight=update+kernel)

Secondly, what is the exact problem you are having.  I see below that you cannot authenticate to a secured network and I am assuming this is wireless.  Can you provide more info about your wireless card and system information?  Also, could you please pastebin any error messages from your logs?  Where did you find the info about the bug?

Perhaps we can get this figured out in a way that doesn't involve updating your kernel.

---

### Post by brandoncolorado on 2007-12-31
Here is the bug that applies to my card:

[https://bugs.launchpad.net/ubuntu/+bug/152522](https://bugs.launchpad.net/ubuntu/+bug/152522)

Thanks for your help.

---

### Post by The Tronyx on 2007-12-31
Hmmm, if updating your kernel is the fix, you should refer to the master kernel thread located here first.  You could also read up on KernelCheck to simplify the process but make sure you know how to follow up on it.
[http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+thread](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+thread)

In my experience, if you have problems with the new kernel for whatever reason you can always boot the older one in GRUB.

---

### Post by brandoncolorado on 2007-12-31
Thanks, appreciate the help.

---

