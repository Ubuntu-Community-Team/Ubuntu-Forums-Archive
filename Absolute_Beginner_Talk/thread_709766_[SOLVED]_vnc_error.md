---
title: "[SOLVED] vnc error"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by cane1832 on 2008-02-27
ok 

i am trying to ssh to vnc to my desktop and i make the ssh connection and then when i run the

vncviewer -via xxx.xxx.xx.xxx my-desktop:0

i give it my password and then i get this

 CConn:       connected to host localhost port 5599
channel 3: open failed: connect failed: Connection refused
 main:        End of stream

anyone help me out id appreciate it
thanks
cane

---

### Post by Dr Small on 2008-02-27
Have you read this wiki page?
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

Dr Small

---

### Post by cane1832 on 2008-02-27
yes there is nothing on this on that page

---

### Post by Dr Small on 2008-02-27
Well, it is definately a port problem, so have you tried opening the port?

---

### Post by cane1832 on 2008-02-27
when im in ssh and use the top command i see that there isn't a gnome-panel running

it has been running for 19 days straight and i think it may have rebooted

how could i promt a loggin in to xwindow

---

