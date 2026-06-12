---
title: "Mail + ssh"
date: 2007-09-20
forum: Argentina Team
---

### Post by Montsegur87 on 2007-09-20
Me dieron una una cuenta en gnu.org y me dijeron esto


```
Please send the following information, preferably GPG-signed.

                           Needed Information

   1. Your primary uses of your fencepost account
      (e.g., "GNU Maintainer of GNU Foobar")
   2. Requested fencepost account username
   3. An email address that does not deliver via FSF or GNU
   4. Phone numbers and time of day where we can contact you to
      confirm fingerprints.
   5. Postal mailing address
   6. SSHv2 *public* key from ~/.ssh/id_{dsa,rsa}.pub or
      ~/.lsh/identity.pub
```

Supuestamente con

> $ ssh [email]XXX@gnu.org[/email]
me tendria que tirar el promp para el password (que supongo que sera la key esa ) pero me tira un timeout (el puerto 22 esta abierto)

Como logro conectarme a esta cuenta???

---

### Post by Hei Ku on 2007-09-20
ssh <server> <usuario>@gnu.org

Creo que esa es la forma correcta

---

### Post by Montsegur87 on 2007-09-20
Interesante , me pondre a investigar cual es el server de gnu.

---

