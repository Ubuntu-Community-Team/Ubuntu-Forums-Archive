---
title: "Gedit error while trying to edit?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-02-11
Hi,

I am trying to edit a file & when I opened up the terminal, this is what happened:

rich@rich-laptop:~$ su root
Password: 
root@rich-laptop:/home/rich# gedit /etc/default/acpi-support

(gedit:6106): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Any ideas why I cant make this work?

Thanks,
Rich

---

### Post by emarkd on 2008-02-11
Why would you su to root?  You can just

```
gksu gedit /etc/default/acpi-support
```

---

### Post by p_quarles on 2008-02-11
Wrong way to run a graphical app as root. Under your normal account:
```
gksudo gedit /etc/default/acpi-support
```
That will take care of the permissions settings. NB: it will spit back a false alarm error message. You can safely ignore that.

---

### Post by Presto123 on 2008-02-11
**Edit: Use the ones above**

---

### Post by p_quarles on 2008-02-11
> **Presto123 said:**
> Try doing this instead:

```
sudo gedit etc/default/acpi-support
```

See what you get.
[Running sudo graphically](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by RichTJ99 on 2008-02-11
Thanks everyone!

---

