---
title: "How to uninstall games????"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-08-14
I messed up on a setting in americas army and now it wont launch. How do I uninstall it?? :confused:

---

### Post by Anduu on 2006-08-14
I am assuming it was installed using a binary installer....It should be as simple as deleting it's directory...

Some installers add an uninstall script...have a look through its directory.

---

### Post by WalmartSniperLX on 2006-08-14
ok thanks

---

### Post by WalmartSniperLX on 2006-08-14
found this:

Uninstall (its a shell script)

So do I uninstall that? or open it with terminal or what? I tried opening it with terminal and it did nothing

I dont know how to use the uninstall script :S sorry noob here](*,)

---

### Post by Anduu on 2006-08-15
Open a terminal and cd to the directory...

```
sh ./Uninstall
```

---

### Post by fakie_flip on 2006-08-15
> **Anduu said:**
> Open a terminal and cd to the directory...

```
sh ./Uninstall
```

why should should you use sh? why not run it like this "./Uninstall"? i dont really understand why people use sh before commands. i am guessing that it uses a different type of shell instead of bash. what's the reason for it?

---

### Post by Anduu on 2006-08-15
Dunno...just habit I guess.

I have run into scripts that wouldn't run unless you sh...

---

