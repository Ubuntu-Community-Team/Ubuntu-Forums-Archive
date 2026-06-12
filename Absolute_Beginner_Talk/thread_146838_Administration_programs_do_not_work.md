---
title: "Administration programs do not work"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by nate_2001 on 2006-03-19
Hi.  I just installed Ubuntu using a Breezy Badger disc.  I installed it just fine and it loads into gnome, but I cannot get programs that require a password to work.  I'm trying to set up my wireless network, but when I open anything that asks for my password, I enter it and the window closes but nothing happens.  A new window does not open ... it seems like the program just dies.  I am really new to this, so very basic answers might be in order.

Thanks!

---

### Post by dermotti on 2006-03-19
Ive seen that happen if you are puttin gin the wrong password...

Go into you terminal and type **sudo top**
and enter your password. If it doesnt work you are typing the wrong password.

---

### Post by xenmax on 2006-03-19
Refer to this thread:
[http://www.ubuntuforums.org/showthread.php?t=146859](http://www.ubuntuforums.org/showthread.php?t=146859)
I configured my network from cmd-line. I am sure there are loads of how-tos to do that if you need help. Also i can help too if it is static ip addr config - not dhcp - dont know much abt that.

---

### Post by steve.horsley on 2006-03-19
Just a thought. Only the very first user that you configured while installing is allowed to do administrative stuff, even if they enter their password correctly into the popup box. This can be corrected later, but only by the first user.

---

### Post by nate_2001 on 2006-03-19
Thanks folks.  The thread posted above fixed my problem.  I just reinstalled the OS using the normal install rather than the expert version.

---

