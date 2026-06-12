---
title: "Web hosting on 7.4 non server..."
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by alexjhill on 2007-05-04
Hi chaps.. what do i need to host some pages off my 7.4 install? i just want to (every now and then) fire it up so people can/ i can access stuff from work.

i have NO ip set up so i can always get a connection. i wonder what programs there are to run that would allow me to host a site off my laptop I'd also like a program that i can host a webcam from that generates it's own ouput / i just have to create a re-direct to the port it uses.



thanks!

---

### Post by dergringo on 2007-05-04
Hi

What do you want to host?
HTML? PHP? Python? Perl?

You are propably looking for a web server. The most common one is called apache2. You can install it with the following command:
"sudo apt-get install apache2"

Edit: If you got a running webcam on a port and you want to redirect, you need a rewrite rule. So I searched the internet a bit for you and I found the following:

> I have a solution I use at my server to proxy (not redirect!)
http://<servername>:80/folder1 -> http://<servername>:8080/folder2
and still be able to access other paths as usual. Please note both port and path are changed, while path in user's browser stays untouched (that I mean "not redirect").

Req:
apache2, mod_rewrite, mod_proxy, mod_proxy_http

Create following .htaccess file in /var/www/folder1

RewriteEngine   on
RewriteRule     (.*) http://localhost:8080/folder2/$1 [P]



No additional changes are required (except enabling .htaccess in apache2.conf if disabled) in /etc/apache2

Source: [http://snippets.dzone.com/posts/show/1318](http://snippets.dzone.com/posts/show/1318)

Greetings

Philipp

---

### Post by alexjhill on 2007-05-04
yea just HTML i'm no expert with pages :) also .. what about web cams? :)


thanks!

---

### Post by dergringo on 2007-05-04
Just edited my post - you're too fast for me mate :KS

---

