---
title: "How to log in remotely to your own computer"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-01-26
I am a complete newbie and I would like to know how to set up my ubuntu computer in such a way that it is a server and I can log into remotely via some website or other means of communication. I would essentially like to be able to access everything on my computer remotely and preferably have it have good security. I would greatly appreciate if you could go into depth about it, recommend any good programs, and also please recommend any good websites. Thank you. 

Please reply here or email me at [email]jprb85@gmail.com[/email]

---

### Post by pbaehr on 2007-01-26
SSH is probably the solution you are looking for. You would be able to log in from another Linux computer pretty simply and even from Windows with a program like PuTTY. All the communication is encrypted, so from a security standpoint it's pretty solid. There are ways to increase the security if you're paranoid or dealing with sensitive information. Most commonly it is used for command line input, but if your computer is running an X-Server (check out cygwin if you're using Windows to connect) you can run graphical programs as well.

Check this out for some more information:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server)

---

