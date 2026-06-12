---
title: "Can't login any more after upgrade to Hoary"
date: 2005-02-09
forum: Apple PPC Users
---

### Post by robsta on 2005-02-09
Hi, 

after upgrading my iBook to Hoary i can't log in to GNOME any more.
After typing user-name and password in GDM the screen clears in "ubuntu-chocolate" colour and the disk stops scratching after a few seconds. Nothing more happens. 

No errors are obvious:

mostpress:/etc# cat /home/robert/.xsession-errors
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/mostpress:/tmp/.ICE-unix/5245
mostpress:/etc#

The same happens when i try to log into a new account which doesn't have old config-files around.

I forgot to mention that logging into my jhbuild't gnome works.

Thanks for any advice, 
Rob

---

### Post by robsta on 2005-02-10
Ok, so i got a hoary .iso and reinstalled the box.
Maybe something was currupted in the process of upgrading SID -> warty -> hoary.
Not it works again.
- Rob

---

