---
title: "Deleting a user - I did something stupid..."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by eyemou on 2007-08-14
Wow, did I ever do something stupid...

I was creating users for an ftp server, and wanted to delete one... well, my brain sneezed or something, and I inadvertently deleted my main system account!! Since I can't sudo ("uid 1000 does not exist in the passwd file"), any ideas as to what I can do?

Man, do I feel stupid.

---

### Post by eyemou on 2007-08-14
Is there a way to use the 'root' account? Normally, I'd just use my suer account with 'sudo', but I don't remember ever using root in kubuntu...and I am a little leary of rebooting until I have a better handle as to what needs to be done.

Any insight is GREATLY appreciated.

---

### Post by Blutack on 2007-08-14
Reboot and select recovery mode from grub menu.
type
adduser 'yourusername' admin

Now reboot, log back in and use Gnome Users and Groups to cleanly add yourself a new system administration user, which will then be your main account.

---

### Post by eyemou on 2007-08-14
I'll give that a try -- thanks!

I'm running kubuntu, but I imagine this will work... (in other words, I'd use kcontrol instead of the gnome users/groups).

---

### Post by Blutack on 2007-08-14
Should be fine.

---

### Post by eyemou on 2007-08-14
Yup -- that worked! Thanks a million.

For anyone else who happens to do this (I can't be the only one!), you'll want to first:

adduser *username*

then 

adduser *username* admin

---

### Post by Blutack on 2007-08-14
Ooh, sorry!  I meant add your existing username (the one you were using that didn't have sudo rights) to the admin group.  I didn't phrase myself properly I guess.  Your command created a new user and then added him/her to the admin group.
Glad it worked though!

---

