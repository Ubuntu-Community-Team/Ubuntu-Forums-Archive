---
title: "Forgot account password"
date: 2012-09-16
forum: Any Other OS
---

### Post by ChaosChris2009 on 2012-09-16
I forgot the pw to my user account and I can't reset it since I don't know my pw.

How can I remove my pw so I can use a new one?

I'm set to auto-login which is the only way I can login w/o providing the pw

Pinguy OS 12.04

---

### Post by snowpine on 2012-09-16
Here are easy instructions to reset your password in Ubuntu:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

(I hope they work in Pinguy too)

---

### Post by vasa1 on 2012-09-16
> **ChaosChris2009 said:**
> I forgot the pw to my user account and I can't reset it since I don't know my pw.

How can I remove my pw so I can use a new one?

I'm set to auto-login which is the only way I can login w/o providing the pw

Pinguy OS 12.04

It's more appropriate to post in the Other OS/Distro section if, for whatever reason, you don't wish to post in [the forum dedicated to the Pinguy OS]("http://forum.pinguyos.com/").

---

### Post by iponeverything on 2012-09-16
sudo passwd```

```

---

### Post by MG&amp;TL on 2012-09-16
> **iponeverything said:**
> sudo passwd

If he doesn't know his password...

---

### Post by iponeverything on 2012-09-16
yea.. I set sudodoers not to ask..

---

### Post by Rumor on 2012-09-16
Rather than rebooting (assuming you know the root password), just open a terminal:
```
su -
<enter root password>
passwd <your_username>
<enter & re-enter new password>
```

---

### Post by MG&amp;TL on 2012-09-17
> **Rumor said:**
> Rather than rebooting (assuming you know the root password), just open a terminal:
```
su -
<enter root password>
passwd <your_username>
<enter & re-enter new password>
```


Ubuntu doesn't have a root password set by default, and setting it is discouraged.

---

