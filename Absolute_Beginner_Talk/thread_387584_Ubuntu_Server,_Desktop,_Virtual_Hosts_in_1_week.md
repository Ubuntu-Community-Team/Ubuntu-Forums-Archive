---
title: "Ubuntu Server, Desktop, Virtual Hosts in 1 week"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by perspectoff on 2007-03-18
Ok, here's a testimonial. I started using Debian a few months ago routinely. Then I switched to Ubuntu last week.

In one week I installed a LAMP server on Ubuntu LTS Dapper Drake on a dual-booting Ubuntu/Windows XP computer. I added a Desktop, set up DynDNS for my router's dynamic IP address so I could have a URL on the web, set up a web page and published it with Apache2, and even set up virtual hosts (i.e. 5 different web sites).

My LAN communicates and shares data between Ubuntu and Windows boxes using Samba, and my favorite drives are mounted. I listen to Shoutcast Internet Radio using XMMS, use Rhythmbox just like iTunes, and have a cool screensaver showing all my pictures.

This week I am going to finish setting up my home surveillance system using ZoneMinder.

Remember, I am new to Ubuntu (and dabbled in Debian Linux for the first time only a few months before trying Ubuntu).

You can do it, too!

I have written down my steps, which is for "absolute beginners" at [http://www.geocities.com/perspectiveoffice](http://www.geocities.com/perspectiveoffice)

Have a look!

---

### Post by h0ax on 2007-03-18
Why are you hosting your site on geocities if you set up a LAMP in your home? :P

just joking here - great link - glad you were successful!

---

### Post by rsanders on 2007-03-18
thanks for the great info! I am sure this will help someone =) Glad to see how easy ubuntu is for people.

Its amazing how many people come here and switch and/or say how easy it is. Welcome to the family! =)

---

### Post by browneye253 on 2007-03-21
I've followed your steps and would first like to say thank you for taking the time to publish it.

I'm having a problem with the virtual hosts part.  When I restart apache I get a failed message.

*****
Syntax error on line 4 of /etc/apache2/sites-enabled/myfile.conf
ServerAlias only used in <VirtualHost>
*****

Any idea what I'm doing wrong?

My .conf is identical to yours with the exception of me substituting my info

---

### Post by browneye253 on 2007-03-21
I was able to solve my own problem.  In your tutorial you have the following listed for your vhosts file.
-----------------------------------------------------------

ServerName foobar1.dyndns.org
ServerAdmin fido@localhost
#We want to be able to access the web site using foobar1.dyndns.org or [www.foobar1.dyndns.org](www.foobar1.dyndns.org)
ServerAlias foobar1.dyndns.org [www.foobar1.dyndns.org](www.foobar1.dyndns.org)
#
DocumentRoot /var/www/foobar1

#if using awstats
#ScriptAlias /awstats/ /usr/lib/cgi-bin/

#we want specific log file for this server
CustomLog /var/log/apache2/foobar1-access.log combined

-------------------------------------------------------------

And you need to have the following wrapped around the code.

<VirtualHost *:80>

Your Stuff Here

</VirtualHost>

Excellent stuff though... finally got me going in the right direction!

---

### Post by perspectoff on 2007-03-29
Actually, it is running and available at

 [http://perspectiveoffice.dyndns.org](http://perspectiveoffice.dyndns.org)

but that web site is directed at another purpose (which is electronic health records). Feel free to check it out, though! 

Besides, initially  I turned off my server at night, so I put a version on geocities. 

It is available 24/7 now, though. Cheers!


> **h0ax said:**
> Why are you hosting your site on geocities if you set up a LAMP in your home? :P

just joking here - great link - glad you were successful!

---

### Post by perspectoff on 2007-03-29
Ha ha. Well, I have to learn a little about HTML. I indeed have the lines listed on my instructions, but, of course, I wrote them down as is. When you view the page the browser interprets <virtualhost *:80>  and </virtualhost> as HTML code so the browser does not display it.  Now I realize I have to use

&lt; for the <
&gt; for the >
 
or &lt;virtualhost *:80&gt;  and  &lt;/virtualhost&gt;  instead of  <virtualhost *:80> and </virtualhost>

Thanks for the feedback!

> **browneye253 said:**
> I was able to solve my own problem.  In your tutorial you have the following listed for your vhosts file.
-----------------------------------------------------------

ServerName foobar1.dyndns.org
ServerAdmin fido@localhost
#We want to be able to access the web site using foobar1.dyndns.org or [www.foobar1.dyndns.org](www.foobar1.dyndns.org)
ServerAlias foobar1.dyndns.org [www.foobar1.dyndns.org](www.foobar1.dyndns.org)
#
DocumentRoot /var/www/foobar1

#if using awstats
#ScriptAlias /awstats/ /usr/lib/cgi-bin/

#we want specific log file for this server
CustomLog /var/log/apache2/foobar1-access.log combined

-------------------------------------------------------------

And you need to have the following wrapped around the code.

<VirtualHost *:80>

Your Stuff Here

</VirtualHost>

Excellent stuff though... finally got me going in the right direction!

---

### Post by papum on 2007-04-21
IBold
	
Italic
	
Underline
		
Align Left
	
Align Center
	
Align Right
		
Ordered List
	
Unordered List
	
Decrease Indent
	
Increase Indent
		
Insert Link
	
Remove Link
	
Insert Email Link
	
Insert Image
		
Wrap [QUOTE] tags around selected text
		
Wrap [CODE] tags around selected text
	
Wrap [HTML] tags around selected text
	
Wrap [PHP] tags around selected text

---

