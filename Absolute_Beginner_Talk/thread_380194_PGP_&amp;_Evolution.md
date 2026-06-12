---
title: "PGP &amp; Evolution"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-03-09
Been trying to search the forum but I have not found anything helpful yet.

I am trying to send an encrypted email. I imported the recipients public key into seahorse (Applications > Accesspries > Passwords and Encryption Keys).

In Evolution I click on New, then under Security I tick PGP Encrypt. I then enter the recipient and type an email. When I click Send I get this error message:

```
Because "gpg: using PGP trust model
gpg: using subkey ******** instead of primary key ********
gpg: ******: There is no assurance this key belongs to the named user
gpg: [stdin]: encryption failed: unusable public key
", you may need to select different mail options.
```

---

### Post by bapoumba on 2007-03-09
Hello,
Edit > Prefs > Security > did you set up your PGP/GPG key ID ?

---

### Post by PartisanEntity on 2007-03-09
Yes I did have my key ID set up. 

But I also just now clicked on "Always trust keys in my keyring when encrypting" in the Security settings of Evolution and that appears to have solved the problem.

I went through the process again and this time the email was sent off without the error message, now lets see if the recipient can decrypt it.

---

### Post by PartisanEntity on 2007-03-09
Okay here is some feedback, ticking "Always trust keys in my keyring when encrypting" solved the problem, the en-/decryption worked.

---

