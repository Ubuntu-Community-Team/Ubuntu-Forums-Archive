---
title: "how to set up your own web server"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-01-26
I would like to know how to set up my own web server using ubuntu on my computer. I do not want to have to deal with a web host. I would appreciate if you could go into depth about how to do it and how to ensure security. Thank you.
Please reply here on the website or email me at [email]jprb85@gmail.com[/email]

Thank you.

---

### Post by banditti on 2007-01-26
From the GUI
System/Administration/Synaptic Package Manager

Then scroll down until you see Apache2.
Highlight it then right click your mouse, then select Mark For Installation.
Then in the Synaptic Package Manager window select Apply.

After it finishes, you are done.

From CLI

sudo apt-get install apache2

---

### Post by banditti on 2007-01-26
Sorry, one more thing.  If you want lamp:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by pbaehr on 2007-01-26
Your easiest bet is to download the server install disc here:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

and do a fresh install, choosing LAMP server. This will install Apache, MySQL, and PHP with pretty minimal hassle. As far as an in-depth explanation goes, your best friend is Google. It's not that I'm not willing to give you pointers, it's just that it's such a broad topic I'd be here typing all day.

---

### Post by jkeyes0 on 2007-01-26
To host a website from your personal machine, you'll have to do several things:

1. Set up Apache (using the earlier instructions)
2. Ensure your ISP allows the operation of personal web servers. I know Adelphia used to block port 80, the most common port for web sites
3. If you have a dynamic IP address for your connection, you will have to go through a service such as [dyndns]("http://www.dyndns.com/") that will give you a static domain name to go with your dynamic IP address
4. Once you've got your "online persona" as it were (domain name, permission from the ISP, etc.), get your Apache configured, put some content up, and you should be good to go.

---

### Post by teet on 2007-01-26
> **banditti said:**
> From the GUI
System/Administration/Synaptic Package Manager

Then scroll down until you see Apache2.
Highlight it then right click your mouse, then select Mark For Installation.
Then in the Synaptic Package Manager window select Apply.

After it finishes, you are done.

From CLI

sudo apt-get install apache2

One thing to add to this...

Ubuntu "hides" your web directory in /var/www (it took me a while to find this the first time).

To make this directory writeable by nonroot user accounts pop open a terminal and type:

sudo chmod 777 /var/www

Then you can click and drag your website files over to /var/www using nautilus or konqueror.

To see your website open up firefox and type 'localhost' into the address bar (no http or anything).

-teet

---

### Post by mahalie on 2007-01-26
Here's a [guide for total Noobs]("http://www.cjfay.com/lamp.html"), setting up your server with a GUI right away.
(There's no GUI included in the ubuntu server lamp install, although you can add one)

---

### Post by thewump on 2007-01-26
Install xampp. It's dead easy and a good framework for future additions.

As far as accessibilty you'll have to redirect port 80 stuff through your firewall / router to go to the IP of this machine.. so you'll also have to setup your machine with a static IP on your network to make life easier. 

Then you'll need a domain, or give out your IP address as the website location ( yuck ).  I use dyndns.org to route stuff to my system for testing.. its pretty good and free.

---

### Post by Thirsteh on 2007-01-29
> **jprb85 said:**
> I would like to know how to set up my own web server using ubuntu on my computer. I do not want to have to deal with a web host. I would appreciate if you could go into depth about how to do it and how to ensure security. Thank you.
Please reply here on the website or email me at [email]jprb85@gmail.com[/email]

Thank you.

You might want to check out

[http://sheeped.com/2007/01/29/set-up-ubuntu-linux-lamp-server-in-minutes/](http://sheeped.com/2007/01/29/set-up-ubuntu-linux-lamp-server-in-minutes/)

:-)

---

