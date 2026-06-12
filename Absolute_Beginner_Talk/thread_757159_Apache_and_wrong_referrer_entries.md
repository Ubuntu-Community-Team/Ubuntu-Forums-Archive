---
title: "Apache and wrong referrer entries"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by davidlynch on 2008-04-16
Hi,

Firstly, I'm new to Apache + php world

Having said so, let me show you my problem:

I'm trying to get the REFERRER WEBSITES that visits my site.
Most of my files are written in plain html, so I'm unable to code server side instructions. 

So I put this simple javascript code:

> <script type="text/javascript">
var url = "js/getreferrer.php";
var ref = document.referrer;
document.write('<script src="', url +'?ref='+ ref, '" type="text/JavaScript"><\/script>');
</script>

the getreferrer.php file just get the origin url and save it to a textfile:

> <?php
$myFile = "listofreferrers.txt";
$fh = fopen($myFile, 'a') or die("can't open file");
$referrer = $_GET['ref'];
$stringData = "$referrer\n";
fwrite($fh, $stringData);
fclose($fh);
?>

The result is that EVERY referrer url entry is replaced with the full URL of the page that uses de javascript code,

In english - if I visit my page called "http://site/file1.htm" from a search result on search engine "http://searchengine", my referrer recorded is "http://site/file1.htm" instead of "http://searchengine".

When I use PHP this problem doesn't arise, but I'm unable to use any other format than "html" file

Any help will be highly appreciatted

David

---

### Post by Oldsoldier2003 on 2008-04-16
> **davidlynch said:**
> Hi,

Firstly, I'm new to Apache + php world

Having said so, let me show you my problem:

I'm trying to get the REFERRER WEBSITES that visits my site.
Most of my files are written in plain html, so I'm unable to code server side instructions. 

So I put this simple javascript code:



the getreferrer.php file just get the origin url and save it to a textfile:



The result is that EVERY referrer url entry is replaced with the full URL of the page that uses de javascript code,

In english - if I visit my page called "http://site/file1.htm" from a search result on search engine "http://searchengine", my referrer recorded is "http://site/file1.htm" instead of "http://searchengine".

When I use PHP this problem doesn't arise, but I'm unable to use any other format than "html" file

Any help will be highly appreciatted

David

you can make you .html pages parseable one of two ways dpeneding on your level of access.

you can add ```
AddType application/x-httpd-php .html 
``` to your .htaccess file

or you can edit httpd.conf

[http://www.zann-marketing.com/developer/20050718/parsing-php-on-html-pages.html](http://www.zann-marketing.com/developer/20050718/parsing-php-on-html-pages.html)

---

### Post by davidlynch on 2008-04-16
Txs oldsolider! I'll try your tips and see what happens, txs for your time
David

---

### Post by davidlynch on 2008-04-16
It worked!
Thanks a LOT for your time and advise, you really helped me
:):):)
David

---

