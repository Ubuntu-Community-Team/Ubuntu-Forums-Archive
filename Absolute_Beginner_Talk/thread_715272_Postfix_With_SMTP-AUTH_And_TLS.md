---
title: "Postfix With SMTP-AUTH And TLS"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by appleimac on 2008-03-04
I am trying to instal this but I get a message asking for pass phrase for smtpd.key

when I run this command

```
openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024

```

I get this output

```
232 semi-random bytes loaded
Generating RSA private key, 1024 bit long modulus
.................++++++
..++++++
e is 65537 (0x10001)
Enter pass phrase for smtpd.key:

```

Where Do i find the pass phrase?



Cheers

---

### Post by dcstar on 2008-03-04
> **appleimac said:**
> I am trying to instal this but I get a message asking for pass phrase for smtpd.key

when I run this command

```
openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024

```

I get this output

```
232 semi-random bytes loaded
Generating RSA private key, 1024 bit long modulus
.................++++++
..++++++
e is 65537 (0x10001)
Enter pass phrase for smtpd.key:

```

Where Do i find the pass phrase?

Cheers

In your head.

[http://www.openssl.org/docs/apps/openssl.html#PASS_PHRASE_ARGUMENTS](http://www.openssl.org/docs/apps/openssl.html#PASS_PHRASE_ARGUMENTS)

---

### Post by glennric on 2008-03-04
> **dcstar said:**
> In your head.

[http://www.openssl.org/docs/apps/openssl.html#PASS_PHRASE_ARGUMENTS](http://www.openssl.org/docs/apps/openssl.html#PASS_PHRASE_ARGUMENTS)

Aaaah, who put it there.  Get it out.

---

### Post by appleimac on 2008-03-05
Thanks for that but now when I run this comand 

```
[root@webserver ~]# openssl req -new -key smtpd.key -out smtpd.csr
```

I get this output

```
Enter pass phrase for smtpd.key:
unable to load Private Key
22855:error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt:evp_enc.c:461:
22855:error:0906A065:PEM routines:PEM_do_header:bad decrypt:pem_lib.c:425:
```


I am using the pass phrase     password



Any Ideas?

---

### Post by appleimac on 2008-03-05
Anyone. I really need to to get this up and running.

---

