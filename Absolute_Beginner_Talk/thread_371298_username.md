---
title: "username?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by a_lacsa on 2007-02-26
hello,

I am allen from the philippines.

when i installed ver 6.10, it never asked me for a username.. only a password.

what username should i use with the password i gave during the installation?

---

### Post by mikewhatever on 2007-02-26
Have you installed with the alternate cd (text mode) and chosen oem install? If so, your username is oem. Otherwise, the default one should be the name of the OS, such as Ubuntu, Kubuntu, etc.

---

### Post by a_lacsa on 2007-02-26
thanks!

oem worked

---

### Post by viper on 2007-02-26
> **mikewhatever said:**
> Have you installed with the alternate cd (text mode) and chosen oem install? If so, your username is oem. Otherwise, the default one should be the name of the OS, such as Ubuntu, Kubuntu, etc.

Brilliant, my brother just rang me with the same question about an hour ago, you have saved me alot of time as i did not even think he might have used the oem install. 
Thanks mate........:)

---

### Post by taurus on 2007-02-26
And don't forget to run this command to create an actual account for you to log in from now on.

```
oem-config-prepare
```

---

### Post by a_lacsa on 2007-02-27
thanks taurus for the added info :)

---

### Post by a_lacsa on 2007-03-01
hi taurus,

I tried that add&#314; info you gave me but I get this error message:

 Adding system startup for /etc/init.d/oem-config ...
   /etc/rc2.d/S12oem-config -> ../init.d/oem-config
update-rc.d: symlink: Permission denied

how come? hwat should I do?

---

### Post by taurus on 2007-03-01
Well, try it with sudo then.

```
sudo oem-config-prepare
```

---

### Post by a_lacsa on 2007-03-02
thanks thanks!

---

