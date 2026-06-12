---
title: "Wordpress Server"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by agaramond on 2007-03-28
I am a beginner... I have installed WP on an Ubuntu/LAMP server. I followed the directions at [http://www.supriyadisw.net/2006/12/wordpress-installation-on-ubuntu-with-lamp](http://www.supriyadisw.net/2006/12/wordpress-installation-on-ubuntu-with-lamp) . 

On my local server, I can view all of my WP pages. However, when I visit my blog from my window machine at work, I can get to the first page, but it does not have the formatting like on my local server. Also, if I try to click on any links from my work PC, I am taken to [http://localhost/wordpress/](http://localhost/wordpress/) which is a "Internet Explorer cannot display the webpage" page. 

My Document Root is /var/www/wordpress on my virtual server. I have given permission when I set up my virtual server. I also have apache, phpmyadmin and webalizer in the /var/www/ directory.

I now need to know how to set up the file structure and permissions for optimal operation and security. Your help is greatly aprreciated. Speak slowly as I am a beginner:-)

---

### Post by wscheer on 2007-03-28
agarmond,
Can you give us some more information about your setup?

I have an ubuntu/wordpress testing server at home but I can only access it at home. 

Is your "work pc" a pc that you take home from work, or is your "work pc" physically at a remote location?

From the ubuntu machine i access it by "http://localhost/wordpress" and from my windows laptop (or any other machine for that matter) i type in "http://192.168.1.205/wordpress". 192.168.1.205 being the local ip of the Ubuntu box.

also in Wordpress if you go under "options" you should see "WordPress address (URL):" and "Blog address (URL):" You'll want to make sure those are correct, they could be effecting your links.

I'm not at home right now to check the see how I have it setup but you can wait till 5:30 easter time, I can repost.

Hope that helps a little.

---

### Post by agaramond on 2007-03-28
my "work pc" is a remote desktop computer at my office. Meaning, it is at a physically remote location with respect to my server.

I will check my wordpress and blog URLs.  those will be the same as my site is only a blogging site...

Let me know if you need any more info.  

Thanks for your help!!!

---

### Post by wscheer on 2007-03-28
agaramond,

When I got home and checked my testing server, I do have ip address in the URL's. (ex: 192.168.1.205/wordress)
On my live site it has my domain name (ex: myblog.com/wordpress)
It looks like the links pull that information from those URL fields. I would make sure they say something like "myblog.com/wordpress" and not localhost/wordpress

Let me know what you find out.

---

