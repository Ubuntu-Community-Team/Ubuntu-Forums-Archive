---
title: "Hosting own website"
date: 2013-05-02
forum: Any Other OS
---

### Post by AudioFlux on 2013-05-02
Hi. I recently got debian. I am trying to host a website using a free Dynamic DNS service called DNS Dynamic ([http://www.dnsdynamic.org/](http://www.dnsdynamic.org/)). I referred to online guides for setting up apache. I followed all the steps, but for some reason I cannot access the site from an external network (non-local). First, I try to access it from the computer that hosts it; I see the site when I type "localhost" in the address bar. When I type the url of the website, I get the router login page. Then I try to access the site from a computer on the local network. I get the router login page when I type the url of the website and I get the site page when I type in the local ip address. I don't know whether I have to configure my router or some other thing on my computer (or both).

Here is what I put in file in the sites-available folder:

<VirtualHost *:80>
     ServerAdmin [email]webmaster@flamewars.dnsdynamic.com[/email]
     ServerName flamewars.dnsdynamic.com
     ServerAlias [www.flamewars.dnsdynamic.com](www.flamewars.dnsdynamic.com)
     DocumentRoot /var/www/flamewars/
     ErrorLog /srv/logs/error.log
     CustomLog /srv/logs/access.log combined
</VirtualHost>

Thanks :)

---

### Post by Lars Noodén on 2013-05-02
You have to configure your router to forward ports 80 (http) and 443 (https) to your web server.  The exact method varies from model to model and brand to brand.  However, there should be a menu for that somewhere in your router's admin pages.

---

### Post by AudioFlux on 2013-05-02
> **Lars Noodén said:**
> You have to configure your router to forward ports 80 (http) and 443 (https) to your web server.  The exact method varies from model to model and brand to brand.  However, there should be a menu for that somewhere in your router's admin pages.

Thank you so much! It worked like a charm!
:)

---

