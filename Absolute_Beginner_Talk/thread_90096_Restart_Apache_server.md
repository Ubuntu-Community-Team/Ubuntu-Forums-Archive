---
title: "Restart Apache server"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by DevyD on 2005-11-14
Hi

Can anyone please tell me how to restart the apache server without restarting the server? I presume that there is a command line argument but I cannot find one. 

Thanks.

---

### Post by odin on 2005-11-14
Sorry if the answer is not very accurate but I dont have my linux machine here right now.

There should be something like this:

/etc/init.d/apache restart

you probably are using apache2 so it must be this instead:

/etc/init.d/apache2 restart

usually all the init files are under /etc/init.d and there you can stop start and restart them.


hope this helps

---

### Post by DevyD on 2005-11-14
Thanks Odin

---

### Post by odin on 2005-11-14
I'll take that as a "it worked" 

Totally wellcome :)

---

