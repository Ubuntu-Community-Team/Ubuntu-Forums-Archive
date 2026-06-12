---
title: "signing under root = signing in as admin?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Unstuck on 2008-04-18
Lately, I've seen a few posts about not signing in as "root".  Is this the same as signing in as the administrator?

---

### Post by SunnyRabbiera on 2008-04-18
Pretty much, by default though Ubuntu doesn't use a root account but instead uses sudo that relatively does the same job.

---

### Post by philinux on 2008-04-18
> **Unstuck said:**
> Lately, I've seen a few posts about not signing in as "root".  Is this the same as signing in as the administrator?

Think of it this way. In the default install when you log in your running as a "limited user" but with access to an admin user via sudo for the commands you use. This is much more secure than running as an admin user.

---

### Post by Unstuck on 2008-04-18
Thanks, everyone.  

Now that I've taken admin privileges from this profile, does that mean I'm not able to "sudo" inside it?  Do I have to use the admin profile for my sudo-ing needs?

---

### Post by ace007 on 2008-04-18
Think of sudo as giving a non admin user temporary admin privileges to run whatever command follows the sudo command

---

### Post by philinux on 2008-04-18
You need to be a member of the admin group to use sudo. It doesn't mean you're running as an admin user.

---

