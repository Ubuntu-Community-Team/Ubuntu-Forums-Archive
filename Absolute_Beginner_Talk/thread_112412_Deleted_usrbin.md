---
title: "Deleted /usr/bin"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by Klumpeduns on 2006-01-04
I had a friend(/idiot) who managed to delete /usr/bin, and I'm wondering if                  someone could tar their /usr/bin and send it. I tried from a debian-dist, but some of the binaries complain of libs (obviously). I'm running hoary.

Thanks

Klumpeduns

---

### Post by KingBahamut on 2006-01-04
ouch.....

You can try to do that, but I think your still looking at a reinstall. 

If Im not mistaken rm /usr/bin -fr , which would be the way you could delete the folder and its contents, would also break all symlinks as well.

---

### Post by earobinson on 2006-01-04
what I want to know is why he had root axcess in the first place... I assume the could be fixed with a life cd but im not sure how.

---

### Post by Klumpeduns on 2006-01-04
Yes, the symlinks are gone as well, but the system still works more/less. The
problem is that some binaries don't work because of missing libraries. (like apt-get).
The "friend" deleted it all thinking he was in a chroot on the system. (which he
quite obviously wasn't)

Thanks

Klumpeduns

---

### Post by bonzodog on 2006-01-04
oh dear. oh dear. oh dear. 
I'm afraid he is looking at a re-install to get the system back properly.
I've avoided chroot on my 64 bit box because it was dangerously close to the the main dirs.

---

### Post by Klumpeduns on 2006-01-04
Could someone just tar me their /usr/bin/apt-get? (preferrably someone running
hoary) So that I could at least get apt-get running.

Thanks

Klumpeduns

---

