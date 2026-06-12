---
title: "Hosting On Ubuntu"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Rhaddad on 2007-05-09
I want to host a website on ubuntu useing apache and MySQL, but I'm not sure how. 

will this enable me to change the MX servers and other CNAME servers as well?

---

### Post by Josh1 on 2007-05-09
The best option is to install Ubuntu Server, as you can choose an option that installs Apache,MySQL,PHP. Configuring DNS in Ubuntu isn't too hard.
Check out howtoforge.com

You might find this interesting:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

### Post by ikonia on 2007-05-09
Hi,

you can host a website on ubuntu using apache / mysql / php using the guide mentioned.

In your post you mentioned "will this allow me to change mx and cname's" 

this is not web hosting, that is dns hosting and although simple to install a dns server, it is quite complex and uncalled for to run your own dns setup properly. I advise you against that more so as at this point you don't know the different between apache hosting and dns records. there are plenty of webhosts that will manage dns for you.

---

