---
title: "Editing xorg.conf - permission denied!"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by mezerik on 2008-05-28
When I try to save the file xorg.conf after editing i get a permission denied error.  Also get this error when trying to copy sp-sc to usr/local/bin

I am the only user set up on my mac book pro, 4th generation.

I have checked that i am an administrator, well i think anyway.

Anyone got any ideas

When i look at the properties of xorg.conf it is grayed out on the permissions and says that i am not the owner and cannot change them.

---

### Post by mfox on 2008-05-28
You have to use sudo when you open up the file in your text editor and be able to save it afterwards.  Alternatively, use the su command to put yourself in root.

---

### Post by mezerik on 2008-05-28
tried typing in su in the terminal and it asks for my password then says Authentication failure

Not sure how i use sudo to edit the file either.  Any chance of some code.

---

### Post by gali98 on 2008-05-28
sudo gedit file
Kory

---

### Post by gali98 on 2008-05-28
to set up su to work on ubuntu you need to do:

sudo passwd

enter a password there. After that you can use su with that password.
Kory

---

### Post by mezerik on 2008-05-28
ahhha.

i typed

sudo gedit /etc/X11/xorg.conf

edited the file fine.

Only thing is i have a lot more editing to do and might be easier to do it all from the root.

What is the exact command for logging into the root?

---

### Post by mezerik on 2008-05-28
Thanks a lot, sussed it now :)

---

### Post by gali98 on 2008-05-28
Glad to have helped. If you feel that everything is working right could you mark this thread as solved?
(in thread tools) you can still post afterward.
Kory

---

### Post by cyberdork33 on 2008-05-28
> **mezerik said:**
> What is the exact command for logging into the root?You can also 'sudo su'

---

### Post by mfox on 2008-05-28
Didn't know that, cyberdork; thanks. :)

---

