---
title: "Password Problems"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by sagarkolte on 2007-06-28
I am having a problem logging into ubuntu:

[LIST=1]
[*]When it asks for a user name I provide it with one, then it asks for a password and I give my password, but it says that the password is incorrect.

[*]Then I start Ubuntu in recovery mode and then it asks for a password again and I give it my password, this time it accepts it! and allows me to change my password too. 

[*]but when I start ubuntu in the normal mode again I am faced with the same problem that it does not accept my password.
[/LIST]

What am I to do?
Help will be deeply appreciated.

Thank You

Sagar

---

### Post by rillip on 2007-06-28
Can you post exactly what you're doing?  I suspect you reset some other user's password, probably root or the ubuntu user.

It should look like 

```

passwd username

```

---

### Post by aquavitae on 2007-06-28
I assume you've checked caps lock?  Are you on a network - i.e. are you trying to log into the network or into your computer?  I've never used a network login before, so I don't know exactly how it works, but I do know that your computer login won't work for the network (unless they happen to be identical).

---

