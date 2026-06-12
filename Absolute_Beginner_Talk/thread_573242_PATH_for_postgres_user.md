---
title: "PATH for postgres user"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Andra on 2007-10-11
hallo group,

I installed postgresql on Ubunut Feisty server. I would like to do something from command line. createdb works, but it is placing the new db in some default location. So I would like to use initdb. But this command is not found. I see that I should add user postgres /usr/lib/postgresql/8.2/bin to the PATH. I cannot do it as user postgres. I do it as my sudoer user, but it appears that postgres user has a different PATH (without all those sbin).

So, how can I change PATH for user postgrres (this is not an ordinary human being user) and permanently?

tia,

---

