---
title: "Webserver - Localhost to view Zoneminder"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Andrew1234 on 2007-01-11
Hi 
I need a little advice if anyone can give me it,

I am using Zoneminder (I have it installed on my Ubuntu Desktop 6.10 working great)

But I would like to able to view my work site via the internet from my home(XP Box) using zoneminder on the work PC(Ubuntu). Is it possible to connect to the work PC with Zoneminder and view the pictures? The way I would like to be able to view the pictures would be able to just type my IP address from my home or other location without Zoneminder installed on (eg [http://111.111.11/zm/zm.php](http://111.111.11/zm/zm.php)) 

I have a static IP address at work, but I have no idea how to set this up. Do I need Ubuntu server/webserver? 

Many thanks
Andrew

---

### Post by Scorpuk on 2007-01-11
I have dabbled with zoneminder on my own ubuntu box and this shoudl be no problem.

I think it will all depend on how your network is setup at work. - How is it?


If you browse to your work's internet IP address what do you get?

---

### Post by Andrew1234 on 2007-01-11
Thanks for the reply, if I am on the work PC (Ubuntu) and enter the IP address or localhost I get the router index.htm,( I have apache installed )

If I am at home and use my XP box and put the IP address in I get a error page 

> 
Connection Interrupted
The document contains no data.
The network link was interrupted while negotiating a connection. Please try again.


---

### Post by Scorpuk on 2007-01-12
You will have to set up port forwarding on your router.


Set port 80 to forward (TCP) to the internal network IP address of your ubuntu box.


I think the reason you get no response from your XP box is that your router is not setup for remote administration so drops the request.

---

### Post by Andrew1234 on 2007-01-18
I had probelms that the ISP had not set up my IP address properly as well, which is supposed to have been sorted out.

I have a speedtouch router, and have been reading the help files but am a little lost to how to set up for port forwarding.

> IP Routing Click this link to display the IP Routing page.
Routing can be useful when subnetting your local network. To add a static IP route
proceed as follows:
1 Click New.
2 Specify the destination IP address (use the prefix notation to apply a
subnetmask), Gateway, Interface and Metric.
3 Click Apply to add the entry to the table.
4 Click Save all to save your changes to persistent memory.


Am I in the right area? Or can you advise me .Thanks Andrew

---

