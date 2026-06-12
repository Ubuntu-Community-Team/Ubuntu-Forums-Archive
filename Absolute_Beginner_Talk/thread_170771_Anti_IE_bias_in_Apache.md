---
title: "Anti IE bias in Apache?"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-05-05
I recently installed apache and started running a very modest website consisting mostly of pictures of my new born son.
Some of my friends could view it and some couldn't , it turns out that all those who use IE couldn't ,while other browsers worked perfectly. 
What could be the reason?
I haven't touched the config files. Just changed the default index.html.en page and inserted some pix and hyperlinks

---

### Post by horace on 2006-05-05
Hard to believe that it would be a problem with Apache itself, given that most of the world's web servers are running it without IE users feeling excluded! Is this an out-of-the-box type of install? The only way I can think of excluding IE users is to configure Apache to serve xhtml with the mime type application xml+xhtml - this does cause IE to offer to download the file because it doesn't know how to handle xhtml, but this wouldn't be the default (unless you use a .xhtml or similar extension on your pages).

---

### Post by Sef on 2006-05-05
> I recently installed apache and started running a very modest website consisting mostly of pictures of my new born son.
Some of my friends could view it and some couldn't , it turns out that all those who use IE couldn't ,while other browsers worked perfectly.
What could be the reason?

I.E. don't support open standards.   Microsoft creates its own standards, so you will be locked in to their software.

---

### Post by cgjones on 2006-05-05
How exactly does it not work with IE? Do you get errors, does the page not display correctly?

---

### Post by seshomaru samma on 2006-05-05
[QUOTE=cgjones]How exactly does it not work with IE? Do you get errors, does the page not display correctly?[/QUOTE]

It sais something like "Internet Explorer cannot open the page" (I'm translating from Chinese here , I dont know what the official English version is).

Now there is a new development , I found out that its just the index.html.en file ([http://ipaddress](http://ipaddress)  I dont have a domain name) that cannot be opened ,but if the address is of a folder or other pages it can open them (like [http://ipaddress/folder](http://ipaddress/folder))

As i said I didn't mess with any config files , I just apt-got apache and changed the default first page using Open Office (!)

---

### Post by echo $USER on 2006-05-05
[QUOTE=seshomaru samma]

As i said I didn't mess with any config files , I just apt-got apache and changed the default first page using Open Office (!)[/QUOTE]

That is your problem.  You need to put your index.html in the > /var/www folder not the > /var/www/default folder.

---

### Post by seshomaru samma on 2006-05-05
I did that.

What I meant is that I didn't mess with apache2.conf or httpd.conf or any of those.

The site works perfectly for non IE users
I can also open it with IE on a windows laptop that is on the same subnet as apache (on ubuntu) . It's very strange...

---

