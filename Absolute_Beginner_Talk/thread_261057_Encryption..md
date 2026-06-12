---
title: "Encryption."
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Titan_Prometheus on 2006-09-19
How Can I Encrypt A File? Like not deny a user access, but actually encrypt it strongly.

---

### Post by kidders on 2006-09-19
Hi there,

That really depends on how you want to approach things. There are just too many ways for there to be a simple answer!

PGP encryption is a common choice, especially for email-related stuff. Additionally, Linux supports a number of encrypted filesystems (such as EncFS), in the event you'd like to garbage entire directories, without making life awkward for yourself.

Post back a little about exactly what you'd like to do, and I'd be happy to try to be more specific for you :-)

---

### Post by Titan_Prometheus on 2006-09-20
Something Like PGP. I just would like to encrypt a few files to pass along to classmates.Something Simple And Common, But almost impossible to break.

---

### Post by kidders on 2006-09-20
Kewl :-) Well then GnuPG is your man. Just in case you don't already know, here's a *reallllly* brief overview:

[LIST=1]
[*]You and your friends each create public and private key pairs, constructed in such a way that using one to calculate the other would take several centuries of grinding away with mersenne primes and group theory.
[*]Typically, you don't just encrypt things ... you encrypt a message **_to_** another person. In other words, messages (or files) are coded in such a way as to be readable only by the intended recipient. To do this, you need the recipients public key.
[*]Using his private key, the recipient short-circuits thousands of years of long-winded multiplication, and decodes the message instantly.
[/LIST]

GnuPG is pretty cross-platform ... there are even Microsoft-compatible implementations of it! Many users publish their public keys on their personal websites, and include them in emails, so that everyone that might want to talk to them in secret can do so easily. The private keys should be jealously guarded though, and need to be grounded in good-quality passwords, to minimise the risk involved in spreading the public key around. The GnuPG engine will help you find one.

I hope that helps. It should fulfil most peoples' usability criteria, in that it's fairly straightforward to use (once you get the knack of it), free, and is available on lots of platforms.

---

### Post by skymt on 2006-09-20
You'll want to install Seahorse. It's available in Universe. It's a graphical GPG interface. You can use it to set up a key pair using a friendly wizard-style interface. It also installs an extension to Nautilus, so you can right-click a file and encrypt it.

---

