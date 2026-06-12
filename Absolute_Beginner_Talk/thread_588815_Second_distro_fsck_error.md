---
title: "Second distro fsck error"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by berZirker on 2007-10-23
I've checked a bunch of the other post, and I have used "the almighty google" and didn't find something that I thought was a safe bet to try.  Sorry if I missed something, just point me to it.  Here is my current partition scheme: hda1: (primary) windows, hda2: (primary) linux /boot, hda3 (extended), hda5 (logical) slackware theoretically, hda6 (logical) ubuntu root, hda7 (logical) linux swap, hda8 (logical) shared /home theoretically.

When I tried to install slackware, I told it not to use lilo but pointed it to hda2 which was the ubuntu boot.  (probably my first error.)  I put the root on hda5 and tried to point the /home to hda8.  Now when I boot slackware doesn't show up as an option (I think I may have found a way to fix this though.)  and when I load ubuntu it outputs the following error (pared down to what I thought was important):

```

*checking file systems...
fsck 1.40.2 (12-Jul-2007)
/dev/hda2 clean
/dev/hda8 clean
fsck.ext3 Unable to resolve 'UUID=01a69622-f494-435f-9a34-9f066ae4609c'
fsck died with exit status 8

* File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
* A maintenance shell will now be started

```

I think ubuntu just needs to realize that hda5 is another distro, and I need to get slackware on the grub.  I read somewhere this second thing might require a second /boot partition?  Any help or pointers are appreciated.

---

### Post by carlosfocker on 2007-11-04
Thats one crazy partition setup.  I would try to restore grub by looking into this post.  
[URL="http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub"]
http://ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub[/URL]

Please make sure you backup any important data before you do anything though.  Don't want to see any sad faces on your next post.

---

