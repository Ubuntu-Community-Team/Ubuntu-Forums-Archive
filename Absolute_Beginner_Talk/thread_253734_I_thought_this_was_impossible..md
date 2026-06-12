---
title: "I thought this was impossible."
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by 4.9 on 2006-09-08
I messed up Ubuntu so badly, that I actually can't repair it using aptitude or apt-get. Can someone tell me how to uninstall Ubuntu?

---

### Post by Anonii on 2006-09-08
How did you repair Ubuntu with APT, before?

Also, uninstall Ubuntu as "Delete the current installation and re-install it from scratch"?

---

### Post by 4.9 on 2006-09-08
> **Anonii said:**
> How did you repair Ubuntu with APT, before?

Also, uninstall Ubuntu as "Delete the current installation and re-install it from scratch"?

That is an option on the LiveCD? It won't accidentally delete my other OSs will it?

---

### Post by Anonii on 2006-09-08
> **4.9 said:**
> That is an option on the LiveCD? It won't accidentally delete my other OSs will it?
I'm sure that you can just uninstall Ubuntu (clear the partitions it uses) and install a fresh one in them, but I dont know how.
You should wait for someone who knows.

---

### Post by jordanmthomas on 2006-09-08
Just to see if it would be any trouble to reinstall, could you post the output of this?
```

sudo fdisk -l

```

You can just use the LiveCD and clear off the partitions you used for Ubuntu and reinstall if you really want.
What did you do to fubar your system?  It's possible it may be salvagable.

---

