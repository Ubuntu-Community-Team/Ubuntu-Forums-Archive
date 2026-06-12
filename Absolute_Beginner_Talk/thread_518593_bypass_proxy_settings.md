---
title: "bypass proxy settings"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by sazan on 2007-08-06
hey can anyone tell me how i can bypass proxy in ubuntu 5.10 ver.... i am in college and unable to access the sites where i can download suffs... 
help please.........!!@!@!@!!!!

---

### Post by sameer.iitg on 2007-08-06
Hi
You can set your network proxy which is an option under the system tab in the main menu. 
Moreover you can set it in your .bashrc file

just do 

vi ~/.bashrc

and add the following lines (if needed) :

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/

---

### Post by sameer.iitg on 2007-08-06
The lines to be added are :

```


export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/
```


:)

---

