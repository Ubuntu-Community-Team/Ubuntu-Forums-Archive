---
title: "[SOLVED] Updating Software"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by skwon11 on 2007-12-24
Very beginner question...

I just that the new version of GThumb now support thumbnailing for videos which is great for me.  Question I have is that is just a matter of going to the site and downloading the new version?  Dumb question I know but in Windows often times doing this will put both the old and new versions on my computer... something I am trying to avoid.  Thank you.

---

### Post by SOULRiDER on 2007-12-24
I think it would be a good idea to read this.
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

If there is a DEB file for Ubuntu on their site, install it, it will overtwrite the old one, you wont have 2 versions of the same package like in windows :)
If there isnt a deb file you can do two things.
1- Compile it from source. Its not hard but its not that great for newbies.
2- Wait until its in the repositories and it will auto-update.

If you have the backports repo enabled you will probably get the update sooner.

---

### Post by mellowd on 2007-12-24
If it's in the repositories it's easy to check for an update like so:
```

sudo aptitude update
sudo aptitude safe-upgrade
```

This will check the repo's for any updated packages, then update them.

---

### Post by skwon11 on 2007-12-27
Thanks everybody,

No autoupdate available.  I found a .deb file to upgrade gthumb at filewatcher (gthumb_2.10.5-2_i386.deb) but when the package installer opens I get "Error: Conflicts with the installed package 'gthumb'".  Is there a reason it doesn't overwrite?

---

### Post by SOULRiDER on 2007-12-27
You could remove gthumb and then install with that package you downloaded.

---

