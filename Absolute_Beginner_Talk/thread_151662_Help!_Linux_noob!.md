---
title: "Help! Linux noob!"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Satchmo724 on 2006-03-28
ok, this would be my first time diving into linux, and I got it installed easily enough. It's installed on a Dell inspiron 1150 laptop. I created a user account called "tjizzle", same for password.  Problem is, once I'm logged in, I can't access anything under the system menu, like users and groups or adjusting the date and time.  I did a search and came to the conclusion that the account wasnt set as an admin, so I booted into recovery mode, and after following the guide, it said that tjizzle was already a member of adm.    What do I have to do to fix this?

---

### Post by Ubuntuud on 2006-03-28
You are supposed to get a sort of a popup asking for your root password (if you haven't changed it, it'll be tjizzle). If you do not get this popup, something is seriously wrong... You might want to try to reinstall (don't rush though), or ask someone who knows more about it than me.

---

### Post by Mustard on 2006-03-28
What output do you get if you type in this..

```
sudo whoami
```

---

