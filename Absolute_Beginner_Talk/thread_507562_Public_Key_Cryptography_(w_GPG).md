---
title: "Public Key Cryptography (w/ GPG)"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-07-23
I just started using GPG, and I have a question about how public key cryptography works.

Is there any danger with making my secret key publicly available?

For example, let's say somebody wants to gain access to my data. They have a copy of my public key because that is available to anyone. They do not have the password used to unlock my secret key. In this situation, do they have any advantage at all if they have a copy of my secret key (but not the password to unlock it)?

I'm considering uploading my secret key to a publicly accessible server. It will be much easier for me to access from different computers, but also will be easy for anyone else to access. Please advise if this is a bad idea or not.

Cheers,
Dr D

---

### Post by Golyadkin on 2007-07-23
This is a very, very bad idea and it will criple your security. It will not break it entirely, but it will make it infinitely easier to crack. It is called secret key for a reason...

If you want to, bring your secret key with you on a USB stick, which itself is secured as well.

---

### Post by Mornedhel on 2007-07-23
Uh...

The point of the passphrase is that it's the only way to protect your secret key once someone has physical access to your account.

Giving away your private key WILL let anyone decipher (with absolutely no effort) your encrypted data. If you did give your private key to someone you don't entirely trust (as in, not a family member who you know understands what not to do with it), you'd better revoke your key pair.

---

### Post by dr_d on 2007-07-24
Thanks for the info guys.

My secret key is safe, and from now on I think I'll only keep it on a usb stick.

Cheers.

---

