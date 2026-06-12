---
title: "LDAP authentication error"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Abhi Kalyan on 2006-11-16
When I
$ ldapadd
SASL/DIGEST-MD5 authentication started
Please enter your password: <password>
ldap_sasl_interactive_bind_s: Internal (implementation specific) error (80)
        additional info: SASL(-13): user not found: no secret in database

What do i do,
Where is my error?
Please help

---

### Post by Abhi Kalyan on 2006-11-17
Problem solved Thank you

---

### Post by netventure on 2006-11-24
Hi Abhi,

I'm getting the same error. Can you tell me how you fixed the problem?

--NV

---

### Post by Abhi Kalyan on 2006-12-10
The matter lies in editing the
slapd.conf file
where you place the rootdn,
Am going through the process again, so will report Immediatly-
Sorry for the delay mate

---

### Post by peaceful_dragon on 2006-12-20
I am having the same problem... How do you fix it?

---

