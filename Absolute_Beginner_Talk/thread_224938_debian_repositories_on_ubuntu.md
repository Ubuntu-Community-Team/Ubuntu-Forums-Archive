---
title: "debian repositories on ubuntu?"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by drosophyllum on 2006-07-28
just a quick noob question....
Are ubuntu repositories the same as debian repositories if not is it possible to add debian reopitories on synaptic?

thanks

---

### Post by benuski on 2006-07-28
> **drosophyllum said:**
> just a quick noob question....
Are ubuntu repositories the same as debian repositories if not is it possible to add debian reopitories on synaptic?

thanks

The Ubuntu repositories are not the same as the Debian repositories.  Since Ubuntu is based off of Debian, I'm sure they include a lot of the same packages, but many of them have been slighty (or more) rewritten by Ubuntu developers to fit even better into the Ubuntu system.

And sure, you can add the Debian repositories.  [This]("https://help.ubuntu.com/community/Repositories/Ubuntu") documentation page will give you all the info you need to know; all you`ll have to do is maybe hunt a little to find the repository link on the Debian website.

---

### Post by drosophyllum on 2006-07-28
thank you.

---

### Post by 5-HT on 2006-07-28
Just to add a note of caution that benuski hinted at: Mixing Debian and Ubuntu packages on your Ubuntu system is not advisable.

A few packages here and there may be ok depending on what they are, but installing a lot on your system, or just some specific ones, could lead to breakage.

---

### Post by az on 2006-07-28
> **benuski said:**
> 
And sure, you can add the Debian repositories. 

No.  Don't do that.  Ubuntu and Debian are *not* binary compatible.  Use source packages if you must.

---

