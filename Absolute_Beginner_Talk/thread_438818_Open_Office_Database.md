---
title: "Open Office Database"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-10
I am a big user of MS Access (currently using version 2000 in XP).  I use it in my business, and find the way it handles relationships handy and smooth.

I can run Access without a glitch on Ubuntu, but wanted to try out Open Office.

I keep running into a problem that has me stumped.

I create two tables.  The first table contains a key that I call ID.

The second table contains a field that I also call ID.

I want to establish a relationship between these two fields, and then build a form using table 1 as the main and table two as the subform.

OOdb has wizards that walk me through the process up to that point.

Unfortunately, when I finish setting up the form and click to use it, nothing will happen - I mean nothing.  I can click the button a zillion times and it just sits there.  I can move the wizard dialog box and see my form sitting there ready to go, but cannot escape past that last step in the wizard except by pressing cancel which, of course, cancels all my work to that point.

Access has other commendable attributes that I'm curious to see if OOdb supports.  For instance, in designing a table in Access, you can specify a list of acceptable data entries.  For example, if you had a field for days, you could specify that only Sun or Mon or Tues are acceptable entries, so that an error message would appear if the person entering data inputs Monday or Xun or whatever.  This provides data integrity that insures you can rely on the input when querying the database, etc.

I use the database to enter construction estimates, so, for example, if my entry person would enter str instead of stair, that entry would not get picked up and posted to the list I use to quantify the number of stairs.

Anyhow, I'm wondering if OO provides for that sort of data integrity.

I'd really like to try it, but can't even get past creating a form for data entry.

Help and other comments would be appreciated.

Thanks.

Caruso

---

### Post by starcraft.man on 2007-05-10
I don't actually use Base at all, but I believe your questions can be answered via some of the resources from the [wiki]("http://en.wikipedia.org/wiki/OpenOffice.org_Base") :) So, have a look through them :) I don't think there are that many Base users here, thats kinda specific... might also wanna go straight to the source, OO has [forums]("http://www.oooforum.org/"), I'm sure they would know :)

---

### Post by BLTicklemonster on 2007-09-16
I'm eager to learn to use Database or Access even, but the problem I keep running into is that every piece of literature I look over assumes I know the first thing about access. I've asked before about access, but ran into the "if you don't know whit, then why are you trying to use it" argument. Gee.

So I ask, is there some meaningful tutorial that guides the total noob like myself through setting up a database from scratch? The help file seems nice, but it doesn't really say, "okay, stupid, look here, do this first, then that, this goes here, that goes there".

I feel that if I can just get the mechanics of it down, then I'll be okay, but heck, I can't tell if I need to make a table, a query or coffee first.

This is totally frustrating. Yes, I have managed to make something in Access before, but it was just me messing around until I had some sort of ... something that would open that was totally useless to me, though it did perform certain functions that would appear to the casual observer that I'd done some magical thing with it.

---

### Post by tvrg on 2007-09-16
first time ever using base, but here's how i got about it:
- create new table in design view named 'polls' with the following fields
   id, integer, autovalue, primary key
   title varchar, 100
- create a new table in design view named questions with the following fields
   id, integer, autovalue, primary key
   question varchar 100
   poll_id
   votes
- open view > relations and drag a relation between poll.id and question.poll_id

go back to the base main window, select forms and create a new form using wizards
- in the first screen (field selection) select table "polls" and add all fields
- in the next screen select "add subform", based on existing relation, mark "questions", add all fields, click next
- in the next screen add the questions fields to the form, click next
- i layed the fields out as "in blocks" for the main form and "as data sheet" for the subform, click next
- set your preferences (i allowed everything)
- select a style
- name it polls and select "work with the form"
after clicking "finish" it opened the form in writer

as my first experience i get the impression it's fairly limited, but then again i don't plan on using it much (hated access too) but it appears to work

I should also note that I'm using the OOo 2.3 that's currently in gutsy

---

### Post by BLTicklemonster on 2007-09-16
Thanks tvrg. The main reason I want to learn to use access or database is because I have records of everything I've done over the last 7 years, and I'd like to be able to take them from excel and make them available in a database that can be searched for just about anything anyone could think of. If I can just get my head wrapped around the concept, I think I can move on from there.

---

### Post by swisscow on 2007-09-16
Many people have the problems with the wizards getting stuck, me included. I solved it by removing all traces of open office, then downloading from the open office website the new version and installing that. I believe it comes as rpms (or it did when I did it) which I then had to covert to debs using alien. There are instructions on the forum somewhere, certainly I have them in my posts somewhere if you want to look through them.

---

### Post by R_U_Q_R_U on 2007-09-16
> **BLTicklemonster said:**
> I'm eager to learn to use Database or Access even, but the problem I keep running into is that every piece of literature I look over assumes I know the first thing about access. I've asked before about access, but ran into the "if you don't know whit, then why are you trying to use it" argument. Gee.

So I ask, is there some meaningful tutorial that guides the total noob like myself through setting up a database from scratch? The help file seems nice, but it doesn't really say, "okay, stupid, look here, do this first, then that, this goes here, that goes there".

I feel that if I can just get the mechanics of it down, then I'll be okay, but heck, I can't tell if I need to make a table, a query or coffee first.

This is totally frustrating. Yes, I have managed to make something in Access before, but it was just me messing around until I had some sort of ... something that would open that was totally useless to me, though it did perform certain functions that would appear to the casual observer that I'd done some magical thing with it.


There is plenty of free online training here:
[http://office.microsoft.com/en-us/training/CR061829401033.aspx](http://office.microsoft.com/en-us/training/CR061829401033.aspx)

There are many sites with great Access tips like this:
[http://www.granite.ab.ca/access/tipsindex.htm](http://www.granite.ab.ca/access/tipsindex.htm)

---

### Post by Irihapeti on 2007-09-16
Here's the link to Swisscow's posts about installing the "official" version of Open Office.
[http://ubuntuforums.org/showthread.php?t=413392&highlight=Open+Office&nojs=1#goto_threadtools](http://ubuntuforums.org/showthread.php?t=413392&highlight=Open+Office&nojs=1#goto_threadtools)

I've used the method successfully. Thanks, Swisscow.

Unfortunately, Base seems to be the least reliable component of Open Office. There are plenty of messages to that effect on the Open Office forums. One of the, to me, very annoying things is that once you've defined a table you can't change its definition. I've got to the stage where I'm investigating MySQL as the actual database and using Open Office as a front end. There is an online tutorial for MySQL at [http://www.webdevelopersnotes.com/tutorials/sql/installing_mysql_on_linux.php3](http://www.webdevelopersnotes.com/tutorials/sql/installing_mysql_on_linux.php3) which I find useful for learning about what databases do in general. I agree with BLTicklemonster - there's a tendency to think that all database users are geeks with at least 3 years' experience doing fancy things.

HTH
Irihapeti

---

### Post by The Mekon on 2007-09-16
> **BLTicklemonster said:**
> Thanks tvrg. The main reason I want to learn to use access or database is because I have records of everything I've done over the last 7 years, and I'd like to be able to take them from excel and make them available in a database that can be searched for just about anything anyone could think of. If I can just get my head wrapped around the concept, I think I can move on from there.

You may find the following link helpful.

[http://sheepdogguides.com/fdb/fdb1main.htm](http://sheepdogguides.com/fdb/fdb1main.htm)

Brian

---

### Post by jesaisrien on 2007-11-13
Hi! I have been using postgres, which is very nice, but I change distros and versions so often, it's a pain to keep setting it up. So I have been trying to use base, which continues to get better and better. I'ver used Access in the past (years ago) and liked it - it did the job.

I'm using the Base on OO 2.3 at the moment, and it is the best version so far, but I am having one problem that maybe someone out there can help me with.

When I try and use the form wizard it does a beautiful job except for one smal but critical thing: It is really tiny - to the point of being unreadable. I can tell that there is something there, when there is data there, and I can see that I'm adding somethin g when I'm inputting data, but it it completely unreadable.

I could try and use the "zoom" tool in the short term, until a better version comes out, but the Zoom tool is apparantly frozen and can't be used in the final form.

So right now if I make a form for inputting data about all I can really do with it is wave to it, far off there deep within the screen. Ha! Not very useful.

---

