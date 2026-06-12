---
title: "getting mysql server configured?"
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-08-28
I am trying to get mysql set up. I never have these problems on windows but this is the first time on linux and I am confused.

I need to add a user of root but doing:

 SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpwd');

Just tells me that there is no such row in the user table.

I can do

 SET PASSWORD FOR ''@'localhost' = PASSWORD('newpwd');

but obviously that user doesn't have any permissions so I can't add any users or do anything.

Help.  :-|

---

### Post by gammyhand on 2005-08-29
[QUOTE=gammyhand]I am trying to get mysql set up. I never have these problems on windows but this is the first time on linux and I am confused.

I need to add a user of root but doing:

 SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpwd');

Just tells me that there is no such row in the user table.

I can do

 SET PASSWORD FOR ''@'localhost' = PASSWORD('newpwd');

but obviously that user doesn't have any permissions so I can't add any users or do anything.

Help.  :-|[/QUOTE]
 Is it that difficult?

---

### Post by gammyhand on 2005-08-29
Never mind, I solved it with google. I was thinking that it was a ubuntu specific thing but of course it's not.

---

