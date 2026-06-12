---
title: "Wheres desktop"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by nhnewbie on 2007-06-12
I just installed Ubuntu server 6.06 within vmware workstation and am able to login but would like to get to a desktop if possible. I understand I may need to use the get_apt command but am unsure how to do that from the command prompt. Also, without a desktop browser how can I confirm I have a connection to the internet.  

Thanks

---

### Post by lapsey on 2007-06-12
sudo apt-get install ubuntu-desktop


then reboot

---

### Post by Inxsible on 2007-06-12
The Ubuntu server edition does NOT have a GUI desktop. If you want a desktop, you would have to use the LiveCD to install it. Or you can try to install ubuntu-desktop which will install the GUI

---

### Post by lapsey on 2007-06-12
you can check internet from the command line (which is the default environment for server, btw) by using 

ping google.com

there are many other ways to do this but that is the easiest

---

### Post by Inxsible on 2007-06-12
lapsey by a second !!! ;)

---

### Post by nhnewbie on 2007-06-12
The apt-get Install ubuntu-desktop command worked.  Thank you for the help and one heck of  a time saver!

NHnewbie:p:

---

