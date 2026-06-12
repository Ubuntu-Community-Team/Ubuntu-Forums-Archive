---
title: "Plz, how to do XDMCP ??"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-05
Hi Linux community !!
  
I am trying to use the XDMCP 'cos I start to gather linux boxes in network...
Soo, I did : 
  
On the XDMCP server PC:
-----------------------
[xdmcp]
Enable=true
  
 
# /etc/init.d/gdm restart
   
Stopping GNOME Display Manager: gdm.
Starting GNOME Display Manager: gdm.
  
   
On the client:
-----------------------
X -query IP_server
  
  
But I get the error message:
X: user not authorized to run the X server, aborting.
   
   
Please what to do now ??
  
Kind regards ,

Patrick

---

### Post by patrick295767 on 2005-11-05
Is XDMCP secured if no firewall ??

thanks !!!

---

### Post by patrick295767 on 2005-11-05
I found !!! 

X -query works from the tty1 console ....

---

