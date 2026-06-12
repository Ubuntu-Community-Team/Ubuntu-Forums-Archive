---
title: "What's the difference between apt-get update &amp; apt-get upgrade?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Sporkman on 2007-08-10
apt-get upgrade doesn't seem to do much of anything, whereas apt-get upgrade seems to do much more.

Does apt-get upgrade = System->Administration->Update Manager->update?

That won't load a new Ubuntu release if one exists, will it?

-Thx

---

### Post by moffa on 2007-08-10
update contacts the servers to determine which programs have been updated where upgrade actually updates the software to the newest version

---

### Post by nisarg on 2008-03-07
I was wondering the same thing.
So what does synaptic package manager runs?
upgrade or update??

Cheers, N

---

### Post by herbster on 2008-03-07
Synaptic package manager is a GUI front-end for the apt-get package management. It's the same thing. When you hit Refresh in Synaptic, it's the equivalent of "apt-get update."

---

### Post by nisarg on 2008-03-08
Right. Thanks.

> **herbster said:**
> Synaptic package manager is a GUI front-end for the apt-get package management. It's the same thing. When you hit Refresh in Synaptic, it's the equivalent of "apt-get update."

---

