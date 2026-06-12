---
title: "Latest kernel upgrade broke suspendability"
date: 2008-10-16
forum: Apple Hardware Users
---

### Post by flaggh on 2008-10-16
I'm running Hardy64 on a Macbook 2,1. The latest kernel update seems to have broken suspend.  Any attempt to suspend now results in a kernel panic.  Anyone else experiencing this problem?

---

### Post by StooJ on 2008-10-28
Yep, I have the same problem. Unfortunately haven't had time to find out what's going on, but will hopefully do that next week.

Checked this evening and it's happening with the 2.6.24-21 kernel.

---

### Post by kfl on 2008-10-29
I also have that problem. I'm on a Macbook Pro 3,1. 

I think the problem might be because the ath9k module is now loaded, and I used a self-compiled madwifi before the upgrade.  But I haven't investigated in details.

---

### Post by cyberdork33 on 2008-10-29
> **kfl said:**
> I also have that problem. I'm on a Macbook Pro 3,1. 

I think the problem might be because the ath9k module is now loaded, and I used a self-compiled madwifi before the upgrade.  But I haven't investigated in details.
To test that, just unload ath9k manually before suspending to see if it then works...

```
sudo modprobe -r ath9k
```

---

### Post by kfl on 2008-10-30
Indeed.

It seems that it really is ath9k that is the problem and not suspend. Because when I unload ath9k the machine crashes.

---

