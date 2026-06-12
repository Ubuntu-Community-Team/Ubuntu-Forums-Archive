---
title: "Gaim environment variables for system and local users"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mchnhed on 2007-08-06
How do I change System and User Environment variables for Gaim? More specifically, in Windows I did the following:

1. System Properties (right click My Computer -> Properties)
2. Advanced tab -> Environment Variables (at the bottom)
3. Click New to add a new User Variable (Name = GAIMLANG, Value = [two-character language code])
4. Click New to add a new System Variable (Name = GAIMHOME, Value = [desired directory path]

This makes it so that the **user interface language is customized per user**, but the Gaim application data refers to **one location, even under different usernames**.

What is the equivalent of doing this in Linux / Ubuntu? I understand that I can do something like this...

```
export VARIABLE_NAME=somevalue
```

...but I just don't know how to differentiate between the system and local users. I hope someone can help me. Thanks in advance!

---

### Post by Pragmatist on 2007-08-06
[https://wiki.ubuntu.com/environment_variables?highlight=%28variable%29](https://wiki.ubuntu.com/environment_variables?highlight=%28variable%29)

---

