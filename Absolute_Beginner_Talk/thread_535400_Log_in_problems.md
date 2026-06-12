---
title: "Log in problems"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Firequacker on 2007-08-26
I installed Ubuntu7.04 the 64 bit version and it worked fine for about a week, but then I realized my  username wasn't set up so that I could do a lot of things, and that I had to log in as root. So I tried doing that, and I couldn't and apparently I needed to edit my login settings. I did, and then I rebooted and now when I try to log in as root or just my normal account it goes through a couple of screens, then the loading icon for the mouse stays there for hours and it never loads. I'm trying to see if I can undo those changes in the settings without actually logging in.... HELP! (by the way, I tried erasing the partition and installing it again, but on the 4th installation screen it said "no root directory somenthing something" and I don't know what that means... so yea.)

EDIT: I can boot directly from the cd just fine, if that information helps at all.

---

### Post by jamvegan on 2007-08-26
You should be able to log in to a root shell by booting into recovery mode (which should be the second option in your GRUB menu, if you haven't edited that).  If you don't know how to proceed from there, post what you did to cause the problem and we should be able to help you undo it. :-)

Also, if I am understanding correctly what your original issue was, you should probably take a look at the community documentation on [RootSudo]("https://help.ubuntu.com/community/RootSudo").  Basically, Ubuntu does not have a root login by default.  Instead, the first user created during install (and any other user who is given admin privileges) can run a command that would normally require root by putting "sudo" in front of the command.  For instance:
```
sudo ls /var/lib/slocate/
```
You then enter your own password (the one that you use to login) and the command is run as though you were "root".

---

