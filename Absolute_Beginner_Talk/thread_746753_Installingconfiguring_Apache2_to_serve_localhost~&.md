---
title: "Installing/configuring Apache2 to serve localhost/~&lt;username&gt;/ sites"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by xpista on 2008-04-05
Hello,

  I'd like to install apache server with the following configuration:
  [LIST=1]
[*]It will serve the pages from the ~/Sites/ directory (as on mac default web sharing option)
[*]It will be accessible only from the local machine, not from outside
[/LIST]
  
  What is the minimal set of packages I need to install and how to configure it for this purpose?
  Is there any GUI apache configurator available to perform such a basic configs?

Thanks, Stefan

---

### Post by shawnjones on 2008-04-06
You may want to take a look at [[COLOR="Blue"]XAMPP[/COLOR]]("http://www.apachefriends.org/en/xampp.html"), this is a local Apache, PHP, MySQL setup that can be used for web development, very easy to install and customize, hope this helps.

Shawn

---

### Post by apostate on 2008-04-06
You could use chroot, which is how a lot of professional web-hosting outfits create multiple fake web-roots on one server.  Or if you are careful about securing things with proper permissions, you could sym-link the homes of your users into your webroot. So, you install apache2 and it sets you up a web server in /var/www. Create the sites folder yourself. Say you have 3 users who are going to be using this box for websites, which I think is like the scenario you are proposing.  

bob

bill

jim

So you do: ln -s /home/bob/   /var/www/sites/bob/

Anything Bob puts in home becomes accessible on the web via [http://domain.com/sites/bob](http://domain.com/sites/bob)  or localhost/sites/bob

Does that help?

---

### Post by xpista on 2008-04-08
I found what I was looking for.
The mod I need is mod_userdir: [http://httpd.apache.org/docs/2.0/mod/mod_userdir.html](http://httpd.apache.org/docs/2.0/mod/mod_userdir.html)

---

