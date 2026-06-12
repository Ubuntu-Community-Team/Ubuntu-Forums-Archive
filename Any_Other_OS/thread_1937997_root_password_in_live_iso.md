---
title: "root password in live iso?"
date: 2012-03-08
forum: Any Other OS
---

### Post by EmilHem on 2012-03-08
When trying to install Mint it won't work since you're not a sudoer.
What is the live root password?

---

### Post by HappyJony on 2012-03-08
If I remember correctly, when I had to log back on(since I logged out by accident) in a liveCD of Ubuntu, there was no password. Just leave the password blank when you get asked for it and press enter. May work. Heck, it might be something silly like "mint" or "linux".

Hope this helps
Jony

---

### Post by EmilHem on 2012-03-09
I solved the problem by pressing,
CTRL + ALT + F1
then logging in as root ie. "Mint login: root"
then type in visudo and press enter
then at the end of the file insert "mint ALL=(ALL) ALL"
then CTRL + O (to save the file)
then CTRL + ALT + F7
then try to launch the installer again.

---

### Post by codemaniac on 2012-03-09
Congrats !!!!

---

