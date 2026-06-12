---
title: "Files disappear for no good reason"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by chadk on 2007-06-19
I have some directories that come up completely empty all of the sudden.. namely downloaded files.  I go into a directory and see, say, 10 files last night.  Today when I look for those files, there's nothing in that directory.  I've also had random scripts that I've created go missing.  

Is there anywhere I can check to see what's going on?  Do I have a hard drive going bad? - How does one check that?

---

### Post by DerArzt on 2007-06-19
you might consider checking the lost+found directory on the partition that this is happing on

---

### Post by candtalan on 2007-06-19
> **chadk said:**
> I have some directories that come up completely empty all of the sudden.. namely downloaded files.  I go into a directory and see, say, 10 files last night.  Today when I look for those files, there's nothing in that directory.  I've also had random scripts that I've created go missing.  

Is there anywhere I can check to see what's going on?  Do I have a hard drive going bad? - How does one check that?

It is maybe a bit way out: but be aware that if you use a directory as a mount point, then the original contents of that directory are not visible until you unmount the overlay stuff.

---

### Post by chadk on 2007-06-20
> **candtalan said:**
> It is maybe a bit way out: but be aware that if you use a directory as a mount point, then the original contents of that directory are not visible until you unmount the overlay stuff.

Use a directory as a mount point?  Not sure what that means so I don't think I've done that.  I can see some files in a directory but others just go missing.  Strange. -- I'll check the Lost+Found directory.. if I can find that ;)

---

### Post by spivee69 on 2007-06-20
You might also consider using fsck to check the mount point.  You can google fsck to get some good syntax.  Just a word of caution, you never want to fsck a mounted drive.  If the mount point that's being affected is your root drive, you should see about booting off of a cd or floppy.

---

### Post by atria on 2007-06-20
Did you experience a power outage/crash? Because some filesystems (more specifically XFS and JFS) can experience data loss upon a sudden shutdown.

---

