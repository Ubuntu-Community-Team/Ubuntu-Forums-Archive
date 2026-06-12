---
title: "IP Address and Directory Naming"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by louie casimero on 2006-03-22
Hi to everyone. I'm new here and to linux. I hoping that someone has the answer to my question. We have a linux server and is our test server wherein we test our web applications. To access it we have to type the IP address plus the folders to get to the application. Its quite long so we were asked if there's a way in which we can shorten the path to our web app.


The path to our web app is like this: _\\172.16.1.22\memo_viewer\scd_viewer\index.php_

we are hoping for a way to ashorten it.. something like: **\\memo_viewer**

Can anyone help??

:confused:

---

### Post by Sendervictorius on 2006-03-22
Doesn't your browser cache urls you have visited before? When you start typing, it should present you with a list of matches. scroll down and choose  - it is quicker than typing.

The bit after the http:// is the addrress of the machine. No way to shorten it, but you could give the server a catchy name name like Test, by adding an entry to the hosts file in each client pc. (or put an entry in your DNS server on your network if you have one).

The rest of the url is like a path directory name. You can set up something shorter in your web server, or use url renaming if using apache web server.

but whatever you do you will always be left with [http://someserver/somepath](http://someserver/somepath)

---

### Post by louie casimero on 2006-03-22
yes.. the browser caches the previous url but what we are hoping to do is to shorten the path to our web application. The thing is for the url to be remembered easily so that even a person who is not that technical can type and go to the url specified easily. And it is an advantage for us specially if you want to go to the application for the first time. Are there any other Is there

---

### Post by Sendervictorius on 2006-03-24
Why don't you just build yourself a static html page with buttons or hypertext links to the full URL. Even make the first page the default page - or call it quick.html, and store it on your webserver root. Adding in an etc/hosts entry makes it even faster. So  you do:
1. [http://test/quick.html](http://test/quick.html)
2. click on link
3 you are at your page

---

