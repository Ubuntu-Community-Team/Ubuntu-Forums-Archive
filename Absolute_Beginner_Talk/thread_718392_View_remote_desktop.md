---
title: "View remote desktop"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Aleks67 on 2008-03-08
I have installed ubuntu-desktop on my remote server, how do I now view the desktop on my local PC with my SSH client Putty or DataFreeway?

Thank you.

---

### Post by acidsolution on 2008-03-08
if you want to view desktop you can try vncviewer 
only if vnc session is made 
you can make vnc session by 
$ vncserver:1
$ vncpasswd
now type password

now you can access the machine from remote machine by 
if you are using windows that you can download any free vnc viewer software 
vncviewer your ip :1
and password 

this must help you

---

### Post by Aleks67 on 2008-03-08
Sorry, i dont quite understand you? $ vncserver:1?
If i type it in Putty, It says command not recognized.

What am i doing wrong?

---

### Post by Aleks67 on 2008-03-08
Hold on, after Re-reading your post.. i get the idea i need to install VNC?

Well i did, vnc-4_1_2-x86_win32_viewer.exe

from [http://www.realvnc.com/cgi-bin/download.cgi](http://www.realvnc.com/cgi-bin/download.cgi)

I then open it, Type server name in.. And it says, unable to connect to host: Connection refused (10061)

Any ideas?

---

### Post by acidsolution on 2008-03-08
so you are using windows 
try to download free vnc viewer 
[http://www.realvnc.com/products/free/4.1/winvncviewer.html](http://www.realvnc.com/products/free/4.1/winvncviewer.html)
and than install it and try as above not in putty but in vncviewer 

your ip :1

:1 shows the vncsession you have created in server 

but before doing that you should ensure vncserver running on your remote server 
this can be done as mentioned in mine previous post

---

### Post by acidsolution on 2008-03-08
ok first start vncserver in remote server 
as described in first post 

you can make vnc server  by 
$ vncserver:1
$ vncpasswd
now type password
this should be done in remote server which you want to access

---

