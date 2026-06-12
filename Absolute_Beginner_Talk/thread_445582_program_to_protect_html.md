---
title: "program to protect html"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by helphope on 2007-05-16
Hi everybody

I'm looking for a program which can encrypt the source of html pages and can stop spam robots from extracting email addresses.

 Any idea?:confused: 

Thanks

---

### Post by nhandler on 2007-05-16
Well, I don't know about encrypting the html source, but there are a few common ways to prevent spam bots from extracting your email address.

One of them is to display your email address in an image. Then, as long as your email address isn't the filename of the image, the bot won't be able to see it.

A second method is to write your email address like this: yourname[at]site[dot]com
Most bots are looking for something that looks like this: [email]yourname@site.com[/email]
So by doing it the first way, they skip right over it.

The third way is to simply not list your email address. Setup a form on your site that allows them to send you a message. Then, have a php/perl script to actually make it work. Since the bot doesn't have access to the php/perl script, it has no way of extracting the email address.

---

### Post by helphope on 2007-05-17
> **Cheater said:**
> Well, I don't know about encrypting the html source, but there are a few common ways to prevent spam bots from extracting your email address.

One of them is to display your email address in an image. Then, as long as your email address isn't the filename of the image, the bot won't be able to see it.

A second method is to write your email address like this: yourname[at]site[dot]com
Most bots are looking for something that looks like this: [email]yourname@site.com[/email]
So by doing it the first way, they skip right over it.

The third way is to simply not list your email address. Setup a form on your site that allows them to send you a message. Then, have a php/perl script to actually make it work. Since the bot doesn't have access to the php/perl script, it has no way of extracting the email address.

Thanks a lot.  A real good bunch of tips

---

### Post by Tomosaur on 2007-05-17
Unfortunately you can't encrypt HTML pages.

To stop bots, you can:

1) Set up a robots.txt file which forbids robots to scour your site. Unfortunately, the kind of robots that harvest email addresses do not give a damn about the robots.txt file - so its more to stop your site being listed in search engines, or to control which pages are allowed to be listed in search engines.

2) Set up a 'honeypot'. Read up on google how to do this - basically it attracts the bot to a page which links to another page, which links to another page etc etc. The end result is that the bot gets stuck in an endless loop. If you fill up these bogues pages with fake email addresses, then you can both overload the robot (and thus crash it), and also render its email address list useless. If only 1% of the email addresses the bot gathers are real, then it makes life much harder for the spammers.

3) Find some other method to display your email address. The old trick of using an image instead of text is unfortunately mostly useless now - the bots can now read images.

4) Best option - get a decent spam filter. I use gmail, and I end up with like 70 spam messages a week. Not one has ever worked its way into my inbox, and all I have to do is just empty the spam folder every few weeks.

---

### Post by proalan on 2007-05-17
Spam the Spammers, 

[http://www.auditmypc.com/freescan/antispam.html](http://www.auditmypc.com/freescan/antispam.html)

just copy the script and add it to your html

This will populate and crash their databases with randomly generated email addresses. This might be considered mailcious behaviour to some, but its the bots that push the button in my opinion

---

### Post by proalan on 2007-05-17
just to point out the obvious, be sure to place that script above your legit email addresses

---

