---
title: "i've installed LAMP, now what?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by demonicume on 2006-12-16
absolute newbie here. i got experience in repair, network set up, etc. but this is my first non-windows experience. i got my LAMP up and running. i'm about to install unbuntu desktop on one of my other boxes. i got XP running my main machine and a laptop... ok what do i do now? i am unsure of my options. what are somethings i can do to better understand linux itself and my new server. i'm looking to exploit every possibility here, i just dont know anyone who uses linux, so i'm alone in this. i'm unfamiliar with PHP and SQL, but i want to learn.

anyone got blogs or how-tos that'll help me out? dont be gentle, i want to master this.

---

### Post by outofnicks on 2006-12-17
Well, that's kind of like saying "I have a car, now where should I go?"
LOL, sorry...don't mean to be a smart a$$--I remember when I wanted to learn everything there was to know and check out all the possibilities.
All the information is at your fingertips. Did you get the apache-docs ? When you are at the default index page of your webserver, does the link to the Apache documentation go to the docs folder in your /var/www/ directory? If not, just check apache-docs in Synaptic Package Manager and it will be installed in the correct place if you used the default location for your webserver.
Do you have Perl installed? That along with PHP makes for a LOT of fun experimentation. Go to Hotscripts.com at [http://www.hotscripts.com/PHP/Scripts_and_Programs/](http://www.hotscripts.com/PHP/Scripts_and_Programs/) and check out all the neat stuff you can install on your server--this can keep you entertained for weeks or months. You don't need to know PHP or perl to install most of these, mainly only need to edit config files a little. 
One of the first things you may be doing is editing your http.conf file to enable different modules and expand the default capabilities of the Apache server.
What are your goals in life? If you aim to be a pro webmaster, server admin, or network admin of some kind, a local server setup on your computer is a good testbed for learning the ropes. Narrow your focus a bit, take it one or two steps at a time :)

---

### Post by chrisfay on 2006-12-17
I'd start by securing it:
[http://www.petefreitag.com/item/505.cfm](http://www.petefreitag.com/item/505.cfm)
[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)

Many more, too many to list....

Check out [http://howtoforge.com](http://howtoforge.com) for good tutorials on different stuff.

---

### Post by demonicume on 2006-12-17
thanks a lot. i didnt realize my question was so wide open. i installed this server and now the idea of digging in is exhilerating and intimidating. i'll start with the infomration youve posted here and keep checking back.

well, gotta get the install started.

---

### Post by WIVO_Riley on 2006-12-17
Thanks you guys..

I'm with you Demon- same deal.  I feel like I'm at the cusp of something big here, like a WHOLE new world opening up, teetering to take the first step but don't know which direction to go! lol

I've got an OLD P.O.S. that I have 6.06LTS installed, webmin installed, perl, sql, php, and I want to LEARN!

I just picked up a copy of Ubuntu Linux for Non-Geeks, and a copy of Ubuntu Unleashed.  I'm spending too much time searching and very little time finding.  Maybe I don't know even know the questions to ask yet.

Appreciate the security links-- It was first on my list of "to-do's"

Riley

---

### Post by Littleweseth on 2006-12-17
If you want to learn PHP, i humbly suggest the online book at [www.hudzilla.com/phpbook](www.hudzilla.com/phpbook) - outstrips all the paper books I own for writing style and content. It's even available in dead-tree form (as 'PHP in a Nutshell' iirc).

It will wow and amaze you, and aren't all good things free?

EDIT : Oopth - the URL above points to one of those god-forsaken domain parking sites. This is not the URL you are looking for *waves hand* Let us pass to [www.hudzilla.org/php](www.hudzilla.org/php) . *waves hand*

---

### Post by WIVO_Riley on 2006-12-18
Thanks much.  I look forward to the time where I may be able to get to the point where I can help others.

---

