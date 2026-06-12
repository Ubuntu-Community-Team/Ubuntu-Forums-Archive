---
title: "Help Me!"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by skydrifter2 on 2008-03-04
How can I log onto ubuntu if I do not know the username and password? My husband installed it and he is in the military and cannot remember what he used?  Can someone help me out on this?

---

### Post by kellemes on 2008-03-04
Does this help?
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

Edit: This is assuming you know the username by the way..

---

### Post by jken146 on 2008-03-04
Reboot the computer.  At the GRUB menu (you may need to press Escape to get to this) choose Ubuntu Recovery Mode.  When it has finished booting, you will be logged in as root.

To see the users, type ```
ls /home
```

To change a user's password, type ```
passwd username
``` replacing "username" with the username of the user in question.  Then type in the new password and press Enter (you won't see anything appear on the screen while you type).  Enter the new password a second time to confirm.

Then reboot: ```
reboot
```

---

### Post by skydrifter2 on 2008-03-04
yes, this helps, but I dont know the username either. Is there a way to  find the username?

---

### Post by philinux on 2008-03-04
ls /home

this command will show the username

---

### Post by skydrifter2 on 2008-03-04
Thanks to everyone, I will try this and let you know if I succeed!! He knew so much about computers, and now he is gone when I need him for help!!

---

