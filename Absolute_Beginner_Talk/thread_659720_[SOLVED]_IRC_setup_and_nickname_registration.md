---
title: "[SOLVED] IRC setup and nickname registration"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by be4truth on 2008-01-06
I don't know but I feel pretty stupid with this IRC thing. Tutorials like this one [http://freenode.net/faq.shtml#userregistration]("http://freenode.net/faq.shtml#userregistration")
don't go anywhere for beginners. Can somebody explain how I register the nickname on freenode or ubuntu? I really need to know where to type this stuff in. Help like "/msg nickserv register <your-password>" doesn't work as long as I don't know where to type this in, whether the <> are typed or not and what response I should expect. ANd which nichname is it if only the passwd is asked. Do I need the register that nickname on all server I use or once for all? 
Anybody wants to help?
Thx in advance

---

### Post by mike^_^ on 2008-01-06
all the commands are entered into the 'chat bar' (same place you type normal text) 

from '/msg nickserv help register'

```
[02:15] >nickserv< help register
[02:15] -NickServ- Syntax: REGISTER <password>
[02:15] -NickServ- 
[02:15] -NickServ- This enables you to register your nickname with a
[02:15] -NickServ- password so only you can use it.  Please try to
[02:15] -NickServ- use obscure passwords that cannot be easily guessed.
[02:15] -NickServ- Passwords *ARE* case sensitive.  Once you have
[02:15] -NickServ- registered a nickname, you can use the SET and
[02:15] -NickServ- ACCESS commands to configure it.
[02:15] -NickServ- 
[02:15] -NickServ- Please IDENTIFY yourself to nickserv when you
[02:15] -NickServ- connect to the network. Many clients will allow you
[02:15] -NickServ- to automate this function.  If you don't IDENTIFY
[02:15] -NickServ- to NickServ for a period of 60 days or more, your
[02:15] -NickServ- nickname will be considered to be expired and it
[02:15] -NickServ- may be dropped.
```

you only need to register your nick once and it's good for all servers under the irc.freenode.net dns pool. Whatever nick you were using when you registered is the nick you will need to identify for when you join freenode and no, you dont need the <>.  You can also register multiple nicks and link them together under the same "account."

you could also '/join #freenode' if you need staff assistance

---

### Post by be4truth on 2008-01-06
Thx for your reply. The problem was that with the new program 'xchat-gnome' the registration doesn't work. As soon as I used Pidgin everything went ok.
I am using now xchat standard which works fine.

---

