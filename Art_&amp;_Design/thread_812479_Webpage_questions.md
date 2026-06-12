---
title: "Webpage questions"
date: 2008-05-29
forum: Art &amp; Design
---

### Post by jayrix on 2008-05-29
Hi all creative folks..

I want to make a website for hosting results for local funfotball teams. So how do i start ? Dont have to be any nifty stuff, just basic page with the results in the different divisions and tables. 

php + sql = true ?

Or can i just use a predefined webpage thingy like phpnuke and edit in the stuff i need ? (or similar projects)

I want this to be very easy to update etc, and could been nifty if i had the choice to add users who can update results/tables.


So if any of you have an idea please put it out here.. :)

---

### Post by Xfcn on 2008-05-30
PHP + MySQL yeah, that'll do it.

---

### Post by Samhain13 on 2008-05-30
I'd go with PHP + MySQL also.

However, plain-old static HTML might also be the way to go, depending on what sort of data we're talking about and how you're planning on turning that data into information. Hehe. PHP + MySQL does tempt you to make the site more complicated than necessary. :)

---

### Post by jayrix on 2008-05-31
Well i found this script tho [http://webscripts.softpedia.com/script/Games/Football-Website-Manager-41779.html](http://webscripts.softpedia.com/script/Games/Football-Website-Manager-41779.html)

That should do it for me, the problem is that i can't import the sql file (took it in manually) and site not working. I got both php and mysql working on my server (winXX server) and i have no errors that i can see.

Isnt it any settings that i can see php errors or something ? so i can find out where i need to edit some files etc.. feels like i am working in the dark. :(


mysql version: 5.0.51b-community-nt
php version : 5.2.5

---

### Post by Samhain13 on 2008-05-31
PHP errors (type, line and file name) normally come out in the web browser. Unless, of course, the developer prevented PHP from outputting errors.

---

Ok, I played with FMW a bit.

Instead of using PHPMyAdmin, I used MySQL Administrator and MySQL Query Browser to create the schema and the users, as stated in the "readme". There was a problem opening/using fb.sql because of some encoding issue so I opened the file in Gedit, copied the contents and pasted them to the script window of Query Browser. Now, there I have the tables required by the application.

BUT, when I loaded FMW in my browser, I got the following errors:

> 
Warning: require_once(DB.php) [function.require-once]: failed to open stream: No such file or directory in /media/Sandbox/Webwork/Experiments/FMW/db_connect.php on line 6

Fatal error: require_once() [function.require]: Failed opening required 'DB.php' (include_path='.:/usr/share/php:/usr/share/pear') in /media/Sandbox/Webwork/Experiments/FMW/db_connect.php on line 6


Perhaps you can work this out. Good luck. :)

---

