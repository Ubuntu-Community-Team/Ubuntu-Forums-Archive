---
title: "No updates since 19th April in Feisty, am I missing something?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by keith11 on 2007-04-23
I am using Kubuntu Feisty and I haven't noticed any updates since the 19th of april when I installed the release version of Feisty. Have they not released any updates after that date or am I missing something here? Any ideas?

---

### Post by Spr0k3t on 2007-04-23
None since the 19th.  There were two packages that were released the same day as the final I think (upgraded instead of installed).

---

### Post by kostkon on 2007-04-23
No you have the final version.

If you want you can check by doing

```
sudo lsb_release -a
```

If you get the following, you are OK

```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

```

---

### Post by keith11 on 2007-04-23
I typed in the command and mine is the latest version. I was just wondering about the updates but now I know for sure. Thanks guys.

---

### Post by hequ on 2007-04-23
> **keith11 said:**
> I am using Kubuntu Feisty and I haven't noticed any updates since the 19th of april when I installed the release version of Feisty. Have they not released any updates after that date or am I missing something here? Any ideas?

Yeah, Even if Ubuntu is being updated very regularly that is still just four days. :) You shouldn't be very worried about that.  If you get no updates in two weeks then you should wonder.. :) 

So don't worry. :)

---

### Post by jvc26 on 2007-04-23
No Updates for Ubuntu too since the 15th April round of updates, I wouldnt start fretting yet, now its out of development, although there will still be regular updates they won't be as manic as they have been up to now.
Il

---

### Post by keith11 on 2007-06-02
I just read the weekly newsletter on this forum and it mentions some updates to have been released. I tried sudo  apt-get update but it doesn't get me the updates. is there anything wrong going on my side?

Keith.

---

### Post by zvacet on 2007-06-02
Do you have all repositories open?**system>administration<software properties<chek all boxes<reload**

Chek with update manager,bacause it were updates.

---

### Post by keith11 on 2007-06-02
I am running Kubuntu 7.04 and I was able to update through Adept manager but not through the console using sudo. How come?

---

### Post by zvacet on 2007-06-02
Did you tryed this

```
sudo aptitude update && sudo aptitude upgrade
```

---

