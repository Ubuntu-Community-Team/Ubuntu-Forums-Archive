---
title: "Thunderbird cannot update"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by tqprvn on 2008-03-17
hi all

One of my staff has Thunderbird 2.0.0.6 installed, the rest are up to .12

Trying to update it, but in TB itself the check for updates option is grayed out.  In Synaptic, it has no version more recent than 0.6 on hers (mine goes up to 12).

Any ideas?

Matt

---

### Post by Xiong Chiamiov on 2008-03-17
You might check which repositories are enabled in Synaptic (settings -> repositories).  If you really want to, you can download the package from the Ubuntu site [here]("http://packages.ubuntu.com/").

---

### Post by Oldsoldier2003 on 2008-03-17
> **Xiong Chiamiov said:**
> You might check which repositories are enabled in Synaptic (settings -> repositories).  If you really want to, you can download the package from the Ubuntu site [here]("http://packages.ubuntu.com/").

and after checking sure the repos are enabled

```
sudo apt-get update
sudo apt-get upgrade
```

there is a good change that the machine is in need of serious package upgrades...

---

### Post by jrusso2 on 2008-03-17
What Version of Ubuntu are you running?  Are you running 7.10 or an older one?

---

### Post by tqprvn on 2008-03-17
> **Xiong Chiamiov said:**
> You might check which repositories are enabled in Synaptic (settings -> repositories).  If you really want to, you can download the package from the Ubuntu site [here]("http://packages.ubuntu.com/").

umm - which ones should be enabled?

> **Oldsoldier2003 said:**
> and after checking sure the repos are enabled

```
sudo apt-get update
sudo apt-get upgrade
```

there is a good change that the machine is in need of serious package upgrades...

This was what I thought too, but checked with the update manager and it said the machine is up to date.

> **jrusso2 said:**
> What Version of Ubuntu are you running?  Are you running 7.10 or an older one?

7.10

---

### Post by Oldsoldier2003 on 2008-03-17
> **tqprvn said:**
> umm - which ones should be enabled?


the first 4 you probably don't need source :)

---

### Post by Nepherte on 2008-03-17
> **tqprvn said:**
> hi all

One of my staff has Thunderbird 2.0.0.6 installed, the rest are up to .12

Trying to update it, but in TB itself the check for updates option is grayed out.  In Synaptic, it has no version more recent than 0.6 on hers (mine goes up to 12).

Any ideas?

Matt
You can only update that way if you run Thunderbird with sudo priviliges.
```
sudo thunderbird
```
Then the option will not be greyed out, afterwards you just keep using Thunderbird with the normal user rights.

---

### Post by tqprvn on 2008-03-21
well I really do not know what is up with that machine....

It insists there are no updates required for anything.  

Out of update manager and terminal when I check for updates, it is telling me that the machine is up to date (the other computers installed on the same day are all downloading like 300 meg worth of updates, this one is just as the install CD left it).

The machine is also painfully slow, which makes no sense, it is a relatively new laptop.  <1 yr old.

On the TB version - I tried the sudo thunderbird thing, check for updates - even then it says that at 2.0.0.6 no updates are available, just as terminal and synaptic do.

Any ideas?

---

