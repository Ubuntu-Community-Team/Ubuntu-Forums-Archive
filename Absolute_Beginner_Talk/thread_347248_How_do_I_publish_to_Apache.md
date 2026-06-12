---
title: "How do I publish to Apache?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by luishrd on 2007-01-27
Hi all,

First of all, I am just learning to use Linux and web design at the same time.

I was able to set up my Ubuntu workstation with help from you guys specially Taurus, then decided to take it a step further.

Installed the server version on an old laptop including the LAMP package and pointed a domain I own to my IP. I can see the server default page when accessing it from the internet, but have no idea how to publish a website to it.

I am guessing there is some configuring to do, If anyone has done this please share.

While at it, what tool is used to design websites in Linux, Dreamweaver or Front Page dont have versions for Linux.

Thanks.

PS: Dont let the Join Date fool you, I never could get Ubuntu to work back then.

---

### Post by irish_flu on 2007-01-27
Apache stores documents in the /htdocs folder.  

If you put something in that folder called index.html, Apache will use that as the default page.

I think that's the way it is, at least.  It's been awhile since I used Apache without setting up all kidns of weird stuff . :)

---

### Post by luishrd on 2007-01-27
Thanks,

Thats a start, but that would mean that i have to do it from the server itself. I would like to find a good tool to use on my Ubuntu Workstation and just publish to my server through the internet from wherever I may be the same way Hosting services let customers publish to their servers.

Thanks.

---

### Post by Tipo on 2007-01-27
Apache publishes the files that are put in /var/www

An index.html page will be displayed (unless of course you install php and some other stuff on the server :))

You need sudo to move files into that folder, unless of course you chmod it to allow access :)

EDIT: To access and publish the files like you are asking, you'll need to install an ftp server (something like proftpd).

I believe gFTP is a GUI FTP client for Ubuntu...

---

### Post by taurus on 2007-01-27
In that case, you need to install either an ftp server (something like vsftpd or proftpd) or ssh server--sshd.  Then, you can just upload the files to your web server machine from your desktop or another machine.

---

### Post by HereInOz on 2007-01-27
I think you will find that when you install apache using synaptic, you will acquire a /var/www folder, and this is where you place your index file, and whatever else you need.

You can use NVU as a wysiwyg web page designer.

---

### Post by luishrd on 2007-01-27
Thanks,

found the /var/www and created a one line index.html, check it out lol

[http://www.crylh.com](http://www.crylh.com)

now which of the ftp servers is simpler for a total green one like me? and how do I make sure only I can publish to it?

Luis.

---

### Post by taurus on 2007-01-27
Let's see.  I have proftpd running on my VectorLinux, vsftpd running on my Edgy & FC6, and they are all in my office.  So, either one is good.  I am sure there are few other ftp servers out there that you can choose.  One comes to mind is pure-ftpd!

Otherwise, you can install sshd in which case you can upload all your files to your web server and you can log in using ssh at the same time.

---

### Post by luishrd on 2007-01-29
I am trying to install proftpd and get an error saying that it cant find the package. I guess I have to add one of those deb ....  to the sources.list, but I dont know which for Edgy only find for Dapper on the web.

Can I use the one for Dapper or anyone knows the one for Edgy.

Thanks

---

