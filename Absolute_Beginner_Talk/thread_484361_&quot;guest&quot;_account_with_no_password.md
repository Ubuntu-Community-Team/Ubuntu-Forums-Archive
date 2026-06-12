---
title: "&quot;guest&quot; account with no password"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Zannax on 2007-06-25
Is it safe to setup an account "guest", default desktop-user permissions, with no password?
Or would it be a kind of vulnerability?
The account manager refuses to assign a null password, but I could change it by hand...

---

### Post by luckyd on 2007-06-25
Im no pro, but it seems like it should be safe, since they won't able to install or remove any software without the sudoer's password. You should make sure that they only have access to their home partition, and not yours also.

---

### Post by punx45 on 2007-06-25
that should be relatively safe as long as you dont have any remote access services running, such as SSH

---

### Post by Zannax on 2007-06-26
Ok, thank you... So I won't activate any remote service.

---

### Post by mjwhitfield on 2007-06-26
why not make a guest account and remove them from the sudo permissions

---

