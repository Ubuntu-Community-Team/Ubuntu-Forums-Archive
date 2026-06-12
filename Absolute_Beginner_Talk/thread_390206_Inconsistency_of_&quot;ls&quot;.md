---
title: "Inconsistency of &quot;ls&quot;"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by alphilli on 2007-03-21
I have a set of files in a subdirectory of /home/name/x/y.

If I do a cd to /home/name/x/y and issue "ls" I see a different set of files than if I issue the command "ls /home/name/x/y".  

Certain files ("Makefile" for one) just don't show up when I issue the command "ls /home/name/x/y" but they show up if I issue the command "ls" (with no parameters).

What gives here?

---

### Post by overdrank on 2007-03-21
> **alphilli said:**
> I have a set of files in a subdirectory of /home/name/x/y.

If I do a cd to /home/name/x/y and issue "ls" I see a different set of files than if I issue the command "ls /home/name/x/y".  

Certain files ("Makefile" for one) just don't show up when I issue the command "ls /home/name/x/y" but they show up if I issue the command "ls" (with no parameters).

What gives here?

Hi well maybe some of the file's are hidden files. When you use a different command you can see them? Just a thought.:-k

---

### Post by ricardisimo on 2007-03-21
Remember that Ubuntu is case-sensitive, so for example, "Desktop" is a different directory from "desktop" with, obviously, different content.

---

### Post by alphilli on 2007-03-22
It turns out that rebooting fixes the problem though one would hope that it is overkill. 

I have no idea why the directory would not always get officially updated when a new file is created but I guess there's some cache that gets used when doing an "ls" with an absolute path whereas when "ls" is issued specifying no parameters it really does look at the directory.  Also, the file browser seems to look at the out-of-date cache.

I would think it would be pretty important to actually update the directory every time a file is created and always go to the same place when retrieving the contents but I guess efficiency is more important.

---

### Post by lloyd_b on 2007-03-22
> I have no idea why the directory would not always get officially updated when a new file is created but I guess there's some cache that gets used when doing an "ls" with an absolute path whereas when "ls" is issued specifying no parameters it really does look at the directory. Also, the file browser seems to look at the out-of-date cache.

I would think it would be pretty important to actually update the directory every time a file is created and always go to the same place when retrieving the contents but I guess efficiency is more important.

Exactly which kernel version are you running? 
```
cat /proc/version
```

Also, can you provide a series of steps to duplicate the problem?

Simply put, this should NOT be happening.  Linux does implement a "dcache", which caches file/directory information, but anytime that a file/directory is updated, the associated dcache entry should be invalidated.  I've never experienced the situation you've described, and I've been trying to duplicate it on my machine without any success.  

So I'm wondering if it's a bug with the particular kernel that you're running.

Lloyd B.

---

### Post by alphilli on 2007-03-24
Version info:

Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic

I think it can be reproduced ***only ***on a new installation of Linux before a reboot has been done.

The steps It took are:

1. Installed Linux as the only operating system on an older Intel P4 machine - reformatted the harddrive.

2. Downloaded Xerces source from apache.org.

3. Extracted the source files into: /home/alphilli/Xerces.

4. Executed "./runConfigure"  in the directory:
    "/home/alphilli/Xerces/xerces-c-src_2_7_0/src/xercesc"

5. The previous step created the file: "Makefile".

This is where the problem showed up - Makefile was visible with the simple command "ls" but it was not visible with the command:
 "ls /home/alphilli/Xerces/xerces-c-src_2_7_0/src/xercesc"

After the first reboot everything seemed fine.  Maybe I should have known that a reboot was required after installation.

---

### Post by lloyd_b on 2007-03-24
> I think it can be reproduced only on a new installation of Linux before a reboot has been done.

That's still a bit odd, but not as serious as I had thought (I misunderstood your previous messages and thought that it was an ongoing issue, not a one-time case).

For anyone else who experiences this situation, try "sudo sync" in a terminal window and see if that corrects the problem.

Lloyd B.

---

