---
title: "Loading MySQL on Startup"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by alana on 2007-02-28
I have followed the instructions for installing SQL at: [https://help.ubuntu.com/6.10/ubuntu/...databases.html](https://help.ubuntu.com/6.10/ubuntu/...databases.html)

I am now trying to get SQL to startup when the computer is started.  I can't find any steps on how to do this...

Thanks!

---

### Post by astrolabio on 2007-02-28
Your link doesn't work, so i'll make some wild guess.

Try installing sysv-rc-conf
sudo apt-get install sysv-rc-conf

Then type (guess what)
sysv-rc-conf

you can use it to set what services you want activated. Look for mysql and X it.

To exit when finished press Q.

---

### Post by alana on 2007-02-28
Thanks!  That did the trick :)

---

