---
title: "shared home between ubuntu and mac"
date: 2010-11-30
forum: Apple Hardware Users
---

### Post by kitkat12012 on 2010-11-30
I read about moving ubuntu's /home and mac's /users directories to an external partition so both ubuntu and mac can share the same home directory.

I'm interested in this setup (or soomething similiar) in which the personal folders (music, documents, desktop, etc..) are shared between the two

I was wondering, are there any pros/cons in using the shared external home concept?  Also, any pros/cons to just using symlinks instead?


Basically I'm looking for the most seamless way to share the personal folders between the two in a dual boot setup.


Thanks
Thanks

---

### Post by pindar on 2010-12-01
I haven't actually tried it, but sharing the entire /home/you and /Users/you directory might be problematic for a number of reasons:
[LIST=1]
[*]You need a filesystem that is writable in both OS X and linux. Not easy, the only viable choice would be hfs+ unjournaled, which puts you at risk in case of a system crash.
[*] Many applications write their config files into your home directory. When you use the same applications in OS X and linux, they will overwrite each other, and you'll run into subtle differences (as an example: my .emacs for linux has a different mechanism for defining its fonts than the one in OS X.
[/LIST]
So I would go for the symlink way. It will still pretty much leave you with problem 1, but for a shared data directory (for which you certainly have a backup), this may be less important. I have something similar: on my external disk, I have several linux distributions. All my own files are on a separate partition and I use symlinks. Has been working quite well for a while now.

---

### Post by gforster on 2010-12-01
Here's a timely article that deals with this very subject

[A Comprehensive Guide to Sharing Your Data Across Multi-Booting Windows, Mac, and Linux PCs]("http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems?skyline=true&s=i")

---

### Post by srs5694 on 2010-12-02
As a general rule, unjournaled filesystems are no less safe than a journaled equivalent; the journal just speeds up disk checks after a system crash. Thus, the only risk of going with an unjournaled version of a filesystem is that you're likely to have to wait longer for a disk check after a system crash or other uncontrolled filesystem removal. That said, I don't know if there's anything unusual about HFS+ in this respect.

It's possible to share a /home (or /Users in OS X) partition but maintain separate user home directories. The easiest way to do this is to use different usernames in each OS, but it's also possible to do it by mapping the usernames to the home directories in something other than the default way, typically by using usermod to change these details. Of course, if you do this you'll have to create symbolic links if you want to use the standard file locations (~/Music, etc.) in both installations.

Note that you'll have user ID (UID) and group ID (GID) issues, since Ubuntu and OS X begin numbering their users differently. It's easy enough to synchronize them, but you have to be aware of the issue and know how to use usermod (or create a new account in one or the other OS to be properly synchronized).

---

