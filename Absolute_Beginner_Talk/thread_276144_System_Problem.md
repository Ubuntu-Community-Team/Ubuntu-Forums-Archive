---
title: "System Problem"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2006-10-12
I opened my add/rmv apps. and i got a message saying that the following errors where found on my system.

[SIZE="2"]
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718[/SIZE]
 
WTF?

any of u 1337s know wat this means

thanks..:-|

---

### Post by Marsolin on 2006-10-12
Repositories support authentication, but you have to have their public key installed to avoid getting that warning. It doesn't cause a problem with installing software from there if you ignore it. The goal is to prevent malicious software from getting installed.

---

### Post by PriceChild on 2006-10-12
You have installed an unnofficial, third party repository.

As a staff member i've got to reccomend agaisnt the use of software sources other than the official.

In order to ensure that the package you are downloading hasn't been tampered with before you get it, you may check the GPG key (if it was signed)

Keys can be added to system>admin>software properties.

---

