---
title: "SSH Welcome message"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-09-03
How can I change the messages/text i see when i connect to my computer via SSH?
Now it somethig like:
> The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.


---

### Post by Copps on 2006-09-03
Yup, just change the /etc/motd file in your favourite text editor, like;

```
gksudo gedit /etc/motd
```

---

