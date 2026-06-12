---
title: "Domain Issue"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by tj71587 on 2007-11-02
I want to be able to type webserver in my web browser and be able to go to 192.168.1.5, but I am unable to dot hat with this /etc/hosts file.  Is there anything else I am missing?  Thanks

```

127.0.0.1		localhost.localdomain localhost
192.168.1.5		webserver.networkserver.com webserver
::1		localhost6.localdomain6 localhost6

```

---

### Post by Adramelech on 2007-11-02
[http://www.faqs.org/docs/securing/chap9sec95.html]("http://www.faqs.org/docs/securing/chap9sec95.html")


> 
After you are finished configuring your networking files, don't forget to restart your network for the changes to take effect.            

           [root@deep] /# /etc/rc.d/init.d/network restart


---

