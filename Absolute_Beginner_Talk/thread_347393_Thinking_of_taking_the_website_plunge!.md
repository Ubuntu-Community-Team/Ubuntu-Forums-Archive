---
title: "Thinking of taking the website plunge!"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-01-27
Hi I'm looking at creating a website but don't know exactly where to start, would there be a site somewhere for Linux users that explains this process from step one? (i.e. which applications are needed etc..).Thanks for any help anyone could give me :)

---

### Post by matthew on 2007-01-27
I have a personal website as well as a business website. The basic steps in creating a site are outlined below from something I wrote a while back for family wanting to know how I made the personal one...the steps may need to be modified to suit your specific needs.


 Creating any website begins with the choice of a host for the site.
 There are several places that will host a small, non-commercial site for free. For example, you can host pictures at [Flickr]("http://flickr.com/"), make a blog at [Blogger]("http://blogger.com/"), or create a webpage at [Yahoo's Geocities]("http://geocities.com/") without having to pay anything to anyone. Some of these free sites will put ads on your page, some won't. All of them have very specific limitations as to what you may and may not post, how much traffic you can receive over a period of time (how many people can view your site/photos/etc.), and how much storage space you have for your content. For most people they are very adequate and useful. I wanted to do more.


 I started searching for a web hosting company. These companies sell you space on their servers (computer systems that store your files and make them available to others, aka "serve" them to people who want to see them) and have varying levels of plans that will enable you to host large amounts of data, create whatever type of site you want to create, and even run a business or resell your space to others. I chose [Site 5]("http://www.site5.com/") for three reasons; because of the recommendation of a friend in the business, because they have a great deal right now for $5 a month if you pay for 2 years in advance, and because they run all their computers using a [Linux operating system]("http://en.wikipedia.org/wiki/LINUX") running [Apache]("http://httpd.apache.org/").


 Once a host is contracted and your location is secured you then have to register a domain name. Web sites generally use names that you enter into your web browser (i.e. Firefox) to find the content you are interested in. Remembering "Google.com" is much easier than remembering the IP address for the site which consists of numbers. I registered "matthewhelmke.com" as the address for my site "66.29.108.87" so that people can find it without having to remember a list of seemingly random numbers. You generally do this through your web hosting service (as I did) or you can contact an outside "domain name registrar" of which there are several. The cost is usually in the neighborhood of $10 per year for a name to be registered.


 Once those steps are complete it is time to create your site and its content. There are lots of ways to do this. I wanted to try something new (for me) and at the same time I have a strong preference for [Open Source software]("http://www.opensource.org/docs/definition.php") so I wanted to try to make a whole website with all the functions I need/desire using only software that fits that description. I have succeeded for this site. When I get around to finishing my work on my business site I hope to be similarly successful.


 First, I installed a content managing system called [Drupal]("http://drupal.org/"). This is highly a flexible system to which you can add functionality through the use of what are called "modules." These are software extensions that other users have created to give you new abilities like forums, polls and blogs. I looked through the lists of available modules and have chosen several that added things to this site. You can also download different templates to make the site look different. I chose one and then modified it to personalize this site further. Drupal uses [PHP]("http://www.php.net/") which is a scripting language which allows for dynamic content. This means that I don't have to edit the code for the front page with each update, but that this is done quickly and automatically by the software each time someone visits. Someone makes a new blog post or comment and the updates appear as if by magic. That's just cool.
 Everything you do that requires the storage of data (like forum posts, blog entries, gallery pictures) needs to have a database. I have chosen to use [mySQL]("http://mysql.com/") for all of these on my site.


 I found a nifty little module for Drupal that enables a user to set up [Gallery]("http://gallery.menalto.com/"), a great photo posting program, as an actual part of the main website rather than as a stand-alone site like it was really designed to be. I thought that was so incredibly cool I had to try it. With a lot of reading of manuals and various web pages I was finally able to massage the two distinct pieces together and I couldn't be more pleased.


 Well, those are the basics. Essentially I did a lot of reading, some testing, and had a bit of fun hacking stuff together to make what you see in front of you. I hope you enjoy it.

---

### Post by Tomosaur on 2007-01-27
> **nite owl said:**
> Hi I'm looking at creating a website but don't know exactly where to start, would there be a site somewhere for Linux users that explains this process from step one? (i.e. which applications are needed etc..).Thanks for any help anyone could give me :)

Well that depends entirely on what you want to do :P

A website in itself is usually platform independent, if you buy hosting space from a company. Generally speaking, it doesn't matter whether you, as a user, run Linux, or Windows, or Mac, or whatever, since http (the website protocol) is recognise in any browser you're likely to use. There ARE some limitations however. Some sites require a Windows server for specific features, etc etc. It all depends on what you want to do, and what your selected hosting company is capable of.

HOWEVER - if what you're talking about is hosting a website from your own computer, you will need to download server software. One configuration is called 'LAMP', which is an acronym for 'Linux, Apache, MySQL, PHP'. You cannot download 'LAMP', since it's not software, just a name referring to a configuration of software. You are not required to use the software listed, but it's just a popular way of going about it. Since you already have Linux, you just need to download server software - probably Apache, since it's certainly the most popular with Linux users. If you require databases and PHP support, then you can look into those too. The [Apache website](http://www.apache.org/) has documentation on how to set up and configure the apache http server.

If, on the other hand, you're asking about web development software, then there are tons of options available to you. You only REALLY need a text editor, if you already know HTML, CSS, or other web-oriented languages. Web-development software generally just facilitates your design, and helps your to organise your various files and images and whatnot. If your site is hosted with a company, you will also need FTP software to upload your files to the server. There are tons of these available too. If it is development software you're after, just open Synaptic and do a search - there are far too many available to go into specifics.

---

### Post by PurplePenguin on 2007-01-27
> **matthew said:**
> they have a great deal right now for $5 a month if you pay for 2 years in advance
...
 You generally do this through your web hosting service (as I did) or you can contact an outside "domain name registrar" of which there are several. The cost is usually in the neighborhood of $10 per year for a name to be registered.

Disclaimer:  I'm really cheap. :)  Keep that in mind as you read!  And this is just referring to personal websites, as business-related websites should always be on high-end hosts.

$5 a month (and even $10 for a domain name) can be excessive for the average joe who just wants a personal website up, especially if he's got to commit to two years.  

There are tons of hosts out there that charge far less, although you can't be quite as sure of the host's stability.

I've got a website up on tooniehosting.ca right now, and it seems just as good on my end as the hosting I used to get on wirenine (very reputable company, solid customer service, but $6.99 a month) - the main difference is that it costs only $1 a month.  A buck a month is a low price to pay to avoid ads like they have on free hosts.

If you're paying $10 for a domain name, you should really do what everybody else is doing - use Godaddy and put a couple coupon codes in (they're all over the place... check google) and you'll get a name for half of what you're paying.  This adds up if you've got a few different sites.

If you're really adventurous and you want to save even more, you could always set up your own LAMP server.  It's fun, and you learn a heck of a lot in a very short period of time. :D  You can also get DYNDNS going and choose one of their subdomains for free.

---

### Post by matthew on 2007-01-27
> **PurplePenguin said:**
> $5 a month (and even $10 for a domain name) can be excessive for the average joe who just wants a personal website up, especially if he's got to commit to two years.  

There are tons of hosts out there that charge far less, although you can't be quite as sure of the host's stability.

If you're paying $10 for a domain name, you should really do what everybody else is doing - use Godaddy and put a couple coupon codes in (they're all over the place... check google) and you'll get a name for half of what you're paying.  This adds up if you've got a few different sites.Yeah. You're right on all these counts. I was trying to keep it simple and sometimes you pay more for convenience. :) Part of it also depends on the purpose behind the site: business or pleasure?

Thanks for adding some good thoughts to consider.

---

### Post by PurplePenguin on 2007-01-27
> **nite owl said:**
> Hi I'm looking at creating a website but don't know exactly where to start, would there be a site somewhere for Linux users that explains this process from step one? (i.e. which applications are needed etc..).Thanks for any help anyone could give me :)

Everybody's going to make fun of me because I'm *sooo Web 1.0*, but I recommend installing the nVu HTML editor.  It allows you to graphically lay out your website and it should display almost exactly the same in a web browser as it is in the editor (WYSIWYG = What you see is what you get).  Basically, if you can create a Word / OpenOffice document with colour and add in some pictures, you can create a website.

Keep in mind, this is to make a simple website - show a few pictures, tell about yourself, put an email link in, whatever.  If you want something more complex, there are content systems available - drupal was already mentioned.  I'm one of the few remaining hard-core old-skoolers that tries to avoid blogs and flashy web 2.0 stuff, so I stick with my HTML. :D

From there, you'll just need an ftp program (I use gFTP in gnome) to upload your index.html and any pictures you've included onto your website (you'll need to pay for hosting or use an ad-driven free host, see other posts in this thread).  That's about all you need to do to get the website up and running. 

To get your domain name (lets say, [www.niteowliscool.com](www.niteowliscool.com)) pointing to your website content, you'll just need to go into godaddy (or wherever you paid for your domain name) and change the nameservers (proper nameservers for your host will be sent to you by email when you sign up).  It might take a day or so, but then when you type in [www.niteowliscool.com](www.niteowliscool.com), it'll take you to your website.

That's about it, unless I forgot something. :)

---

### Post by PurplePenguin on 2007-01-27
> **matthew said:**
> Yeah. You're right on all these counts. I was trying to keep it simple and sometimes you pay more for convenience. :) 

When you're as cheap as I am, you'll search for any way you can to save a buck. :D

---

### Post by proxima estacion on 2007-01-27
You could always get a free Geocities account check out this link maybe:
[http://www.google.com/Top/Kids_and_Teens/Computers/Web_Page_Design/Free_Web_Space_Providers/]("http://www.google.com/Top/Kids_and_Teens/Computers/Web_Page_Design/Free_Web_Space_Providers/")

See how you get on with that i.e if you actually use it then maybe and like it think about splashing out a couple bucks on a hosted one with more options and services.

---

### Post by proxima estacion on 2007-01-27
actually having re-read your thread i wouldn't bother with my suggestion its a bit basic and probably wont really teach you much.

---

### Post by nite owl on 2007-01-27
Wow thankyou so much everyone for your inputs, I'm sorry I couldn't respond earlier. Would there be any advantages to creating your own server(I read about something called LAMP above?) instead of paying some third party to host it for you?(other then the saving of money of course ;) )

---

### Post by Threbus5 on 2007-01-27
Hi,

Absolutely!  Advantages to making your own server include learning enough to configure it, learning the requirements and building the essential backups, learning and obtaining desired appendages (for example mail server, database server, security issues, and web server, and on into the wonderful world of networking.) An issue is allocating sufficient time and interest to research the resources to accomplish your dream.  The Really Big advantages are education, ownership and pride that you built it! 

However, you may not save too much money by hosting it yourself. If you want a domain name it costs the same as a hosted domain name (maybe a little more - depends on the deal.) Plus you need to leave your site running (24 hours 7 days a week right? that takes some electricity) and $2.00 a month for a hosted site is not too bad.

I agree that purpose should direct the effort.

Take care.

---

### Post by PurplePenguin on 2007-01-28
> **nite owl said:**
> Wow thankyou so much everyone for your inputs, I'm sorry I couldn't respond earlier. Would there be any advantages to creating your own server(I read about something called LAMP above?) instead of paying some third party to host it for you?(other then the saving of money of course ;) )

Threbus5 summed everything up quite well in the above post, but I'd just like to add a bit about my own experiences with this.

If you're interested in just getting a site up quickly and easily, go with hosting.  That way, you'll just skip to the part where you ftp your content to a website and you're off.  If you're the kind of guy that's got a couple of days to put into it and wants to learn a LOT in that period, I'd give a server a shot.  The worst thing that'll happen is you'll think it's too much work and you'll fall back on plan A. :)  I believe that I learned more in the 24 hour period when I got my server up than in any single week of my life.  :D

LAMP stands for Linux, Apache, MySQL and PHP.  If you download the Ubuntu Server disc and have an old computer hanging around (I was recently given a 500mHz computer for free, so I clocked it down to 300mHz and stuck 192MB of RAM, a network card and a small hard drive in it - I figure that makes a decent home server), you'll have a server up and running very quickly.  The Ubuntu disc makes it ridiculously easy to get up and running, and the millions of detailed HOWTOs and walkthrus on this forum and elsewhere make the rest of it a snap, too.

By the way, I'm the kind of guy that's always looking for little projects to do - I used an old computer to make a router, but I've got a store bought router that works perfectly well, so I never used the one I built.  I did learn while doing this, though, which is the important thing.

I am interested in computer and network security, so the first thing I did was search out some information on locking the server down and making it as secure as possible.  There are great howtos out there, you'll find them after about 5 seconds of googling. :)  Or come back here, there's info everywhere.

The way I've got it set up, my server isn't taking up much space at all.  There's no monitor or keyboard attached.  It just sits on the corner of a desk and hums along all day.  If I need to do something, I can 'ssh' into it or use webmin from a different computer.  Webmin, by the way, is INCREDIBLE.  It's a web-based frontend, I guess you could say, to pretty much anything you'd want to do on the other computer.  Basically, if you want to go into the Apache configuration, you can either use a terminal and 'ssh', find the config file and 'nano' it (nano being the easiest to use terminal-based text editor), or use a web browser to make the changes through webmin.  I doubt you'd even need to play around with any config files if you use webmin all the time.  Maybe there's an exception or two (like ddclient.conf, for dyndns, I forget if that's part of webmin).

There are howtos out there that will let you clamp down on security with "ssh" - you can choose to use encrypted keys instead of passwords, for example.

Once you've got a simple index.html in your /var/www/ directory (or subdirectory if you want to have a number of sites), you'll probably want to check out dyndns.org.  I've got a dsl router, so my ip address gets changed often (I don't know... every day? week? few hours? I've never paid that much attention).  Since it changes, I use dyndns to assign my sites a domain name (whateveryou'dlike.dyndns.org, or choose from a list of other domains).  You actually choose a subdomain that sticks on the front of their domain, but it's not too important.  It's free if you go this way... if you want to use your very own [www.websitename.com](www.websitename.com) domain name, you've got to pay $25 or so a year.

You'll need to download and install (on the server) a program called ddclient.  It checks your ip address every so often, so when your internet service provider changes it, your websites don't get lost - it automatically updates the config with the new numbers.  There's a slight bit of configuring, but there are a lot of resources and posts on this forum to help you out.

That's about it.  You can use ftp to put new material onto your server, then 'ssh' back in and place it in the proper places so it goes live on the net.  Or if you need to make a couple small changes (broken links?) you can just 'ssh' in and use 'nano'.

It's actually quite easy.  I put a full day into getting mine up and running, but I think it was the best decision I've made since I decided to completely remove my windows partition. :D

---

