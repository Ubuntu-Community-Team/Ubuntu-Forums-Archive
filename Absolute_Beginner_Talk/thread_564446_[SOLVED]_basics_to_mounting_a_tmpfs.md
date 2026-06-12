---
title: "[SOLVED] basics to mounting a tmpfs"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by scorn on 2007-10-01
Hi All,

I would like to mount a tmpfs to be used for my /tmp/ folder, but it seems I am doing something wrong. I do the following:

1. I looked in my existing /etc/mtab file(the fstab has no tmpfs entries) and found the following entries and tried it with no success
   udev /dev tmpfs rw,mode=0755 0 0
   devshm /dev/shm tmpfs rw 0 0

2. So I tried the following:
   sudo mount /dev/shm /tmp -t tmpfs

3. Running the mount command reveals the following:
   /dev/shm on /tmp type tmpfs (rw), which, to means it was mounted.

Here is the catch, when the screen saver is invoked, you cannot close it as no pwd box is displayed, however if I go to a virtual terminal, and unmount the /tmp folder, all works fine again.

This may be a very basic question, but could someone please show me the correct command to mount a tmpfs as I have tried some examples from the web and had some success on a Redhat box......
   sudo mount none /tmp -t tmpfs

Thanks in advance.

---

### Post by scorn on 2007-10-04
Ok....So a bit more searching on the web I found the following links to be useful :

[http://forums.gentoo.org/viewtopic.php?t=268155](http://forums.gentoo.org/viewtopic.php?t=268155) (This is the solution I used)
[http://en.wikipedia.org/wiki/TMPFS#Linux](http://en.wikipedia.org/wiki/TMPFS#Linux)
[http://www.ibm.com/developerworks/library/l-fs3.html](http://www.ibm.com/developerworks/library/l-fs3.html) (This was a common link on all the pages I found, also good info).

My /etc/fstab now looks like this :

#Added by Scorn
#devshm         /tmp    tmpfs   defaults                0 0
#tmpfs          /tmp    tmpfs   defaults,noexec,nosuid  0 0
/dev/shm        /tmp    tmpfs   defaults,nosuid,size=256M,mode=1777   0 0

As you can see above, the first two attempts were edited out as the tmpfs did not work 100% (I could not cancel the screen saver when it started, only an unmount would work).

The one that worked uses the /dev/shm device, and only uses a size of 256M.

The full process was to edit the fstab file, added in the new values and then gave the machine a boot.
So far I have not had problems yet, I will keep an eye on it and close the thread should it work ok.

If there is anyone that can tell me if this is the correct procedure for a tmpfs, or gimme any ideas how else I can do it, it will be greatly appreciated.

Thanks 
Scorn

---

