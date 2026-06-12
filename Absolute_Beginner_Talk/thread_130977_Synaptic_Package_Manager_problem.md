---
title: "Synaptic Package Manager problem"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by snake1130 on 2006-02-15
Hello evrey one. I'm having a problems with my Synaptic Package Manager. It's trying to see the Repositores but for some resone it says 4 are done and the rest are "Hit". I can''t donwload and install any programs. It was working this morning, and yes i do have internet.


Any help would be appreceated.


P.S. I'm running lates and greates 64bit

---

### Post by cotcot on 2006-02-15
I think you explain 2 different things. Getting the message "hit" is normal. It means that the check for an update list is done and that there was no new list.
This should not lead to the unability of installing packages. So I think there is another reason that you cannot install packages.

If you open synaptic (sudo synaptic) and toggle "reload" (above left), do you get an error ? If yes and the repo with the error message is the one yoy want to get a package from then it will not be possible to install it.

---

### Post by Vengeful Cynic on 2006-02-15
I'm going to assume that you've done the whole resetting your computer and reloading your repositories... if not, now would be a good time to do that and re-check.   I'm gonna do some nosing around to see if there are any known reasons for something like this cropping up... I'll post here if I find something and I'll count on you posting here if something changes.

-Vengeful Cynic

---

### Post by snake1130 on 2006-02-15
i got this error

```
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)

```

and yes i did restart the computer... twice actuly  :mrgreen:

---

### Post by arctic on 2006-02-15
Go into terminal mode and run

sudo apt-get clean all

in order to clean your cache and all other junk. Then retry to install the packages. Any new error messages?

---

### Post by snake1130 on 2006-02-15
I still have the same error as befor. It won't load the last 2 sites it hangs on "8 of 10 files download". It loads all the security ones just not the others as you can see the errors from abouve.

---

### Post by arctic on 2006-02-15
In that case it might be a problem with the software-mirror and not with your computer.... just guessing though.

---

### Post by snake1130 on 2006-02-15
ok well thanks for trying. I'll contine u trying to figure this out.

---

### Post by veritas366 on 2006-02-15
No, it's not his computer.  This was happening to me since the Breezy update.  Now it doesn't happen anymore but it still lists even main ubuntu repos as "unverified".  I've seen other such complaints as well.  No solution to offer, I'm afraid, but you aren't the only one having such issues.

---

### Post by snake1130 on 2006-02-15
great....:-k

---

### Post by snake1130 on 2006-02-15
well I have narowed it down to anything with the "http://security.ubuntu.com" is the only thing that works every other site doen't... including wine :evil:

I need to no how to fix this... do i have to re-format and start over?

---

