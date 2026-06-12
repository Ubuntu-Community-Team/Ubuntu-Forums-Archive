---
title: "Administrator rights?"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by equal on 2005-06-20
I'm not quite sure how to explain this. I was working on my computer yesterday, and I was trying to create a folder, and the option was greyed out. When I went up a level, right-clicked on the folder, and chose properties, it told me that I didn't have the administrative rights to change the folder properties. To be clear, I'm the only user on my computer, there are no other users defined. Any idea what might be the problem? 

I'll post a clearer explaination when I get home.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=equal]I'm not quite sure how to explain this. I was working on my computer yesterday, and I was trying to create a folder, and the option was greyed out. When I went up a level, right-clicked on the folder, and chose properties, it told me that I didn't have the administrative rights to change the folder properties. To be clear, I'm the only user on my computer, there are no other users defined. Any idea what might be the problem? 

I'll post a clearer explaination when I get home.[/QUOTE]

Its clear enough. I'll explain it to you.

In Ubuntu, you run the OS as you- a normal user. Unlike most Windows installs, the main user does not have root priviledges in Ubuntu. This is to avoid a major problem in Windows- programs installing without the user knowing. Plus it makes it harder to mess things up.

I bet you are thinking "whats the point of NO admin account?"The answer is that Linux's multi-user set up is VERY elegant. At any time you- a normal user- can become an admin with two commands:

"sudo" for commandline apps.

"gksudo" for graphical apps. 

Lets say you wanted to fix that problem- you wanted to browse the file manager as the admin. run this command:

> gksudo nautilus 

now you have the power. Notice how it asked for you password. That is the big security feature. Macs do the same thing. If you ever are doing something that shouldn't need be admin to do (say surf with Firefox) and its asks for a password you then KNOW that something fishy is going on. 

With this protection, malware on Ubuntu may never exist.

---

### Post by desdinova on 2005-06-20
[QUOTE=equal]I'm not quite sure how to explain this. I was working on my computer yesterday, and I was trying to create a folder, and the option was greyed out. When I went up a level, right-clicked on the folder, and chose properties, it told me that I didn't have the administrative rights to change the folder properties. To be clear, I'm the only user on my computer, there are no other users defined. Any idea what might be the problem? 

I'll post a clearer explaination when I get home.[/QUOTE]

A lot of it will depend in exactly where you were trying to create a folder - in the system directories such as /usr or /lib you won't have permission unless you become root. Its to protect you from deleting important system files for example

---

### Post by equal on 2005-06-20
[QUOTE=desdinova]A lot of it will depend in exactly where you were trying to create a folder - in the system directories such as /usr or /lib you won't have permission unless you become root. Its to protect you from deleting important system files for example[/QUOTE]
 Thanks so much guys, you're all helping quite a bit :)

---

