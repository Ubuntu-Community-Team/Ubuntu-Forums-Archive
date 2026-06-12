---
title: "Multiple Websites behind single router?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-05-22
Well I have a server behind a router and I have a domain pointing to the server. Everything works fine etc.

But now my father and friend need their own websites with their own domain names.

How is this possible with only one IP?

My only guess would be to have the websites be on different ports (other than 80). Though I can't get my domain name registrar (GoDaddy) to allow my domains to point towards ports other than 80.

Thank you so much!

---

### Post by Bachstelze on 2007-05-22
VirtualHosts in Apache ?

I don't know much about it myself but it's most likely what you want.

---

### Post by Xarok on 2007-05-22
> **HymnToLife said:**
> VirtualHosts in Apache ?

I don't know much about it myself but it's most likely what you want.

The problem isn't the server, it's that fact that I only have one IP

How can I get my router to direct different domain names to different servers (or virtual servers)

Although I use Linux, I have to admit that this in not a Linux question. (I just like this community)

---

### Post by Bachstelze on 2007-05-22
You can very well have more than one domain name for the same IP...

---

### Post by Xarok on 2007-05-22
> **HymnToLife said:**
> You can very well have more than one domain name for the same IP...

And have them go to different servers through the same IP?

---

### Post by Bachstelze on 2007-05-22
DIfferent physical servers ? I guess it must be possible if you setup a DNS server so you can access them with host.domain.org but don't take my word for it. Don't know about different domains, though...

---

### Post by wormser on 2007-05-22
> **Xarok said:**
> And have them go to different servers through the same IP?

Web host companies do this set up as default.  

> Configure it directly by way of the configuration file /etc/apache2/ sites-available/filename(by default we have default name file take this as reference and create new file). To activate name-based virtual hosts, specify a suitable directive. NameVirtualHost *. * is sufficient to prompt Apache to accept all incoming requests. Subsequently, configure the individual hosts:

The full document is [here]("http://www.debianadmin.com/creating-name-based-and-ip-based-virtual-hosts-in-apache.html").

---

### Post by mnewbegin on 2007-05-23
right now im trying to get away from my apache setup in windows but this works

i have apache running and i have a single dsl line with a static ip, i currently have 6 websites on that 1 IP address, and there setup like this.



This is how I do it.

it might be in your httpd.conf, or it might be in the extra folder  and its vhosts

the actual file is

httpd-vhosts.conf  "this  block might be in your   httpd.conf file directly. if not look in the  extra folder"

on my system and inside i have something like this.


#
# Use name-based virtual hosting.
#

NameVirtualHost *:80

<VirtualHost *:80> 
ServerName [www.website1.com](www.website1.com) 
ServerAlias website1.com 
DocumentRoot "C:\xampp\xampp\htdocs\website1" 
ServerAdmin [email]webmaster@website1.com[/email] 
</VirtualHost> 

<VirtualHost *:80> 
ServerName [www.website2.com](www.website2.com) 
ServerAlias website2.com 
DocumentRoot "C:\xampp\xampp\htdocs\website2"  
ServerAdmin [email]webmaster@website2.com[/email] 
</VirtualHost>


<VirtualHost *:80> 
ServerName [www.website3.com](www.website3.com) 
ServerAlias website3.com 
DocumentRoot "C:\xampp\xampp\htdocs\website3"  
ServerAdmin [email]webmaster@website3.com[/email] 
</VirtualHost>

and for my dns I use everydns.net

its free.


Hope I helped someone

Mark Newbegin

---

### Post by southernman on 2007-05-23
> this block might be in your httpd.conf file directly

You would be correct.

---

