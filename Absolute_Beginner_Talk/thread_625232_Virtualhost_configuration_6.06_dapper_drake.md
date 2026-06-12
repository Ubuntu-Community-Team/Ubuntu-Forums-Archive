---
title: "Virtualhost configuration 6.06 dapper drake"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by pdumbelton on 2007-11-27
Hi All,

I'm new to Ubuntu so please be gentle with me..

I am running 6.06 Dapper Drake. I'm having trouble configuring virtual hosts.

I have followed the available documentation on Virtual Hosts but have hit a snag... no doubt through my own fault.

I copied the Default "/etc/apache2/sites-available/Default" to make my new VH. I made no changes to the Default.
New VH is called trackinganywhere.

Below shows the changes I made to "trackinganywhere"
NameVirtualHost *:80
<VirtualHost *>
	ServerAdmin [email]tech@cloverpoint.com[/email]
	ServerName trackinganywhere.com
	ServerAlias [www.trackinganywhere.com](www.trackinganywhere.com)
	DocumentRoot /var/www/trackinganywhere

I then used the a2ensite command to enable the site. Then I rebooted the server. When the server restarted it displays the this [warn] NAMEVIRTUALHOST *:80 HAS NO VIRTUALHOST

when I try to hit my site it works just fine... this is great but I'm concerned by the warnng...
I plan to add further sites therefore create more VH so I want to get this sorted as I fear the moment I need to do this I'll have problems.
My server only has 1 IP.

Your thoughts are apreciated.

cheers, Pete.

---

