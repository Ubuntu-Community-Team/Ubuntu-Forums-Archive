---
title: "Zorin: Failure to Update"
date: 2013-01-01
forum: Any Other OS
---

### Post by ProxyCyber on 2013-01-01
So I installed ecryptfs-utils. Using sudo apt-get ecryptfs-utils. Didn't  install but the next time I did sudo apt-get update, it said 

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I UNINSTALL  ecryptfs-utils using terminal or some other way? What's the issue?

---

### Post by oldos2er on 2013-01-01
Moved to Other OS/Distro Talk.

---

### Post by ProxyCyber on 2013-01-01
> **oldos2er said:**
> Moved to Other OS/Distro Talk.


If you move my post, do you mind linking it again? I couldn't possibly know where you moved it, and the URL if you only tell me just by category.

---

### Post by lisati on 2013-01-02
> **ProxyCyber said:**
> If you move my post, do you mind linking it again? I couldn't possibly know where you moved it, and the URL if you only tell me just by category.

You can find your posts with by using the "search" drop-down menu, which has options to find all your threads and all your posts.

Although [Zorin]("http://zorin-os.com/") is based on Ubuntu, it's a distro in its own right.

---

### Post by NikTh on 2013-01-02
> **ProxyCyber said:**
> So I installed ecryptfs-utils. Using sudo apt-get ecryptfs-utils. Didn't  install but the next time I did sudo apt-get update, it said 

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I UNINSTALL  ecryptfs-utils using terminal or some other way? What's the issue?

Use this command to see if encrypt-fs is actually installed or not.
```
dpkg -l | grep -i encryptfs
```as for the error message it means that you have open 2 or more processes at the same time. Processes that are using the same resource. 
e.g update manager or synaptic or some Zorin's application that uses the apt or dpkg.
For example you cannot combine one of above applications with apt-get via terminal.
Sometimes a reboot can solve this problem. 

Thanks

---

