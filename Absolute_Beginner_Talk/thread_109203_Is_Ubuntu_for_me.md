---
title: "Is Ubuntu for me?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by thepomegranateprophecy on 2005-12-28
Recently I acquired a static IP address in my house and with that I want to host a server. I have asked elsewhere and they have said to try Ubuntu. Well, I just wanted to make sure its right for me.

What I have:

Dell Dimension 8300:
    200 GB HD
    512 MB RAM
    3 Ghz Processor
Connection:
    Cable connection
Monitor:
    Dell 17" Flat Screen

What I want to do:

I want to host a server for my band. Basically initally just a server to host a simple website with very little traffic and a small FTP site for the band members. Gradually I wish to incorporate a larger FTP site into the website allowing public access to the whole "anthology". I just want to have my own computer used as a server so I don't have to pay charges and I will only limit my services by my knowledge.

-Website
-FTP site
-E-mails

What I can do:

Well, I'm still in highschool. I really didn't do much on Windows when I lived with it. I really hated it and after getting fed up purchased a Macintosh. I recently re-installed Windows, so I have two working computers, which I find unessecary. But, while never dabbling in command line in Windows, I dipped my hand in with my Mac, since I was less worried about destorying the whole computer. I am fairly proficeint in web design, nothing outstanding but definetly a work in progress. I can learn quite quickly but I must say that I'm in no advanced computer user.

What I have been told to do:

I have been told use Linux or Windows. I was told Linux is the only option for a true server, while I would be hemmed in by Windows even if it was easier.

-Stock Windows Web Hosting software
-Abyss Web Server
-XAMPP
-Ubuntu
-Linux in general

What I want to do:

Get an advil because my brain hurts. I have no clue what to do. I have no problem going out for Linux, but why do so if its a lot harder for relatively easier reward; however, can I let myself be hemmed in by Windows? Is the learning curve that high? Unfortunately I have been given advice from diehard web hosting people, the kind of people who would chew on code for breakfast instead of cereal. What I have noticed is these people pick sides and pick it well, which isn't helpful when someone needs unbiased and insightful help.

So, please help by either telling me if Ubuntu is it, if there is another solution, or if there is another forum I can visit that could better help my indesicive needs.

Thanks for all the help.

---

### Post by Imexius on 2005-12-28
Definetly go for ubuntu:cool:

---

### Post by thepomegranateprophecy on 2005-12-28
Any more specific recommendations? Where do I start, how do I do this?

---

### Post by xtacocorex on 2005-12-28
While I haven't really set up a server by myself, I would definately say that Linux is the way to go. If you'd run Window's, I'd suggest getting Win2003 Server, but that is probably beyond your price tag.

I would use Apache for the webserver. It isn't that hard to configure, at least from my brief experiences with it on Windows. 

Email is definately another story. I was recently in a Cyber Defense Competition (with people who know more about servers than I since they are Com Sci and Computer Engineering majors) and email was one of the harder things to set up, but not impossible. I don't know the names of the email servers, except for Postfix, but I don't know how to use them.

If I'm correct, I think ftp servers are already installed, so setting them up and securing them is just a matter of configuration files, I could be wrong though, but everything you could possibly need is in the repositories, so obtaining the programs is easy.

I hope this helps some.

---

### Post by Norberg on 2005-12-28
Yes Ubuntu is for you to install a webserver you only have to run sudo apt-get install apache2 it could'nt be easier.

---

### Post by 504harry on 2005-12-28
This sounds an interesting Thread....many folk will want to have a simple server for similar reasons......no mention about back-up PSU's or RAID mirror (so you have a complete set of data in the event of HDD failure)
Perhaps these are lower-down the list of **Must Have's...**

My local LUG (Linux User Group) was considering their own WIKI on a server, but it can't be that easy, as they are way-ahead of me.
/
Let us know when the site's running so I can give it a try.....you will have to consider......... Web-User minimum system-specs......I have an Audigy 2 sound-card, but don't know what Ububtu installs to play it.
/
Good Luck
(PS) 
I changed the "Title" as there have been other similar threads concering the migration from Win to Ubuntu.....whereas you have "probably" made the right choice...hope you don't mind

---

### Post by thepomegranateprophecy on 2005-12-28
Ok guys thanks it sounds like Ubuntu will be perfect for my needs. I'll just forget about the e-mail think and use gmail. FTP and webhosting is fine. Back-up is very important, I forgot to mention.

So, where do I begin, is there a good guide for installing and using Ubuntu or should I just download and search as I go on?

---

### Post by peanut butter on 2005-12-28
for apache just do apt get like menttioned eirlier for an ftp server how to go here [http://www.ubuntuforums.org/showthread.php?p=532679](http://www.ubuntuforums.org/showthread.php?p=532679) you also might want to enable root when you have ubuntu installed do sudo passwd root type in your password type in a password that is easy to remember yet secure type in that password again
for your webserver you must put everything in the /var/www folder that youwant on your website

if you need backup you will want to make another partition of your hd (hard drive) and zip your backups in that folder

---

