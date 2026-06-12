---
title: "[SOLVED] system admistration mess!"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-12-05
Ok, so I have gone on a little path that started with one problem, of which the attempt at a fix has created several more.
At first, I wanted to change my root password, because it had been the same as my regular user. That was easy enough, and I was content. However, I soon discovered that my regular user account could run system -> administration programs and other "sudo" commands without a password prompt. Sensing a security vulnerability, I went into "users and groups" and deselected my ability to administer the system. ooops! Now no superuser commands could be run at all. After a little googling, I restarted into recovery mode and ran visudo. From there I changed "root   ALL=(ALL) ALL" to "anu   ALL=(ALL) ALL". However, this did little to assuage the problem. Luckily, I recovered from my brain fart and simply ran the terminal with the su command. duh! Reversing my visudo edit and reinstating my "administering to the system" rights was a snap. *deep breath*
Now at the present. I have administrative control, but under "system -> administration", only nine out of about 20 of the icons show, even they are all selected to be displayed through the menu setting. So my two problems are: I need my icons back, and I can still run sudo commands without a password prompt. Any help would be greatly appreciated.

---

### Post by HermanAB on 2007-12-05
Here you go - all the help you need:
$ man sudoers

---

### Post by rouge568 on 2007-12-05
Cool. That solved problem B. Now how do I get my icons back?

EDIT: Never mind: a quick restart solved this. Thank you!

---

