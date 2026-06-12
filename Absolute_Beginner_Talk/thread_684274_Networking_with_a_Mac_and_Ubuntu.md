---
title: "Networking with a Mac and Ubuntu"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2008-01-31
Hello,

I have a desktop running Gutsy, and it is connected to a wireless router via the ethernet port on the router. So, it is not wireless. I have a MacBook laptop (running Leopard) that is connected to the same router via wireless. Thus, the two systems don't appear to realize that they're on the same network; that is, Ubuntu cannot see the Mac, and the Mac cannot see Ubuntu.

Typically, I know enough about networking to get things done, while being confused. I have been able to set up a Windows network under the same situation; in that there was a Windows desktop hooked up to the router via ethernet, and a Windows laptop via wireless. They could share files, printers, etc. with ease.

What steps do I need to take to allow this to happen correctly? Thanks so much.

Jon

---

### Post by mikeyphi on 2008-02-01
1. Setup the router to allow both systems to see each other.
2. install Samba and Mac equivalent on relevant systems.
3. setup file sharing on both systems.

---

### Post by ronmarley1 on 2008-02-01
You'll also need to set up a samba user on the Ubuntu box.  See this link.
[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)

---

