---
title: "ubuntu 7.04 &amp; Apache 2 Server"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by jpinto on 2008-03-26
Hello Everyone,
I'm a *complete* newbie where Linux is concerned.  Here's what I need to do:

I need to setup a virtual directory in ubuntu 7.04 which can be accessed by the apache2 server.  

so the folder path would be : /var/www/App/wwwroot

wwwroot has to be the virtual directory which should have an alias say "App".  It contains a file: ui.html.aspx

I want to be able to execute the file from the browser like this: [http://localhost/App/bk/ui.html.aspx](http://localhost/App/bk/ui.html.aspx)
And it should show me my appln home page.

What's happening now is it is not executing the aspx file & showing me the site in the browser, it is just showing me the contents of the file, the code within it etc.  It is only browsing not displaying or executing (I'm not sure if I'm using the right words).

So far I've only worked on Windows & used IIS to setup my Web Application.  I found a lot of documentation on the Internet but those steps do not seem to be working for me.

How do I go about setting up a new site?  I just need one working site so that I can test my application on ubuntu.  I need a step by step bcoz I'm very very new to this.

Please help me out. Thanks in advance.

Jackie

---

### Post by zen_waters on 2008-03-26
ASP is a Microsoft technology, I am fairly certain that you can't run .aspx pages on apache.  If there were such a module, it probably wouldn't work very well, or be up to date with the .NET framework.

Jeremy

---

### Post by iSplicer on 2008-03-26
Apache only supports PHP scripting as far as I know, ASP isnt supported, neither is it widely used.

---

### Post by WorldTripping on 2008-03-26
You can run ASP using Apache.

From [http://www.apache-asp.org/]("http://www.apache-asp.org/")

> Apache::ASP provides an Active Server Pages port to the Apache Web Server with Perl scripting only, and enables developing of dynamic web applications with session management and embedded Perl code. There are also many powerful extensions, including XML taglibs, XSLT rendering, and new events not originally part of the ASP API! 

Apache::ASP's features include: 
Scripting SYNTAX is Natural and Powerful 
Rich OBJECTS Developer API 
Web Application EVENTS Model 
Modular SSI Decomposition, Code Sharing 
User SESSIONS, CIFS & NFS Cluster Ready 
XML/XSLT Rendering & Custom Tag Technology 
CGI Compatibility 
PERLSCRIPT Compatibility 
Great Open Source SUPPORT 
 


This module works under the Apache Web Server with the mod_perl module enabled. See [http://www.apache.org](http://www.apache.org) and [http://perl.apache.org](http://perl.apache.org) for further information. 

This is a portable solution, similar to ActiveState's PerlScript for NT/IIS ASP. Work has been done and will continue to make ports to and from this implementation as smooth as possible. 

From experience the above works well, though as it states it will only run Perl ASP, not VB ASP.

Couldn't comment on the .NET Framework though.

---

