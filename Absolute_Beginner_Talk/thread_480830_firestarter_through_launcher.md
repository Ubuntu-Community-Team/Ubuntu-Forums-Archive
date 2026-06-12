---
title: "firestarter through launcher"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-06-21
apparently creating a launcher icon with sudo firestart does not seem to work. i guess that's coz it requires the root password... 

how do i fix this?

---

### Post by p_quarles on 2007-06-21
If you don't know how to do that, you probably don't want to. Keeping Firestarter running is actually more of a security risk than anything else, since you would have a root process running.

Ubuntu comes standard with a very restrictive firewall, and the Firestarter app is more of an advanced tool for modifying it.

---

### Post by NeoLithium on 2007-06-21
In the command use  
gksu firefstarter

---

### Post by Sushubh on 2007-06-21
i wanted to use the internet connection sharing feature of firestarter... :)

---

### Post by p_quarles on 2007-06-21
> **Sushubh said:**
> i wanted to use the internet connection sharing feature of firestarter... :)
Oh, I see. In that case, it may be more efficient to unblock the relevant ports in iptables. Gksu will still ask you for your password, but modifying iptables would be a more permanent solution. But, whatever works.

---

