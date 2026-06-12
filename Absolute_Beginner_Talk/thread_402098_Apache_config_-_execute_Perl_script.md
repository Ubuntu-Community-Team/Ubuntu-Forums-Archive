---
title: "Apache config - execute Perl script"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Winterdream on 2007-04-05
I'm trying to set up a LAMP (without the "M" right now) to work on Perl scripts.  I've got Apache serving a simple HTML page at localhost but when I try to execute a Perl script, it wants to open it instead of running it.

I edited the /etc/apache2/sites-available/default, in this section only:
> 	<Directory /var/www/>
		#In Options I added Includes and ExecCGI
		Options Includes ExecCGI Indexes FollowSymLinks MultiViews
		#I added AddHandler
		AddHandler cgi-script .pl
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
	</Directory>

I tried putting the Perl script in a folder "cgi-bin" in this location:
/var/www/cgi-bin/
and I also tried putting a Perl script in 
/var/www/

But it only tries to open the Perl script....  :confused: 

Please, can someone tell me where I've gone wrong??
Many thanks for any insight.

---

### Post by WorldTripping on 2007-04-05
Err, silly question, but do you have the shebang in your first line of perlscript ??

#!/usr/bin/perl

?

---

### Post by WorldTripping on 2007-04-05
Actually, this would make it a little more portable.

#!/usr/bin/env perl

---

### Post by Winterdream on 2007-04-05
> **WorldTripping said:**
> Err, silly question, but do you have the shebang in your first line of perlscript ??

#!/usr/bin/perl

?

Yes, I have the shebang as above.  I tried changing it to:
#!usr/bin/env perl
It still doesn't work.

Not a silly question at all, I've been known to miss the obvious!  ;) 
Thanks for trying, do you have any other ideas for me?

---

### Post by WorldTripping on 2007-04-05
Er, I'm kinda new to linux, and someone else could correct me on this, but I think you might have to make the file exectuable.

Something like:

chmod +x scriptname.pl

---

### Post by WorldTripping on 2007-04-05
Last thing I'd say is to look at the apache logs, they are normally quite good at helping you out.

Apart from that, I'm fresh out of ideas I'm afraid.

---

### Post by Winterdream on 2007-04-05
> **WorldTripping said:**
> Er, I'm kinda new to linux, and someone else could correct me on this, but I think you might have to make the file exectuable.


I tried both 700 and 755 (different servers that I've used have required different permissions and I don't understand why, so I thought I'd just try both).  I didn't use CHMOD, I navigated to the script, right-clicked, chose "properties" and then the "permissions" tab.

It does seem like I must be overlooking something obvious, doesn't it?  :confused: 

Thanks again, if you have any other ideas, I'm willing to try them!

---

### Post by Winterdream on 2007-04-05
> **WorldTripping said:**
> Last thing I'd say is to look at the apache logs, they are normally quite good at helping you out.

I **forgot** about the logs !!!  Completely !!

Looking in the error log, I see that I'm looking in the wrong place - I put the script in /var/www/cgi-bin/ and when I enter the URL localhost/cgi-bin/ - it's going to usr/bin/cgi-bin/

I am an idiot.

Thank you, I will try again !

---

### Post by bporter4339 on 2007-05-06
Thank you very much for this thread. I am new to ubuntu and cgi. This thread helped me understand and solve what I think would be a common startup issue. I believe many can benefit from these and other forums.

---

### Post by bitumen on 2007-08-21
yahooooooo!

after 6 hours trying different configurations, including installing lamp 2 times , loads of goggling "lamp- how to's" 

someone finally mentions perl not install or configured 

After following this how to --
and 10 minutes to learn that i couldn't navigate with the web browser to the cgi-bin and click the test script. 

also to note
(no spaces between hash and beginning of file) will also cause a script to download too the browser    
 #!/usr/bin/perl
^

but that URL linking to it  works perfect!!!!! thanks 

also to note

Excellent how to

---

