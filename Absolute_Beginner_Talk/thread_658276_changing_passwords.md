---
title: "changing passwords"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by lore lei on 2008-01-04
This is my first post.

Computers are somewhat new to me other than dinking around for years as a dumb user and now  ready to get real. I have had Ubuntu since April and have learned much on my own reading "help" and this forum. 

I choose Ubuntu because my knowledge of computer technology is primitive, I don't want habits associated with Windows, Ubuntu is revered for its security, my passion is art and more.

My hope is this forum will enable me to move to the next level and answers given are smart and contain approachable solutions for an eager and attentive beginner. 

Thank you to those who remember my user ID when browsing and are interested in helping me. 

FINALLY MY QUESTION

How do I change user passwords. login, key, synaptic...
and with change is the password for all tasks?

If the only answer is terminal. I will need clear instructions.

DETAILS
have not tried re boot yet
want to adept terminal use when better user
tried user groups will try again
I didn't forget it I just want to change it

have to go to work
I will try suggestions and thank later
thank you for now

---

### Post by reckless2k2 on 2008-01-04
in the adminstration menu is the user and groups panel to make all of your changes or add/remove users.

---

### Post by Techwiz on 2008-01-04
If you are the administrator of the computer do this:
Go to System then go to Administration then on to Users and Groups, select you user Click the Properties button then twoards the bottom you should be able to change your password.
So in short:
System>Administration>Users and Groups>Click your user name>Properties>Change your password>Click OK>DONE!
Hope this works!

---

### Post by LowSky on 2008-01-04
i'm pretty sure it in the menu. system>admin>users, you can and/delete user and change passwords

---

### Post by Lostincyberspace on 2008-01-04
if you want to change user and groups then you need to got the system menu then the administration submenu and then in to the users and groups program. Then you click on one of the users there and click on the properties and change what you want.

---

### Post by steeleyuk on 2008-01-04
And if you really want to do it in the terminal ;)

Applications > Accessories > Terminal

Type:

passwd <username of the account you want to change>

Then you'll be asked to enter you current password. Then it'll ask you twice to enter your new password.

---

### Post by LowSky on 2008-01-04
very handy if you build a linux box, and dont use it for months because you lost interest and use another computer, then go back and need it... little story from my life..lol

If you select "Ubuntu Recovery Mode" in the bootup menu, it will boot you to a terminal with root access without prompting for a password.

Then use the command "passwd userName" to set a new password for yourself. Obviously, userName is your username.

If you have forgotten your username as well, then "ls /home" from the terminal will tell you the user directories on your system, which will job your memory. Alternatively "tail /etc/passwd" should help.

---

### Post by lore lei on 2008-01-04
easy thank you the user group worked

---

