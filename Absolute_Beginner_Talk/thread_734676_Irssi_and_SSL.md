---
title: "Irssi and SSL"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2008-03-24
anyone help me, need 2 connect to a irc server using ssl

---

### Post by L0cKd0wN on 2008-07-10
Type the following commands into your Irssi status window:

```
/set use_ssl on
```
```
/set ssl_verify on
```
```
/save
```

Then after you've set that up, you need to use the -ssl option in conjunction with the /connect command.  (The server also must be SSL enabled). 

Example of connecting to EFNet:
```
/connect -ssl irc.blessed.net 7000
```

Hope this helps someone!
~L0cK

---

