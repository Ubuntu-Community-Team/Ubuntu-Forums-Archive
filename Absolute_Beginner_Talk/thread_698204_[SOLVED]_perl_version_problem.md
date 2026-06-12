---
title: "[SOLVED] perl version problem"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Scut_Farkus on 2008-02-16
Greetings!

I've been trolling around, trying to find an answer to this problem, but so far I haven't had any luck.  I AM learning how to interpret error messages, though.

It looks like I've got a perl version problem, but I'm not sure how to fix it.  I've done several things, (based on some help from people here), but nothing has worked.  Now that I have a proper title for the thread, maybe someone else can give it a shot?

The problem started when I tried to use Update Manager.  It seems to have broken perl by attempting to install a new version.  Everything I've tried to fix it has failed.  Here's the latest attempt and it's results:

ed@ed-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of perl:
 perl depends on perl-modules (>= 5.8.8-7ubuntu3.1); however:
  Version of perl-modules on system is 5.8.8-7ubuntu3.
dpkg: error processing perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 perl
ed@ed-desktop:~$ 

If I'm reading this right, it looks like it's telling me that perl-modules needs 3.1, but the system only has ver. 3 (which is why I'm trying to upgrade it!) :)  

Any help would be greatly appreciated!  I'm here, in front of the computer.  I'll try anything and get back to you with results right away.

Thanks a lot, everyone!

---

### Post by mattismyname on 2008-02-16
I would try launching Synaptic and clicking the "mark all upgrades" button and then applying the changes.  I've had that fix issues like this in the past...

---

### Post by Scut_Farkus on 2008-02-16
> **mattismyname said:**
> I would try launching Synaptic and clicking the "mark all upgrades" button and then applying the changes.  I've had that fix issues like this in the past...

Thanks for trying, but I've attempted that.  Here's what I get:

"You have broken packages. The the broken packages filter to fix them."

Turns out the broken package is perl.

When I mark it to reinstall it, I get this:

E: /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu3.1_all.deb: corrupted filesystem tarfile - corrupted package archive

The details in the terminal are very similar to details in my original post.  It's a dependency problem.

Thank you for trying though! :)

---

### Post by mattismyname on 2008-02-16
Try blowing away all of the files in /var/cache/apt/archives/ and then doing the reinstall.  The error seems to suggest one of the files there is corrupted.

I have to clean those files out every so often anyway to free up diskspace.

---

### Post by Scut_Farkus on 2008-02-16
Oh my gosh!

I think that worked!  I could've SWORN I already tried that, but perhaps I did something else that returned the corrupted file?  Anyway, the broken package is fixed and it looks like it was replaced with the 3.1 version!  I've now marked all the other updates for installation!

Oh, I only removed the one file, not everything in the archive.  I was afraid to get rid of everything yet.

Here's what I did:

sudo rm /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu3.1_all.deb

Then I clicked on the broken filter in Synaptic and marked perl for re-installation.  It fixed it and now I can apply the other updates!  WooHOO!

Thanks!

I'll be sure to mark this as solved as soon as the updates are finished.

---

