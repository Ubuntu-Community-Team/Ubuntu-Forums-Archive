---
title: "Remote desk top"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by bugster on 2007-08-17
Is it possible to have a remote desk top program in Ubuntu which will log onto a remote Windows 2003 server?  I work from home a lot using Ubuntu but have to log on to the server at work about once an hour and at the moment this means rebooting into xp each time.

---

### Post by mikex on 2007-08-17
Hey I've been wanting to do the same thing, and i just found this. I'm at work so i can't set it up. I'm going to try it later today.

[http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/)

---

### Post by bodhi.zazen on 2007-08-17
To connect to windows form Ubuntu use Terminal Services Client :

[http://blog.dantup.me.uk/search?q=RDP&x=0&y=0](http://blog.dantup.me.uk/search?q=RDP&x=0&y=0)

---

### Post by bugster on 2007-08-17
Thanks both.  I've found the Terminal Server Client and know the answers to most of the questions except Client Hostname.  Is this the name of the PC I'm trying to log in from?

---

### Post by steve.horsley on 2007-08-17
No, it's the name (or IP address) of the server you are trying to connect to. You probably want to use RDP (Remote Desktop Protocol) which is the normal remote desktop that comes with Windows (I forget what they call it).

---

### Post by bugster on 2007-08-17
Thanks Steve.  Your answer threw me a bit because I had used the IP address as the answer to an earlier question "Domain".   Here's what I've tried so far

Computer:  WORK_TS
Protocol:    RDP
User Name:   My Name
Password:  My Password
Domain:  123.456.789.123
Client Host Name:  ??????? This is the one I don't understand.

Any help appreciated.

---

### Post by bodhi.zazen on 2007-08-17
You can use the server name if you add it to /etc/hosts (on the client)

<ip> <server_name>

---

### Post by bugster on 2007-08-17
Thanks bodhi - though I'm afraid you lost me there.  I've looked in /etc folder and there is no /hosts sub folder.  Should I make one?

---

### Post by bodhi.zazen on 2007-08-17
sorry, it is a file

/etc/hosts

you will see 

127.0.0.1 localhost

just add

192.168.1.xx <server name>

then you can use the name rather then IP to connect

---

