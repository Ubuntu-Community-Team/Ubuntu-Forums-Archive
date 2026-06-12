---
title: "How to acces my OWN hard drive."
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by keantoken on 2008-03-20
Hi. 

I installed ubuntustudio a while back but have been sticking to win2k because of very annoying and troubling issues. 

Mainly, I have no privileges. I am sharing a partition with win2k, and I need access to ALL of my files, not just the ones on my windows partition and not just the ones on my linux partition.

I can do this, of course, if I go into recovery mode via the grub boot loader, input my username and password, and log on as root, after watching the numerous error messages fly by faster than I can understand their meaning. After this, I go into the X server into an old and somewhat unfamiliar user account, supposedly with root privileges, though I still have to type in some ridiculous code in the terminal each and every time I log on to root and want to have full read/write/delete privileges.

Now, mind you, I do love linux, but it is not anywhere as efficient a solution as windows if I cannot access any files without having to type in some 'intuitive' pattern of strange mnemonics. 

I do not wish a full explanation, if possible, please just give me a reliable link on Ubuntu Linux and how to AT LEAST be able to access all files with all privileges on the linux partition WITHOUT having to log on a root.

Sorry if this seemed a bit abrasive, bu tat its current state, ubuntu is not as intuitive a solution as windows. Thank you for your time.

Note: I have searched, but all I found was how to modify files belonging to root. Unfortunately, I am going to be constantly modifying files of these type, as I am installing various tools for my future linux endeavors. So, even though sudo works great, I like using the file browser GUI. No I'm not a command-line phoeb, I just don't want to have to use it for everything.

 - keantoken

---

### Post by insane_alien on 2008-03-20
sudo su will make you root.

use with caution, you can and probably will mess something up.  there is a reason for not giving you root by default. it limits damage. its poor security policy to run as root all the time. it is also one of the reasons there are practically no viruses(no totally destructive ones anyway) and why on windows a virus can delete EVERYTHING.

---

### Post by Captainm on 2008-03-20
Just press alt+F2 and type gksudo nautilus. This will give you a file manager with root privileges. It is really easy to botch your system this way though so be careful.

---

### Post by kpkeerthi on 2008-03-20
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Use that driver in windows to access linux partition in an intuitive way

---

### Post by scramasax on 2008-03-20
> **keantoken said:**
> ... access all files with all privileges on the linux partition WITHOUT having to log on a root.

Isn't that a bit like saying, I'd like to be able to lay my hand on any item in my house without having to unlock the door first?

Of course, you *could* leave the door unlocked, but if you did you'd make it easier for anyone else to walk in there and take your stuff -- or grab items that would help them impersonate you, steal your identity, empty your bank account, or anything else ... or set booby traps for you in your own house for the matter of that.  But it's a pain every time you need to find your key, of course.

There's a trade-off between security and ease of use, which is why we fit locks to front doors.

If there are particular files you need to access from both machines, you might honestly be better to keep those files on an external hard drive or network-attached storage or something.

---

