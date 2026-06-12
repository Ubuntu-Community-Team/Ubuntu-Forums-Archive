---
title: "Invalid user name/or password...Retrieval??"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by justlisawv on 2006-06-02
I am trying to log onto Ubuntu. I am pretty sure I am using the name and password I set, but it is saying invalid. Is there a way of retrieving this information? (or adding a user without it?) Thanks!

---

### Post by 5-HT on 2006-06-02
[LEFT]Did you check caps/num lock?

If that doesn't help, this should do the trick:  [https://wiki.ubuntu.com/LostPassword]("https://wiki.ubuntu.com/LostPassword")

Hope that helps.
[/LEFT]

---

### Post by mlind on 2006-06-02
[QUOTE=justlisawv]I am trying to log onto Ubuntu. I am pretty sure I am using the name and password I set, but it is saying invalid. Is there a way of retrieving this information? (or adding a user without it?) Thanks![/QUOTE]

for the initial question, password retrieval to cleartext isn't possible because
passwords are hashed using one-way hash function (md5?), and result is a hash digest.
For your amusement, you can try cracking it using JohnTheRipper for example ;)

Adding new users without password is possible, but to get allow one to log in GNOME
session requires adding a new PAM authentication method to /etc/pam.d/gdm,
which allows 'password-less' logins.

(I'm about to write a small howto about this, if anyone needs to login without
using a password. Good for family environments.)

You probably just want to change your lost password, so just follow the link 5-HT
gave.

---

