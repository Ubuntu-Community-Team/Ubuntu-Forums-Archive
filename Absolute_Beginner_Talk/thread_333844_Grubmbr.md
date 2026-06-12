---
title: "Grub/mbr"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by drake18746 on 2007-01-08
I recently turned of my computer which was running Ubuntu 6.06.  When I tried to boot it back up again, it told me that there was no operating system present.  I thought at the time that the harddrive had just finally given out, its an old drive, so I bought a new one and reinstalled Ubuntu, same version, on that.

Now, when I boot up, right after BIOS, it seems to hang.  I'm left with a black screen with only the blinking underline cursor.  I tried leaving it for an extended period of time after that once, over an hour, and it was still there after that.

So I'm wondering how to reinstall GRUB and fix the MBR, which I think is the issue.  I've looked at many other links on the forum and none of them seemed to help me (though that's probably due to my lack of understanding) so I'm kind of looking for the complete answer.  As in, not commands that I need to figure out on my own, but something more along the lines of "here, type this -exactly" (yes, I -actually- do need this much help with this).

Any and all help would be more than greatly appreciated.

---

### Post by riven0 on 2007-01-08
Have you looked [here yet]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")? These are step by step instructions.

---

### Post by drake18746 on 2007-01-08
I actually did.  That was the first and most recent page I actually looked at.

The one problem that I ran into was this:
find /boot/grub/stage1

It said that there was no such file or directory.  And when I tried mounting the drive like it said later on in the post (which I probably did wrong), it gave me errors then, too.

---

### Post by louieb on 2007-01-08
Hum new hard drive. Just a wild guess. Check the BIOS setup and see if hard drive detection is set to auto and mode is set to LBA. It may be that BIOS is incorrectly reporting the new drives geometry.

---

### Post by drake18746 on 2007-01-09
Thanks louieb!  I didn't do exactly what you said, I don't think.  I was just so fed up with the whole darn thing that I set BIOS to return to factory defaults.  And it booted with the old 20 gig drive, I swapped it for the new 100 gig drive and that loaded too!

Now all I need is (a lot of) assistance in copying everything from my 20 gig drive over to my 100 gig drive so the 100 is the main boot drive, and then setting up my illegally partitioned 300 gig drive so that Ubuntu can actually write to and read from it.  Any links/hints/tips on that?

---

