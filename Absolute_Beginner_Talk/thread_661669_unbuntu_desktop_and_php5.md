---
title: "unbuntu desktop and php5?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by kobra1234 on 2008-01-08
Hi!

I would like to do some local dev in php5 on my ubuntu machine. I only got the desktop version installed 7.02 I think...
Is there any way one can install apache on desktop or unother solution to execute php5 server side code on desktop machine??

thx

---

### Post by hyper_ch on 2008-01-08
by install the php5 and php5-cli packages you can run .php files from your command line. However if you want to do web developping you'll need apache or another webserver also.

---

### Post by kobra1234 on 2008-01-12
> **hyper_ch said:**
> by install the php5 and php5-cli packages you can run .php files from your command line. However if you want to do web developping you'll need apache or another webserver also.

ok, thanks! And can I install Apache on ubuntu desktop or do I need the ubuntu server?

---

### Post by hyper_ch on 2008-01-12
A server is nothing more than an operating system running services that wait to be called by other computers... so do you think you can install apache?

---

### Post by GavinZac on 2008-01-12
> **kobra1234 said:**
> ok, thanks! And can I install Apache on ubuntu desktop or do I need the ubuntu server?

> **hyper_ch said:**
> A server is nothing more than an operating system running services that wait to be called by other computers... so do you think you can install apache?

to clarify... yes you can ;)

I have php5 and apache installed on my "ubuntu-desktop" laptop, and have created a little shell script to stop/start them whenever i need to.

---

### Post by mcduck on 2008-01-12
You don't need the server edition, all the things from different Ubuntu versions can be installed on every other version. The different versions just give you a different starting point.

Easiest way to get a working Apache, MySQL and PHP is to run 'sudo tasksel install lamp-server'. 
Alternatively to do the same with a GUI open Synaptic (in System/Administration/Synaptic Package Manager), then go to Edit/Mark Packages by Task, select 'LAMP server', click OK and then Apply.

---

### Post by kobra1234 on 2008-01-12
thanks a lot everybody!
I now have it installed!

---

### Post by GavinZac on 2008-01-13
> **kobra1234 said:**
> thanks a lot everybody!
I now have it installed!

dont forget the thanks button ;)

---

