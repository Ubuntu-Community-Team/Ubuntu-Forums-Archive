---
title: "how to remote desktop in ubuntu"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by saurabh srivastava on 2008-01-10
hi
how i can use remote desktop in ubuntu....i m using proxy server connection.
please help me
:(

---

### Post by codesplice on 2008-01-10
Have you tried the rdesktop command?

```
$ rdesktop server.domain
```

---

### Post by saurabh srivastava on 2008-01-10
wat u mean by domain 
where i 'll write user name password
:confused:

---

### Post by codesplice on 2008-01-10
By domain, I mean domain :-D

If you need to specify a username, use the -u option.

For instance, if I wanted to log on as splice to a server at remote.server.net, I'd use
```
$ rdesktop -u splice remote.server.net
```

---

