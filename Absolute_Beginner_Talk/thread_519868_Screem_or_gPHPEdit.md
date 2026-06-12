---
title: "Screem or gPHPEdit?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-08-07
Is there a significant difference between Screem and gPHPEdit? 

Based on the descriptions they both seem to do the same thing and their ratings are nearly the same. I would appreciate hearing if any folks out there have used both and what their preference was/is.

Also, (if I am allowed two questions in one posting), 'If you have OpenOffice.org Database installed, do you need or is there an advantage to installing MySQL Administrator and/or MySQL Query Browser?'

What would you recommend for a noob?

---

### Post by Pragmatist on 2007-08-07
> **rsnow said:**
> Is there a significant difference between Screem and gPHPEdit?
I think screem does much more, at least according to the package descriptions which I read in synaptic:
> 
gPHPEdit:
**development environment for PHP/HTML/CSS**
gPHPEdit is a GNOME2 editor that is dedicated to editing
PHP files and other supporting files, like HTML/CSS. It
has support for drop-down function lists, hints showing
parameters, and syntax highlighting.

> 
SCREEM:
**A GNOME website development environment **
SCREEM is a tag-based Web page editor which aims not only to aid in creating
Web pages, but also to provide [B]useful site maintenance facilities,
including automatic link updating and site upload facilities.[/B] SCREEM has
more than just the usual HTML tags, with features for including Javascript,
PHP, cascading style sheets, etc within your site.
It is **written for use with the GNOME** ([http://www.gnome.org](http://www.gnome.org)) desktop
environment


  If you need that extra functionality (for example, site maintenance tools), or if you just prefer the way screem looks or works, then go with that.  If not, my view is that lighter weight programs are better since they load and run faster and are less likely to crash.  You could install both and see which you like--that is what I do.  I'm partial to bluefish, even though it can't do as much as screem.

> **rsnow said:**
> ....If you have OpenOffice.org Database installed, do you need or is there an advantage to installing MySQL Administrator and/or MySQL Query Browser?....
After searching around, it seems that since OpenOffice2, Base can be used on its own.  However, you can also use it with those other databases if you want.  The question is, what do you need the database for?  The choice of database program depends on what your using it for.

---

### Post by rsnow on 2007-08-07
> **Pragmatist said:**
>  The question is, what do you need the database for?  The choice of database program depends on what your using it for.

That is a good question. I'm not even sure I do need a database. What I want to do is to set up a web site that will mostly be used for people to look at and hopefully download some royalty free gospel music. I also plan to have some audio & video stream.

---

### Post by Pragmatist on 2007-08-07
> **rsnow said:**
> That is a good question. I'm not even sure I do need a database. What I want to do is to set up a web site that will mostly be used for people to look at and hopefully download some royalty free gospel music. I also plan to have some audio & video stream.
I couldn't tell you if you do or do not need a database for that.  How many songs do you have?  A typical example of a database-driven website is an e-commerce site.  They have a catalog of products and they want to store information on each product and serve it to their visitors on request.  They also want to store information on each customer.

 A database has a "record" (row) and in that record you find many types of information for a particular thing.  If it was a library catalog, you would have a single "record" (row) for a book and each "field" (column) of that row, would contain information about that book (title, author, subject, keywords, price, ISBN, publisher, location, etc...etc...).  Sorry if you already know all of this, but if you understand how a database works, you can usually figure out if you need one :)

Without knowing more information, if I were making a website for people to download a few songs, I wouldn't use a database.  If I had hundreds of songs, I would probably store them in a database, and design a database-driven website to deliver them to people based on requests (i.e. searches).  If I even had 100 songs, I might just alphabetize them and have a page for each letter of the alphabet--or any number of other non-database solutions.  It all depends on your exact needs, what you can do with your ISP, and how much time and expertise you'll need.

---

### Post by rsnow on 2007-08-07
What you described gives me an idea of what I'll do for starters. If my repository of music grows I can always transition to a database.

So, for now I think I'll just go with whatever I can accomplish with Nvu and see how it develops.

Thanks for taking the time to give me your viewpoint.

---

