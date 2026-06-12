---
title: "Making a server"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by wildgene789 on 2008-01-20
Hey guys i just downloaded ubuntu server 7.10 and i was wondering if there is a step by step tutorial that will help me setup a web site and enable file sharing for my linux and window computers to connect to.

---

### Post by kebes on 2008-01-20
This looks like a rather detailed how-to (it's for Ubuntu 6.06, but the steps are nearly identical for 7.10... just use "Gutsy" instead of "Dapper"):
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

Of course, you won't need to follow all the steps (it depends what kinds of things you want to do with your server). Using that guide, you can install Ubuntu server. To run a website, you'll install the packages "apache2" and "php5".

To create a Windows share, install "samba".

---

### Post by wildgene789 on 2008-01-21
thank you i will try this

---

### Post by hyper_ch on 2008-01-21
> **kebes said:**
> 
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

You could also point to the gutsy howto:

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

If it's just 1 website there are easier ways than the perfect howtos. The perfect howtos will setup an ISP-ready server. Meaning dns hosting, website hosting, email hosting, ftp/sftp transfer, multiple resellers and clients.... (if you also install ISPConfig).

So if it's just one website that you want to test on... there are easier way. However if you want to setup multiple ones, then I recommend the perfect setup.

---

### Post by wildgene789 on 2008-01-21
thank you

---

