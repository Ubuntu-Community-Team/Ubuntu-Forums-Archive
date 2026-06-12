---
title: "About environment variables?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by HuBaghdadi on 2008-01-06
Hi.
What is the difference between setting an environment variable in .bash_profile and /etc/profile?
For what ~/.bashrc is used?
How to make an environment variable permanent and visible to all users?
Thanks.

---

### Post by TBerben on 2008-01-06
I'm running Ubuntu Gutsy now, but I don't see any file named .bash_profile; at least nog in my /home directory.
bashrc is used for stuff that needs to be run everytime you start a shell. The commands and expressions in /etc/profile are the same, except for the fact that they are systemwide. Changes in ~/.bashrc only affect one user.

---

### Post by HuBaghdadi on 2008-01-06
>>I'm running Ubuntu Gutsy now, but I don't see any file named .bash_profile; at least nog in my /home directory.

It seems it could be create by hand under user's directory.

---

