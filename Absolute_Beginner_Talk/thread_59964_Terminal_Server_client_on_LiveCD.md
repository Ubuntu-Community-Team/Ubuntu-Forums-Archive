---
title: "Terminal Server client on LiveCD"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by gcmartin on 2005-08-25
Has anyone seen this problem when using the "Terminal Server Client" to connect to Linux server(s) on the LAN using LIveCD?

When the LiveCD is booted, my system is on the LAN and I can browse locally and into the Internet. So my LAN servcies are OK.

When the Ubuntu version of "Terminal Server Client" is started from its menu, it is missing the XDMCP protocol. Is this a bug or is something not started? The client works for contacting a Microsoft Terminal server using the RDP client, but appears to be DISABLED for contacting a Linux server (XDMCP affords connecting to a Linux Terminal server). 

Please help. 
P.S. I posted this on 8/23, but I cannot find it today. I may have done something wrong, but unless someone tells me, I don't understand why I cannot find this in the forums???

Thanks

---

### Post by cwaldbieser on 2005-08-25
[QUOTE=gcmartin]
P.S. I posted this on 8/23, but I cannot find it today. I may have done something wrong, but unless someone tells me, I don't understand why I cannot find this in the forums???

Thanks[/QUOTE]
Just click on your user ID anywhere it is a link and then click on the "find all posts by gcmartin" link.  I found your earlier post that way.

Sorry, I don't know the answer to your terminal server question offhand.  I will try to take a look and find out.

---

### Post by gcmartin on 2005-08-26
Thanks for helpig me to see my other thread.

I did find another entry, but I'm not sure if it applies to the tsclient problem.

It suggest that the problem is in /etc/X11/gdm/gdm.conf. In here, the section [XDMCP]  has the following entry ===> Enable=false and MUST be changed to 'true'.

I have done this. But I am not sure how to stop and start gdm or anything such that this takes affect and I can then check to see if tsclient allow XDMCP as a selectable item.

Maybe guidance here if you feel that this is a solution.

---

### Post by gcmartin on 2005-08-26
I got this straight from the Terminal Server Client author. He says: "If you want XDMCP as an option, you'll have to install the xorg XNest package.  That should enable it."

I followed his directions and did the following:
1. apt-get upgrade
2. apt-get install xnest

Then, I went to Start...Internet...Terminal Server Client....XDMCP..."voila", I can now sign on to my Linux Terminal server on my local LAN. Ubuntu with XDMCP is a wonderful solution for home, or schools or ...

Now does anyone know how to get this message to the Ubuntu developers, so that they can properly set  this up in the LiveCD's ISO  package?

I appreciate ANY help here. Thanks

---

