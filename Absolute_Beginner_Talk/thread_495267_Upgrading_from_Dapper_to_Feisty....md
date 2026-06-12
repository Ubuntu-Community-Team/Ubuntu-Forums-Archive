---
title: "Upgrading from Dapper to Feisty..."
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by B-777 on 2007-07-07
Is there an article/website which explains how to upgrade from Dapper to Feisty without a CD or can someone post the steps?

---

### Post by Happy_Man on 2007-07-07
From Dapper? It won't be easy.... You'll have to upgrade Dapper --> Edgy --> Feisty. It will be messy. If you're still willing, open up /etc/apt/sources.list with sudo permission, change all the "dapper" to "edgy" and run an upgrade. Then, boot into Edgy, and change all the "edgy" to "feisty". Boot into that, and you will have a Feisty install.

---

### Post by B-777 on 2007-07-07
> **Happy_Man said:**
> From Dapper? It won't be easy.... You'll have to upgrade Dapper --> Edgy --> Feisty. It will be messy. If you're still willing, open up /etc/apt/sources.list with sudo permission, change all the "dapper" to "edgy" and run an upgrade. Then, boot into Edgy, and change all the "edgy" to "feisty". Boot into that, and you will have a Feisty install.

So, there is no way to upgrade from Dapper to Feisty without going through edgy first?

It looks more of a pain to do it the way you describe and I don't want to mess up a perfectly working Dapper Install.

Guess I'll wait for the 7.04 CD I ordered and go from there :p

---

### Post by abn91c on 2007-07-07
did you try sudo apt-get dist upgrade

---

### Post by Sef on 2007-07-07
If you try to upgrade directly from Dapper to Feisty, you will break the system, and it will need to be reinstalled.

---

### Post by B-777 on 2007-07-08
Just upgraded from Dapper>Edgy>Feisty and all seems to be working without a hitch.

---

