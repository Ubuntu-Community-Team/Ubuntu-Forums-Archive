---
title: "[SOLVED] FTP suggestions to upload website"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2008-01-21
I've read that gftp is broken. so I've looked in Synaptic for another.  Several choices appear but before I choose, I'd like to ask if there is an ftp alternative which doesn't use the terminal  and is very user friendly, please?

---

### Post by renzokuken on 2008-01-21
if you use firefox then use "FireFTP". 

its an awesome addon for firefox that gives you an ftp client in your browser. its the only one i use these days

[https://addons.mozilla.org/en-US/firefox/addon/684](https://addons.mozilla.org/en-US/firefox/addon/684)

---

### Post by stump138 on 2008-01-21
You can also try [Filezilla]("http://filezilla-project.org/download.php?type=client")
which is popular with many and easy to use :)

also available via apt now afaik

---

### Post by a.v.l on 2008-01-21
> **renzokuken said:**
> if you use firefox then use "FireFTP". 

its an awesome addon for firefox that gives you an ftp client in your browser. its the only one i use these days

[https://addons.mozilla.org/en-US/firefox/addon/684](https://addons.mozilla.org/en-US/firefox/addon/684)

How do I install this please. Your link allows me to click a download button  which downloads it to the desktop but I cannot open it from there. :(

---

### Post by a.v.l on 2008-01-21
> **stump138 said:**
> You can also try [Filezilla]("http://filezilla-project.org/download.php?type=client")
which is popular with many and easy to use :)

also available via apt now afaik

I'm having the same problems here too. Its on my desktop after downloading it, there but I cannot open the .tar file to install it, help!

---

### Post by Sidewinder1 on 2008-01-21
I was not aware that there was anything wrong with gftp; I've been using it for a little over a month with no problems. I installed it via Synaptic Package Manager and It put an icon in my Applications>Internet menu. I then downloaded (via the same method) Quanta Plus to build my web site locally and gftp'ed to my web host. Check it out if you like at;  [http://mysite.verizon.net/worralle](http://mysite.verizon.net/worralle)  It's a very simple site with some pics and a table.
Hope this helps.

---

### Post by Dr Small on 2008-01-21
+1
I have been using gFTP for over a year with very few problems.
Occasionally it will freeze when it attempts to ask you if you want to overwrite the file, but that could be due to connection too.

Other than that, it works fine and would recommend it to anyone.

Dr Small

---

### Post by zach12 on 2008-01-21
gFTP work's fine with me

---

### Post by renzokuken on 2008-01-21
for fireftp use this link instead

[http://fireftp.mozdev.org/](http://fireftp.mozdev.org/)

click on "Download FireFTP" in the green box and it will autoinstall in firefox.

restart firefox then it will be in your "Tools" menu

---

### Post by a.v.l on 2008-01-21
> **Sidewinder1 said:**
> I was not aware that there was anything wrong with gftp; I've been using it for a little over a month with no problems. I installed it via Synaptic Package Manager and It put an icon in my Applications>Internet menu. I then downloaded (via the same method) Quanta Plus to build my web site locally and gftp'ed to my web host. Check it out if you like at;  [http://mysite.verizon.net/worralle](http://mysite.verizon.net/worralle)  It's a very simple site with some pics and a table.
Hope this helps.

Seeing as a few of you are using gftp I gave it a try. Unfortunately, more than likely through my own inexperience with using it, I've managed to loose my website altogether. Now when I type my web addresss in a browser I don't see my webpages, just this message.

Forbidden
You don't have permission to access /index.html on this server.
Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.

Before trying this I had a five page website created in MS Windows Front Page and was  trying to move it to Linux using Komposer. I've re-written the new website and would appreciate some help in using gftp to try and regain my website as it's obvious I'm doing something wrong in gftp:confused:. Can someone help please?

---

### Post by thelatinist on 2008-01-21
I use lftp from the terminal. *shrug*

---

### Post by OffAxis on 2008-01-21
> How do I install this please. Your link allows me to click a download button which downloads it to the desktop but I cannot open it from there.
if your download is a .xpi file you can drag (from the desktop) and drop it (on an open window of firefox) to install.

---

### Post by houstonbofh on 2008-01-21
I like filezilla.  It is in the repos, so you can install it with synaptic.  It also has a nice look and feel.  It sounds like you uploaded files with the wrong permissions, and so the web server can not "see" your files.  You might need shell access to fix this.  Do you own the web host?

---

### Post by Sidewinder1 on 2008-01-21
<Quote:>            Forbidden
You don't have permission to access /index.html on this server.
Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.

That's strange. I was under the impression that the "index.html" or "index.htm" was the default file read by any browser 'touching' the website. What is your web site's url? When I used gsftp to access my site, I just put in the url [I]without [I]  the index.html. When I got in, with password, of course, I could then see the file structure etc.

---

### Post by thelatinist on 2008-01-21
> **a.v.l said:**
> Now when I type my web addresss in a browser I don't see my webpages, just this message.

Forbidden
You don't have permission to access /index.html on this server.

You have set the permissions wrong on that file.  Chmod it 644.

---

### Post by a.v.l on 2008-01-21
Just to let you all know that I've resolved the issues I had with gftp and its working ok now. Thanks for the advice.

---

### Post by Thund3rstruck on 2008-01-21
Main Menu:

Places > Connect to Server > FTP w/Login

Doesn't get easier than that! Ftp sites appear as if they're local in Nautilus. It's awesome!

---

