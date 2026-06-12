---
title: "fqdn"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by wgato on 2006-10-05
How do I find out what my FQDN?  

$ hostname -f
localhost.localdomain

i figure i need to change that but what to and how?
i know the machine name but dont know what my localdomain is.  the is address from my isp? 
the other machines on the network are all windows machine and the network neighborhood is named 912...

sorry, i realize this is a really basic question

thanks

---

### Post by dmizer on 2006-10-05
localhost.localdomain is your fully qualified domain name.

what are you trying to do?
1) host a locally accessable website?
2) host samba shares?

what is your need to know the fully qualified domain name?

---

### Post by wgato on 2006-10-05
I am trying to setup postfix so i can receive messages from cron.

I am already hsucessfully hosting a website locally and am sharing files with the windows machines through samba.

---

### Post by po0f on 2006-10-05
wgato,

You can do this in /etc/hosts:
```

#IP address    fqdn                     aliases
127.0.0.1       mybox.mydomain   localhost,mybox
```

---

### Post by wgato on 2006-10-06
thanks poOf,
but i am wondering, how do i find out what 'mydomain' is?

---

