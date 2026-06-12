---
title: "[SOLVED] ...install software that can't be authenticated!"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-06-09
I am getting a warning when trying to update.
> You are about to install software that can't be authenticated!
[IMG]http://zune-downloadz.com/updatewarning.png[/IMG]
How can I fix this authentication error?  Thank you.

---

### Post by Kobalt on 2007-06-09
Since you're updating the kernel I assume something is wrong with the GPG keys of your official Ubuntu repos. To fix it, go into System > Admin. > Update Sources. Click on the Authentication tab and then Restore original keys.

---

### Post by wormser on 2007-06-09
> **Kobalt said:**
> Since you're updating the kernel I assume something is wrong with the GPG keys of your official Ubuntu repos. To fix it, go into System > Admin. > Update Sources. Click on the Authentication tab and then Restore original keys.

That sugestion did not work.  But it got me thinking.  I did a **sudo apt-get update** and that resolved it.

Thanks for you help

---

