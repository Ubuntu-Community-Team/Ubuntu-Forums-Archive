---
title: "I am learning PHP - Do I need a PHP Editor Program?"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-21
Hello All!!!

I visited the following site for a Tutorial for PHP:

[http://gr.php.net/manual/en/tutorial.firstpage.php](http://gr.php.net/manual/en/tutorial.firstpage.php)

Right in the beginning of the Tutorial, it says to create the First Page with code:

"Example 2-1. Our first PHP script: hello.php:"

<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
 <?php echo '<p>Hello World</p>'; ?>
</body>
</html>

So, what I did is the following:

1. I opened an Open Office's Writer Program.

2. I copied & pasted the above in an empty Writer's Document.

3. I saved the above in the "html" format & on the Desktop.

4. I tried to open it with the Mozilla Firefox Internet Browser & Instead of seeing the "Hello World" I just see all the above (exactly as you see it here posted)...


Do I need a PHP Editor Program?

It never said that I need a PHP Editor Program...

IF Yes, can you suggest one (a Free one)?

What is wrong?

Thanks.

P.S. 1> I want to learn PHP5, so that I can create a Web site.
            I am also learning MySQL so that I can connect the Web site to a 
            Database.
            I have installed both of the above & also the php5-mysql.
            I have NOT yet installed the "Apache" program, because I first want to 
            learn howto, then create the Web Site & (ONLY after that) try to post it...
            Could this be the reason to my problem?

P.S.2> Can I create a Web Site with PHP?
           OR: HTML is ALSO required, to help with the creation of a Web Site?
           I would like to know, cause I might be doing it ALL wrong, right from the 
           start...
           _Note_:
           I do NOT want to learn EVERYTHING (ALL) Mixed up...
           I would prefer to avoid messing with HTML, because to get in learning mode 
           in 4 different stuff (Apache, MySQL, PHP & HTML), ALL at the SAME time, is 
           waaaaayyyy too much!!!
           Thanks.

---

### Post by rejser on 2006-03-21
you can create a website using entirely php.
try rename the file you saved from *.htm(l) to *.php

---

### Post by dvarsam on 2006-03-21
Thank you for your repply!!!

I would have done this if Open Office's Writer Program supported that format...

Since it does NOT, I probably need a different Editor...

Note:
I do NOT have the OOO version 2 - I just have the one that comes pre-installed in Ubuntu Breezy 5.10.
Does OOO version 2 support the .php format?

Thanks.

---

### Post by mlind on 2006-03-21
any editor will do, but it's easier to with program that supports syntax highlighting, like Emacs or jEdit.

---

### Post by fergus.b on 2006-03-21
For an editor if you're using Ubuntu then use Gedit. If you're using Kubuntu then try Kate. They're both pretty straightforward. 

To run your php scripts you'll need to have Apache with PHP installed. You can't just make a php file and double click it to view it. It needs to be run through a web server (Apache). Use synaptic to install apache and php. I'm not sure where Ubuntu makes the doc root (someone know?) but you'll have to save your php scripts in it and then open your browser and type in [http://localhost/yourfile.php](http://localhost/yourfile.php) to view the file properly.

---

### Post by meborc on 2006-03-21
i use gedit... kind of sidekick for notepad (but much better) ... old-school style

btw - haven't coded anything since high-school... those were the days... :rolleyes:

EDIT: check out this also: [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=php&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=php&titlesearch=Titles)

---

### Post by dvarsam on 2006-03-21
Hello Everybody & thank you for your help...

It is nice that you all suggested of your favorite Editor, but I would appreciate if you could all bare with me for a while...

A. Formats Supported by gedit Program:

1. Current Locale (UTF-8)
2. Western (ISO-8859-15)

B. Formats Supported by OOO v2.0 (specifically v1.9.129) "Writer" Program:

01. Microsoft Word 97/2000/XP (.doc)
02. OpenDocument Text (.odt)
03. OpenDocument Text Template (.ott)
04. OpenOffice.org 1.0 Text Document (.sxw)
05. OpenOffice.org 1.0 Text Document Template (.stw)
06. Microsoft Word 95 (.doc)
07. Microsoft Word 6.0 (.doc)
08. Rich Text Format (.rtf)
09. StarWriter 5.0 (.sdw)
10. StarWriter 5.0 Template (.vor)
11. StarWriter 4.0 (.sdw)
12. StarWriter 4.0 Template (.vor)
13. StarWriter 3.0 (.sdw)
14. StarWriter 3.0 Template (.vor)
15. Text (.txt)
16. Text Encoded (.txt)
17. HTML Document (OpenOffice.org Writer) (.html)
18. AportisDoc (Palm) (.pdb)
19. DocBook (.xml)
20. Microsoft Word 2003 XML (.xml)
21. Pocket Word (.psw)


NONE of the 2 Programs you suggested to me using, supports a ".php" format...

Can you please VERIFY, before you suggest something to me, that it in Fact DOES support ".php", because if I start trying ALL the software you suggested, ONE BY ONE until I get something done, in the meantime...

... I will first have to pull my hair out...

Thanks.

---

### Post by dvarsam on 2006-03-21
A. Formats Supported by gedit Program:

1. Current Locale ( UTF- 8 )
2. Western (ISO-8859-15)

Sorry for the Re-post, but I think the previous combination of "8" & ")" creates a smilie...

---

### Post by mcduck on 2006-03-21
[QUOTE=dvarsam]Hello Everybody & thank you for your help...

It is nice that you all suggested of your favorite Editor, but I would appreciate if you could all bare with me for a while...

A. Formats Supported by gedit Program:

1. Current Locale (UTF-8)
2. Western (ISO-8859-15)
[/QUOTE]
Gedit supports _any_ file that is basic text, no matter what extension the file has. And php is just text :)

---

### Post by Bagnaj97 on 2006-03-21
To view php files you need apache and php installed. This can be done using synaptic. Once you have done this copy the html/php file to /var/www or into a directory in your home folder called public_html. Once you have done this you can either open a web browser and go to ```
localhost
``` (if the files are in /var/www) or ```
localhost/~YourUsernameHere
``` (if the files are in your public_html folder). Note that the permissions have to be correct for the public_html folder to be accessible to apache.

As for a php editor try using bluefish or quanta. I havent personally used bluefish but quanta is very good for any web development.

---

### Post by meborc on 2006-03-21
[QUOTE=dvarsam]A. Formats Supported by gedit Program:

1. Current Locale ( UTF- 8 )
2. Western (ISO-8859-15)
[/QUOTE]

so i guess you haven't used notepad for java either... :mrgreen:

---

