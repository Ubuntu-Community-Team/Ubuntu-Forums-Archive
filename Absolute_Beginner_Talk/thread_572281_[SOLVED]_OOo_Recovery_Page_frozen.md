---
title: "[SOLVED] OOo Recovery Page frozen"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by njmacrai on 2007-10-10
Hello. Sorry for being such a Newbie to LINUX. I am currently running Feisty Fawn and recently I tried to download a WORD doc. My OOo Recovery Page came up saying that this doc cannot be recovered. That's fine because I don't really need the doc anymore, and I can retrieve it from the website in the future if I need to. In the meantime, my OOo Recovery Page won't allow me to do anything. I try to close it but it doesn't respond. I've tried restarting my system and then it just comes back. With this frozen Recovery Page I cannot currently open any text docs, or run anything that requires OOo. Please, any suggestions?

In fact, I wouldn't even mind getting rid of OOo because I've heard that ABIWORD is just as good.

---

### Post by por100pre1 on 2007-10-10
Try this:

```
mv ~/.openoffice.org2 ~/.openoffice.org2_backup
```

```
pkill soffice
```

and try again. :-k

---

### Post by njmacrai on 2007-10-10
Thank-you so much for your help. That suggestion worked and now I am back to normal OOo functioning. I am so pleased! Terrific! Very kind of you to help.

---

### Post by por100pre1 on 2007-10-10
Glad to help! 8) Thank you for marking the thread as SOLVED. :)

---

