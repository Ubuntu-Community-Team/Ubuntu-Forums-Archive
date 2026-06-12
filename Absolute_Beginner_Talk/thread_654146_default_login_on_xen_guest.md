---
title: "default login on xen guest?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by uk28 on 2007-12-30
A very simple and stupid problem, if you would be so kind to help :)

I've setup a Xen Gutsy guest on Gutsy. All is well, apart from the fact i've specified a default root password when creating the guest image. Ubuntu doesn't allow root login, so i can't log in! :)

I've tried to mount the .img and manually add a normal account, but it doesn't want to play ball. 

I just created an entry in 'passwd' with 'x' in password feild. Created a shadow entry with '*' in password field, in the hope i could login without a password, no luck.

So has anyone got a tip on what i could do here. Or directions on how to successfully manually add a normal account once the file system is mounted. I swear i've done it on other distro's without issues, but will ubuntu allow accounts without a password?

*Sorry, i was having a 'moment', its been a long week, i've found a solution. 

I simply mounted the domU image file,  copied my account from the dom0 to the domU, then added the account to the sudoers file.

---

