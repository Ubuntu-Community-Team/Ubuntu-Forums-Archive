---
title: "PHP problems!!"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by benclinch on 2006-07-18
Hi,
I have used Synaptic to install Apache, this works fine.
Next steop is to install PHP, I used synaptic for this too, but it doesn't seem to work!
I have created a simple phpinfo file, and when i try to open it in firefox, it wants to save it, it doesn't understand what it is. In opera it just displays the php code.On any of my networked computers with Windows and IE it wants to download it too.
I used synaptic to install php5, and pretty much everything related to it!

Please help, I am quite desperate.

Ben

---

### Post by az on 2006-07-18
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by benclinch on 2006-07-18
I followed the steps about if it asks to downlaod the php file.
But when I try to restart Apache it says:
```
 * Forcing reload of apache 2.0 web server... (13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```
What should I do to fix this?

---

### Post by az on 2006-07-18
Do you have apache or apache2 installed?  If you have both installed, remove apache.  You only want apache2 running.

---

### Post by benclinch on 2006-07-18
I have Apache2, no other versions of apache running :mad:

---

### Post by az on 2006-07-18
What versions of php and mysql do you have?

dpkg -l |grep php
dpkg -l |grep mysql

---

### Post by benclinch on 2006-07-18
I've fixed it now!!
I just thought that uninstalling everything and starting again would help, and it did! All fixed.
Thanks for your help
One last thing though...
How can I change my /var/www area so that when i am logged on (my username is ben) I can drag and drop etc files into www. Rather than using sudo and terminal etc...

Ben

---

### Post by az on 2006-07-18
> **benclinch said:**
> I've fixed it now!!
I just thought that uninstalling everything and starting again would help, and it did! All fixed.
Thanks for your help
One last thing though...
How can I change my /var/www area so that when i am logged on (my username is ben) I can drag and drop etc files into www. Rather than using sudo and terminal etc...

Ben

Damn good question.  I am not sure.  Better start a new thread about that in the security section.  

I have had success with adding my user to the www-data group.  That way, I can ssh into the box as the user and upload my files.   Then, when I am done, I can remove that user from the www-data group.

Maybe I am paranoid?  I just don't know.

---

### Post by Kilz on 2006-07-18
The way I do it is type
```
gksudo nautilus
``` in the terminal. That opens up nautilus as root. I transfer the files and then close it. You can even add it to the administration menu with the alacarte menu editor so the only thing you need to do is enter a password.

---

