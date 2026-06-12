---
title: "Perl Script in Apache"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-04-15
I have reinstalled Apache on Dapper, and came across a problem with putting a Perl script (a counter, more specifically) on my page.  This is the Perl script, labeled "counter.pl":
```
#!/usr/local/bin/perl
	use warnings;
	use strict;
	use CGI qw/:standard/;
	
	my $file="counter.txt";
	
	open( LOG, "$file" ) or die "Cannot open file $!";
	my $cnt = <LOG>;
	close(LOG);
	
	++$cnt;
	
	open( LOG, "> $file" );
	print LOG $cnt;
	close(LOG);
	
	print "$cnt";
```
Now here is what I put in my index HTML file (while I am testing this, I was trying to successfully load a page with **only** a counter):
```
<html>
<body>
<!--#include file="counter.pl" -->
</body>
</html>
```
Now, I labeled this "index.html" and put it in the /var/www/ folder along with "counter.pl."  From here, I accessed my page from the web but the counter didn't show up.  Where did I go wrong here?  Thanks very much, I appreciate the help :) .

---

### Post by Ensnared on 2006-04-15
You probably need to name the file index.shtml since this is using server-side includes (SSI). The server needs to know it should parse the file rather than simply give it to the client, and to tell it that, it needs to be named .shtml instead.
I suppose you can instruct the webserver to also parse files named only with .html but that means it will parse all such files, which isn't a very good thing from a performance point of view ;)

It's also possible you need to edit the main Apache configuration-file to enable server-side includes - it's been ages since I used this so I'm not quite sure if it's enabled by default or not in Ubuntu.

If memory serves, the configuration file is /etc/apache2/httpd.conf.

Oh, and you may also need to edit the first line of the perl-script as well, as it currently points to "/usr/local/bin/perl", but the correct location is "/usr/bin/perl".

---

### Post by amcavoy on 2006-04-16
Thanks for the reply.  I renamed index.html to index.shtml and changed the path in the perl script.  It still doesn't work, but I can try to fool around with it some more.  Has anyone else tried this?

---

### Post by amcavoy on 2006-04-17
Also, is this really supposed to be in the /var/www/ folder?  I was trying to find a cgi-bin folder, but there doesn't seem to be one.  By the way, the only thing I installed was Apache:
```
sudo apt-get apache2
```

---

