---
title: "apt-get behind a proxy?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-05-31
Hello,
Can anyone tell me how to get apt-get working from behind a proxy?

I can ping other machines on my lan, I cn browse the web with firefox, and I ve set up the proxy settings from the menu.

Thanks for any help!

---

### Post by linuchsan on 2006-05-31
You have to specify a port number in the sources.list.
Like deb [http://xx.archive.ubuntu.com:xxx/blabla](http://xx.archive.ubuntu.com:xxx/blabla).....

---

### Post by zappafrank on 2006-05-31
make a file /etc/apt/apt.conf and add the following lines:


Acquire::http::Proxy "http://user:pass@xxx.xxx.xxx.xxx:port/"; 
Acquire::ftp::Proxy "http://user:pass@xxx.xxx.xxx.xxx:port/";

---

### Post by zvezdogled on 2006-05-31
or you can just type in terminal:
export http_proxy=http://user:pass@proxy:port/
export http_proxy=ftp://user:pass@proxy:port/

that will work for that terminal until you close it an you must retype it ech time...

---

