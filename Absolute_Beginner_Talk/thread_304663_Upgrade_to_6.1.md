---
title: "Upgrade to 6.1"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by captgadget on 2006-11-22
Is it possible to upgrade to 6.1 from 6.06 without losing all the information on the hd? I've come so far here that I don't want to have to reload everything.

---

### Post by rigol on 2006-11-22
Is there any specific reason you want to upgrade to Egdy?
Because otherwise I would advise to stay with Dapper.

---

### Post by bigken on 2006-11-22
in your source list change dapper to edgy the do a apt-get update and upgrade ;)


sudo gedit /etc/apt/sources.list

---

### Post by Spin Doctor on 2006-11-22
I upgraded from 6.06LTS to 6.1 without losing anything.

Make sure you have a network connection and run the following command:

```
gksu "update-manager -c"
```If you havenot read the release notes:
[http://www.ubuntu.com/download/releasenotes/610](http://www.ubuntu.com/download/releasenotes/610)

---

### Post by RobsterUK on 2006-11-22
Bear in mind that the update process downloads about 1GB of data so it can take some time, depending on the speed of your connection.

---

