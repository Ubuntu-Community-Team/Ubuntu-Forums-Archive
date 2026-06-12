---
title: "Nvidia dont wanna work"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by kingvicious on 2006-08-02
i posted this in the video sound thing but no one is responding and well its been awhile so.. i thought i'd try my luck here plz respond i need help with this


ok well i read some of the threads of the people that cant get there nvidia drivers to work and well i couldnt find one with the same issue as me so here i go.
i went to wiki and searched nvidia found the how to for the install and followed it word for word untill about step ten where it asks to open the terminal and type sudo nvidia-glx-config enable. well when i do that i get the msg.

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

and well to be honest i dont even know what my x config is i read allot about it on the other topics simliar to this one but being iam a linux noob i really dont know and well anywas anyone got any ideas on how to fix this?

---

### Post by Dr. Nick on 2006-08-02
Ive had this error before, look here

[http://www.geocities.com/aebcoat/xorgresproblems.html#When_nvidia-glx-config_enable_fails](http://www.geocities.com/aebcoat/xorgresproblems.html#When_nvidia-glx-config_enable_fails)

---

### Post by kingvicious on 2006-08-02
thank you sooo sooo much that worked out great u are my life savor. iam keep that site in my favorites just incase thanks man

---

### Post by Dr. Nick on 2006-08-02
Glad it worked for you

---

