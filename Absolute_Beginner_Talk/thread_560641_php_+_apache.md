---
title: "php + apache ?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-09-26
Let me first say that I'm running Feisty & just started experimenting with PHP into my website.
I currently use Screem & save the file then download it to my webhost (1&1.com), then go to my site to test it out. Especially for a beginner this is very cumbersome so now I want to test my php scripts on my computer without getting online which I assume can be done in Feisty.   
I used the folowing code to install the packages I think I need:

sudo apt-get install apache2 libapache2-mod-php5 php5-mysql mysql-server

sudo apt-get install gcc 

I know this is going to sound stupid but now that everything is installed I have no idea how to even get started. I was hoping the installation would put something on my desktop. What I need is probably an outline of what steps I need to learn or a site written with the assumption that the user knows absolutely nothing to begin with.

---

### Post by CaptainInsaneO on 2007-09-26
You should be able to find what you need in System>Administration>Services

After that, you should be able to type in your IP address of your Ubuntu machine and access your php and html pages. Go to [Apache]("http://www.apache.org") for more info.

---

### Post by garyed on 2007-09-26
> **CaptainInsaneO said:**
> You should be able to find what you need in System>Administration>Services

After that, you should be able to type in your IP address of your Ubuntu machine and access your php and html pages. Go to [Apache]("http://www.apache.org") for more info.

Thanks for the reply but when I said beginner I wasn't kidding.
1 - Where do I type in my IP address?
2 -What or how do I find the IP address to type in ?
I went to Admin>Services> & found  Apache2 + Myqsl databses active.

---

### Post by CaptainInsaneO on 2007-09-26
lol, my fault. You can find your IP address by typing```
ifconfig
``` and finding eth0 in the results.

You type that address into your browser's address bar (i.e. where you would normally type something like [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)).

Once you do that, the default page for Apache will appear. The directory it's talking about when it says this> You may now add content to this directory and replace this page.

is /var/www

Hope this is a little more clear than my last post, if you need any more help just ask! :)

---

### Post by garyed on 2007-09-27
> **CaptainInsaneO said:**
> lol, my fault. You can find your IP address by typing```
ifconfig
``` and finding eth0 in the results.

You type that address into your browser's address bar (i.e. where you would normally type something like [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)).

Once you do that, the default page for Apache will appear. The directory it's talking about when it says this

is /var/www

Hope this is a little more clear than my last post, if you need any more help just ask! :)

Thanks,
It worked like a charm.
When I click on the Apache2 directory it says "IT WORKS"
I've got my stuff loaded into  /var/www/  & my directories show along with Apache2 on the page when I put in my ip address but I haven't got my pages to work right yet.
I'm slowly getting the hang of it.

---

