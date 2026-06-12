---
title: "Remote Server help"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by jazzman84116 on 2007-05-20
I ment Remote Login in or acess

---

### Post by finer recliner on 2007-05-20
what kind of server are you looking to make? http? ssh? ftp? smtp? ...etc?

if you don't understand what these terms are, then please explain in words what you would like the server to do.

---

### Post by jazzman84116 on 2007-05-20
Sorry I ment Remote Acess or login in

---

### Post by krisfrajer on 2007-05-20
try vnc. You can install it through synaptic:

System menu >> administration >> synaptic
and then install the following two packages:
vnc-common
xvncviewer

After the installation  it should be straight forward to use. vnc will allow you to connect to a vnc server and you would be controlling all the operations from your computer i.e. you will have a identical graphical Desktop of the server computer in your computer. To log in the server you only need two things: the IP of the remote computer and that remote computer has to have install and running vnc server. 

If you just want to manipulate only files on a remote computer then you can use ftp.

Hope it helps!

---

