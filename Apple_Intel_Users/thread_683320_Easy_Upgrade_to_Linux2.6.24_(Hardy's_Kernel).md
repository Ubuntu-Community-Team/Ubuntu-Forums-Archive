---
title: "Easy Upgrade to Linux2.6.24 (Hardy's Kernel)"
date: 2008-01-30
forum: Apple Intel Users
---

### Post by cyberdork33 on 2008-01-30
For those wanting to get a newer kernel without compiling, there is a good how-to located here:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

There is even a python script to do it for you if you rather.


This may not include the the specific patches needed for the newest Macbooks (Santa Rosa), but can be obtained here:
[http://ubuntuforums.org/showthread.php?t=610375](http://ubuntuforums.org/showthread.php?t=610375)

---

### Post by incubus on 2008-01-31
Hey cyber,

Do you know if the new kernel includes patches for the Fn key?  (In my case, for the wireless keyboard, but I assume this is a general problem.)  I don't think so, but thought I might as well ask.

incubus

---

### Post by cyberdork33 on 2008-01-31
> **incubus said:**
> Hey cyber,

Do you know if the new kernel includes patches for the Fn key?  (In my case, for the wireless keyboard, but I assume this is a general problem.)  I don't think so, but thought I might as well ask.

incubus
I don't know. I have an iMac and use the white full keyboard which has always worked. According to [this]("http://ubuntuforums.org/showpost.php?p=4205205&postcount=155"), it is possible that some patches have been merged into the Hardy kernel already. You can always try it out, and revert to the older kernel if it is no good (it won't remove the old kernel, you just have to select it at startup, then remove the hardy kernel). There are instructions for removing the newer kernel in the how to I linked to.

---

