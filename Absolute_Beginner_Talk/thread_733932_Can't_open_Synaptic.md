---
title: "Can't open Synaptic"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by lemmyc on 2008-03-24
Hi,
I made the mistake of giving root a password when following a user guide.
Now, when I try to open Synaptic, I get the following message: 

> E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

I'm not logged in as root. Also, I tried doing this to disable the root account again:
```
sudo passwd -l root
```

Any ideas how I might fix this? 

I'm using Hardy Beta, by the way, but I'm guessing this is a general Ubuntu issue?

Thanks.

---

### Post by bhavi on 2008-03-24
> **lemmyc said:**
> Hi,
I made the mistake of giving root a password when following a user guide.
Now, when I try to open Synaptic, I get the following message: 



I'm not logged in as root. Also, I tried doing this to disable the root account again:
```
sudo passwd -l root
```

Any ideas how I might fix this? 

I'm using Hardy Beta, by the way, but I'm guessing this is a general Ubuntu issue?

Thanks.
Appears to be solved here:

[http://ubuntuforums.org/showthread.php?t=699130](http://ubuntuforums.org/showthread.php?t=699130)

---

### Post by lemmyc on 2008-03-24
Thank you very much, that worked!

---

### Post by bhavi on 2008-03-24
> **lemmyc said:**
> Thank you very much, that worked!
Please mark the thread as solved then...

---

### Post by yngens on 2008-03-27
- go to System->Administration->Users and Groups
- click on the "root" user, and click properties
- choose the Advanced tab and change '/home/root' in "Home directory" to '/root'.

---

### Post by wizard_wiz on 2008-04-18
Re: Can't open Synaptic
- go to System->Administration->Users and Groups
- click on the "root" user, and click properties
- choose the Advanced tab and change '/home/root' in "Home directory" to '/root'.

Thanks!
This solution worked for me but with a slight modification. I changed the '/root' directory to '/', since it was already '/root' and wasn't working.

---

