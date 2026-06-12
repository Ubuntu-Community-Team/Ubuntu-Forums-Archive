---
title: "Using a router"
date: 2011-10-18
forum: Any Other OS
---

### Post by tech291083 on 2011-10-18
Dear Friends,

My ISP uses MAC binding, which requires me to use a router if I want to access the net using two different computers simultaneously.  I have 2 pcs one with Windows XP Home and another with Ubuntu 10.10 and a DSL connection with a username and password. I need to dial everytime I need to access the net. Now I have this router with me Netgear WGR614v6. Can I use this router to connect to the net?

Another thing is which OS or pc I should use to configure this router? Should I use the Win XP Home pc or the one with Ubuntu 10.10 on it? Or am I required to configure it on both pcs? Once I dial to get connected to the ISP and get the connection working, then I do not need to dial again using another pc, is this the right way? The second pc will automatically get connected to the net once the connection is successfully dialled by the first pc. Right? I need your help here, please do help. Thanks.

---

### Post by SirDrexl on 2011-10-19
We would really need more info about how your ISP works.  How are you connecting now and what modem do you use?

Typically the router is configured through a web browser, and it  shouldn't make a difference which OS you use.  Although, in some cases a  particular browser may have trouble for some reason and you'd have to  try another one.

---

### Post by tech291083 on 2011-10-19
> **SirDrexl said:**
> We would really need more info about how your ISP works.  How are you connecting now and what modem do you use?


Hi,

Thanks for the reply.
I do not use a modem to connect. It is a CAT 5 cable coming from a switch on the top floor of my building, which was placed there by my local ISP. Other users also get their connection from this switch only. It is a DSL ethernet connection. I have been given a username and password. They do MAC binding and thus I have been told to use a router to connect more than one pc to the net simultaneously. Please help me, I am really confused here and I have mentioned some concerns in my previous post as well, thanks.

---

### Post by SirDrexl on 2011-10-19
In that case, the router would be making the connection itself.  Do you know what kind of connection it is?  I mean, more specific than just DSL.  Many DSL connections (including mine) use PPPoE, for instance.

If it's PPPoE, you would go into the router and enter your username and password in the section for the connection.  According to the manual, the router's address is [http://www.routerlogin.net](http://www.routerlogin.net).

---

### Post by mips on 2011-10-19
> **tech291083 said:**
> Hi,

Thanks for the reply.
I do not use a modem to connect. It is a CAT 5 cable coming from a switch on the top floor of my building, which was placed there by my local ISP. Other users also get their connection from this switch only. It is a DSL ethernet connection. I have been given a username and password. They do MAC binding and thus I have been told to use a router to connect more than one pc to the net simultaneously. Please help me, I am really confused here and I have mentioned some concerns in my previous post as well, thanks.

The MAC binding would have to be setup for the routers MAC address.

Could you please provide a link to your ISP and service/package you are using!

---

### Post by tech291083 on 2011-10-20
> **SirDrexl said:**
> Do you know what kind of connection it is? 

If it's PPPoE, you would go into the router and enter your username and password in the section for the connection.  According to the manual, the router's address is [http://www.routerlogin.net](http://www.routerlogin.net).


Yes, mine is the same ie DSL with PPPoE. Now I have the following questions for you.

Which OS or pc I should use to configure this router using the web browser as mentioned by you earlier? Should I use the Win XP Home pc or the one with Ubuntu 10.10 on it? Or both pcs? Once I dial to get connected to the ISP from one pc and get the connection working, then I do not need to dial again from another pc if I also want to use it simultaneously, correct? The second pc will automatically get connected to the net once the connection is successfully dialled by the first pc, right? Now since both pcs are connnected to the router then I can just switch off the first pc (the one from which I dialled the connection) and continue using the second pc to surf the net. Am I right here? I am new to networking and need your help here, so do help. Thanks.

---

### Post by SirDrexl on 2011-10-20
It shouldn't matter which OS you use to configure the router.  You just need a web browser.  Ubuntu might have less going on in the background to interfere with the process though, so try that first.

What you will do is configure the router to "dial in" and it will stay connected, even when the PCs are off.  Page 3-5 of the router's manual will tell you how to do this.  Note that you will select "other" as the ISP since it uses that for PPPoE.

The manual, if you don't have it, can be downloaded here: [http://search.yahoo.com/r/_ylt=A0oG7mwWW6BOFUgA.wNXNyoA;_ylu=X3oDMTEyYWxtNmxnBHNlYwNzcgRwb3MDMQRjb2xvA2FjMgR2dGlkA0RGUjVfNzQ-/SIG=12gg3hho7/EXP=1319160726/**http%3a//kbserver.netgear.com/pdf/wgr614v6_ref_man_20Apr05.pdf](http://search.yahoo.com/r/_ylt=A0oG7mwWW6BOFUgA.wNXNyoA;_ylu=X3oDMTEyYWxtNmxnBHNlYwNzcgRwb3MDMQRjb2xvA2FjMgR2dGlkA0RGUjVfNzQ-/SIG=12gg3hho7/EXP=1319160726/**http%3a//kbserver.netgear.com/pdf/wgr614v6_ref_man_20Apr05.pdf)

BTW, you should update the firmware for the router if it isn't the latest.  Here's the page for that: [http://support.netgear.com/app/products/model/a_id/2588](http://support.netgear.com/app/products/model/a_id/2588)

---

### Post by tech291083 on 2011-11-06
Hi,

I have set it up correctly using the Internet Explorer  version 8 on my Windows XP Home pc. I just opened this page 192.168.1.1 in IE 8 and  did the settings ie provided user name and password the for the  connection. Now this pc connects to the internet automatically, I do not  have to dial it any more as was the case earlier. I just have to plug  the internet cable into the back of my router and then plug one end of  an ethernet cable (CAT 5) into any LAN port on the router and another  end into the pc. This automatically starts the internet for me. I just  open Internet Explorer and start using the internet now. Simple as that.  The router dials for me now. 

But I have another pc with Ubuntu  10.10 on it which does not seem to connect to the net, whenever I  connect it with the ethernet cable to the router (just like the 1st  Windows XP Home pc). Why so? It should automatically start the net once  it is connected to the router as per my understanding, correct me if I  am wrong here. This is really irritating me a lot. Please help me. I have come so far with your help and need one more piece of guidance from you. My router is Netgear WGR614v6. Thanks.

---

### Post by tech291083 on 2011-11-06
Ok, I seem to have found the solution after all. Here is the link to the solution. 

[http://visibletrap.blogspot.com/2009/03/solved-cant-connect-with-wired-dhcp.html](http://visibletrap.blogspot.com/2009/03/solved-cant-connect-with-wired-dhcp.html)

And this what I tried. 


> 

Edit /etc/NetworkManager/nm-system-settings.conf and changed managed=false to managed=true.

Reboot

Done.


---

