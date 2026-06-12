---
title: "port 515"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by new_foo on 2006-09-06
I've been to the Shields Up web site and appearantly my port 515 is open.  How do I close it?

Thanks in advance

---

### Post by hw-tph on 2006-09-06
tcp/515 is normally used by network printing. Stop whatever network printing system that is running (cupsys, or whatever).

You can check what *really* is running by using the lsof tool. Try **sudo lsof -i @localhost:515** to see what's listening on port 515.

When you know what is running you can shut it down. Services can be shutdown using **sudo /etc/init.d/${SERVICENAME} stop**. Replace ${SERVICENAME} with the actual name of the service, like **sudo /etc/init.d/cupsys stop** to stop the printing service. You can manage services using either the **update-rc.d** tool or by using a GUI application like Bum.

Håkan

---

