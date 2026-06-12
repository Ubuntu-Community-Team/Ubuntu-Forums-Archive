---
title: "Update Issue"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Chadwick17 on 2007-09-15
Ran the update manager and after checking for updates I get this message:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

Any ideas? Everything was working just fine a couple of days ago (as far as updates).

---

### Post by Chadwick17 on 2007-09-15
Found a solution :

needed this key: 
wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

---

