---
title: "[SOLVED] Help on making a web page..."
date: 2008-10-14
forum: Art &amp; Design
---

### Post by Margus81 on 2008-10-14
Hey!

I have no experience making web pages at all!

But I would like to make one for my soccer team, such that everyone can log in with its name and password and make a click somewhere, that he is coming to the training.

So that there would come a list of people, who would be coming.


So my questions would be:

1. Would it be a too difficult undertaking for a beginner?
2. How are those features - "log in" and "click, that I am coming" called?
3. Which program would support these features, which would you recommend?


Thank You so much in advance!

Greetings...

---

### Post by DrMega on 2008-10-14
> **Margus81 said:**
> Hey!

I have no experience making web pages at all!

But I would like to make one for my soccer team, such that everyone can log in with its name and password and make a click somewhere, that he is coming to the training.

So that there would come a list of people, who would be coming.


So my questions would be:

1. Would it be a too difficult undertaking for a beginner?
2. How are those features - "log in" and "click, that I am coming" called?
3. Which program would support these features, which would you recommend?


Thank You so much in advance!

Greetings...

It might be a bit ambitious for your first web project, unless you have plenty of time and enthusiasm.

I would start by building a static website with info about your team. That way you will develop a good understanding of HTML and CSS as you go along.

I would then go on to implement some dynamic functionality with PHP, just experiments at first, then gradually build your feedback features for your football site, learning as you go along.

There are very many tutorials all over the internet. I don't mean to be dismissive but it is quite a big subject and you can only learn by doing it, and experimenting.

Good luck.

---

### Post by Margus81 on 2008-10-14
But I would still need to know, how those things are called and if every open source web page creator supports them. Kompozer for instance... could one do it with that?

If I knew that info, I could start picking the program and start learning it.

Greetings

---

### Post by DrMega on 2008-10-14
> **Margus81 said:**
> But I would still need to know, how those things are called and if every open source web page creator supports them. Kompozer for instance... could one do it with that?

If I knew that info, I could start picking the program and start learning it.

Greetings

Kompozer is fairly good, but I personally prefer to write the HTML and CSS manually rather than letting a design tool do it. You won't learn much HTML if you use Kompozer, as it is a visual designer. I think it is always best to make your first few web pages entirely manually in a plain text editor, that way you become familiar with the structure of HTML and the more common tags. If you start with a visual design tool like Kompozer (and thus don't get a good grounding in HTML) you will really struggle when you come to do the dynamic bits.

The links that you click on are just hyperlinks. It's what they link to that influences the functionality. They can link to other pages of your site, pages on other sites, back to the page they are on (this last case is a special case used for submitting forms, and the functionality and syntax differs in this scenario.

---

### Post by StooJ on 2008-10-14
I second that; making dynamic sites will require learning HTML, CSS & PHP. The best way to learn is by doing it, and for that you need nothing more than a text editor.

There are many many tutorials online. I used [http://www.w3schools.com/]("http://www.w3schools.com/") and would recommend it as a great place to start on any aspect of web design. Work your way through the HTML tutorials to begin with, and enjoy it.

---

### Post by tonytr on 2008-10-14
As a possible alternative, you could check out [eteamz]("http://www.eteamz.com/")

If I recall correctly, the "basic" package is free and may have all the capabilities you are looking for.

Regards

---

### Post by Margus81 on 2008-10-14
Got the message and the tips!

Thank you so much DrMega, StooJ and tonytr !!!

Greetings!

---

### Post by ToasterThief on 2008-10-15
> **tonytr said:**
> As a possible alternative, you could check out [eteamz]("http://www.eteamz.com/")

If I recall correctly, the "basic" package is free and may have all the capabilities you are looking for.

Regards

[http://www.eteamz.com](http://www.eteamz.com) is not free. It has a 3 weeks trial though. 

This however is free and supports what the poster wants to accomplish.

[http://www.teamzonesports.com/](http://www.teamzonesports.com/)

---

### Post by tonytr on 2008-10-15
> **ToasterThief said:**
> [http://www.eteamz.com](http://www.eteamz.com) is not free. It has a 3 weeks trial though. 

This however is free and supports what the poster wants to accomplish.

[http://www.teamzonesports.com/](http://www.teamzonesports.com/)

Not to belabor the point, but I just double-checked eteamz and according to their web site they *do* have a free, no cost service, albeit with reduced services. Here's a [link]("http://www.eteamz.com/etz/compare/index.html") to comparisons of their options. What they offer when you initially signup is automatically a 3 week trial of the "plus" package which you can then refuse to extend, which should revert you back to the free, no frills package.

Btw - I'm not affiliated in any way with eteamz, other than I used their free package several years ago for managing my soccer team.

Taking a quick glance at teamzonesports looks promising too. If I were starting up another soccer team I'd look closer at it.

Regards - tonytr

---

### Post by whiteraven on 2008-10-16
Rather than re-inventing the wheel, I'd suggest you take advantage of a Content Management System (CMS). While you certainly could roll your own, it takes quite a bit of PHP knowledge as well as HTML and CSS which you won't get overnight. Plus, there are security issues that must be dealt with for any web site and you must effectively create two systems, one that the public sees and another for login and site administration. I could go on, but your best bet is to select one of the many fine CMS software packages out there and go with that. You still have the opportunity to learn, but will be able to have your site up and running quickly, in a matter of hours if all your ducks are lined up.

An excellent resource to look at and test drive a CMS is [OpensourceCMS]("http://www.opensourcecms.com"). All the major PHP/MySQL packages are there, like Joomla, Wordpress, etc. Going the CMS route will save you all sorts of headaches, get your site up quickly, and save you time that you can use later to write your own system. Plus there are countless themes for the popular CMS's - I've seen several made just for soccer.

I code regularly in PHP and would never think of creating a site from scratch unless I have a very specific need to be filled.

Something to think about.... no? Oh! And did I mention that all are open source and don't cost a cent? All you need is a host that supports PHP/MySQL (very common), or you can go flat file if you don't want a database. Databases are a good thing though, searchable, archivable, etc.

---

### Post by Margus81 on 2008-10-16
Great tips! Thanks to everyone!

Greetings,

Margus

---

