---
title: "&quot;Could not open cache - Adept Updater&quot;"
date: 2006-05-02
forum: Apple PPC Users
---

### Post by fraterf93 on 2006-05-02
I just installed Kubuntu Dapper test 6.06 on my Mac Mini, and I get this message when I try to update using Add Remove Programs, or Adept, or by clicking the exclamation icon by the clock: [IMG]http://f3.yahoofs.com/users/41b4d294z7c2ed2c1/3503re2/__sr_/1dc5re2.jpg?phgn8VEBX.nGVpXZ[/IMG]
apt-setup doesnt work: brant@macubuntumini:~$ sudo apt-setup
sudo: apt-setup: command not found

apt-get update does work, but I still get the message "APT database cannot be opened" etc.

So now what?
Thx Peeps!

---

### Post by Steveire on 2006-05-03
```

sudo debtags update

```
Does it apparently. I had the same problem and that's what a search turned up. I'd already updated with synaptic by then though, and after I did, adept was working.

---

### Post by fraterf93 on 2006-05-15
Yea thx, I did the same thing, and now my mini's running fine:D

---

