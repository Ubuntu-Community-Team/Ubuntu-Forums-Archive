---
title: "Mythweb won't display in Internet Explorer"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2007-04-22
Just reinstalled to 7.04 and got mythtv up and running again, but I am having a strange problem with mythweb in that I can browse to it with Firefox, but not Internet Explorer.


When I try with IE I get the following error:

  Internet Explorer cannot display the webpage 
   
   Most likely causes:
You are not connected to the Internet. 
The website is encountering problems. 
There might be a typing error in the address. 
 
   What you can try: 
     Diagnose Connection Problems  
 
     More information 
 

But, as I said, if I use Firefox it works a treat. 


This would not normally cause me a problem, but my works computers use IE and not Firefox so I will not be able to schedule anything while away from home. Somewhat the whole point of mythweb.



Any help would be greatly appreciated.

---

### Post by Scorpuk on 2007-04-22
I am not certain, but I think it has something to do with Apache and Internet Explorer 7 incompatabilities?


I am running : Apache/2.2.3 (Ubuntu) PHP/5.2.1

---

### Post by vonfluffy on 2007-04-28
I also have the exact same problem.. its driving me nuts.

upgraded from myth 0.19 and ubuntu 5.05 by dist-upgrading a couple of times.. now mythtv doesnt work in IE.. and even worse is the things i schedule in mozilla using mythweb dont start recording.. they look fine, but fail as soon as the recordings are suppposed to start.

---

### Post by jboehm on 2007-05-01
Another mythweb feisty problem:

With MythWeb running on Ubuntu Edgy when my mouse hovered over a Upcoming Recording schedual it used to show extra program info in a dynamic window.  (Its not a pop up but I don&#8217;t know what to call it.)  However, after upgrading to Ubuntu Feisty this is gone.  This under firefox.  IE is broken for me too.

---

### Post by Sloebervos on 2007-05-06
Hi,

I had the same problem after upgrading my server from Edgy to Feisty. I just found the solution on the mythtv wiki:

Edit the /var/www/mythweb/.htaccess file and comment out these 3 lines:

        php_value zlib.output_handler           Off
        php_value zlib.output_compression       16384
        php_value zlib.output_compression_level 4

Restart apache and it should work (tested with IE 7).

---

