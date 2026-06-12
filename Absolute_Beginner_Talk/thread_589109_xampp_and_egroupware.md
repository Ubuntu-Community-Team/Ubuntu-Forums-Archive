---
title: "xampp and egroupware"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by johngavin on 2007-10-23
I have installed XAMPP
All is well

Now I need to install egroupware into the "docroots" of my webserver
I assume this means Apache , but for the life of me I'm not sure where to go.

I had to install Xampp into /opt , and this sudo instead of root is driving me crazy.

I am sure that I am making this too difficult

any help , Please !

---

### Post by edwardTheGreat on 2007-10-23
> **johngavin said:**
> I have installed XAMPP
All is well

Now I need to install egroupware into the "docroots" of my webserver
I assume this means Apache , but for the life of me I'm not sure where to go.

I had to install Xampp into /opt , and this sudo instead of root is driving me crazy.

I am sure that I am making this too difficult

any help , Please !

if it's the standard xampp for linux install look in /opt/lampp/htdocs

Look in your 
/opt/lampp/etc/httpd.conf file and you should find something like:

DocumentRoot "/opt/lampp/htdocs"

That will tell you definitively where it is
HTH
Ed

---

