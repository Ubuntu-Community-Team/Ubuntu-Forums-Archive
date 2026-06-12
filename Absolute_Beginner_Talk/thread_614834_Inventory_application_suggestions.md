---
title: "Inventory application suggestions"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Frumious Boojum on 2007-11-16
I'm trying to make my life here at work a lot easier, thus why I took one of the old computers and put Ubuntu for a second computer.

So, I'm looking for something that will help me out a lot...    I could go with a calendar program, but if I could do something a bit more organized than even that, would be great.

Part of my job, people submit requests for use of a/v equipment for the day.   So, I file it away and hope that I don't get things all mixed up by the time that it comes.   Basically, my ideal application is this:

[LIST]
[*]Lets me create custom fields for name, date, times needed, room location(s), number attending, etc.
[*]Add every item that we have available in our inventory and quantity available.
[*]Outputs that information into a calendar, decreasing the quantity available each day so that I cannot accidentally overbook during any given time period.
[*]Exports to a format where they can view this calendar on the web (on web space where I do not have access to configure PHP and such)
[*]Calendar can be ordered by location rather than time.
[/LIST]

I've been searching for the perfect solution.    I'm not much of a coder (ok, so I haven't written a program in about 11 years and that was on an Apple IIe), but I wouldn't much have time to write this program anyway -- probably would be a rather simple project, mostly.

Have any suggestions on an application, alternatives, or anything  of the sorts?

---

### Post by silent1643 on 2007-11-16
um not sure--but since no one else has chimmed in-
try zoho.com
might have something web based that will work for you - zoho creator is a nice app for creating databases and forms

---

### Post by Frumious Boojum on 2007-11-16
Definitely not going to work...

So, there's these blocks that we have on our computers and it likes to block a lot of things that really should be just fine.   But since I don't quite work at the central data center, I don't quite have the rights to get around these.

Anyway, that site is blocked due to "Personal network and storage."

I swear, sometimes, that big apple logo can seem a lot scarier that BOSD.

---

### Post by silent1643 on 2007-11-16
> **Frumious Boojum said:**
> Definitely not going to work...

So, there's these blocks that we have on our computers and it likes to block a lot of things that really should be just fine.   But since I don't quite work at the central data center, I don't quite have the rights to get around these.

Anyway, that site is blocked due to "Personal network and storage."

I swear, sometimes, that big apple logo can seem a lot scarier that BOSD.


not sure what to tell you then...
you can try something similar to ms access or filemaker - where you create your own database and forms - similar to zoho but not an online applcation and i haven't tried this one
maybe [http://www.kexi-project.org/about.html](http://www.kexi-project.org/about.html)

---

### Post by airtonix on 2007-12-29
Currently trying to provide an alternative to a friend who uses Filemaker Pro for his Buddhist Council Database.....

Few things to consider : 
 1. The simple nature of filemaker has led him to use some bad dbase design choices.
 2. At some point in the future, someone else will inevitably take over the running of this database, so it needs to be : 
 * cross  platform 
 * opensource 
 * Similar to existing Dbase programs.(ie MS Access)

So, my first route of action was to : 
 [Filemaker Pro]->exportAs.CSV && [OpenOffice-Base]->importFrom.CSV

1. First we export from Filemaker as a CSV file.
2. Create an OpenOffice Database (Base)
3. Import into an OpenOffice SpreadSheet (Calc)
4. Highlight all cells with Ctrl+A, then copy with Ctrl+C
5. Goto the OpenOffice Database 'Tables' section
6. right click in the table list on a blank space, and select paste.
7. You will be taken through some steps to create table from pasted data.

This is the most 'surefire' way to get your filemaker data over to openoffice base.

I have no idea how to export the forms that Filemaker uses, so i will have to create the forms. 
This will be done anyway as the Filemaker Database only contains one table ( which needs to be broken up into smaller tables), so the forms from Filemaker wont work anyway.

I am looking for aother dbase interfaces, openoffice is way too slow.

I am considering something small like Glom, but  i hope it connects to a mySQL server.

But the mySQL dbase wont be as portable as the openoffice dbase for these non-technical users, which leads me to sqLite.

sqLite is alot more portable than openoffice base, or mysql files. but i just need a good fast user interface to a sqlite dbase......firefox is not an acceptable interface, it is too slow.

update : Glom would be awesome except it only runs on linux, and requires a postgres server.

---

### Post by robertrej on 2008-01-03
I have been trying KEXI for a couple days and want to know is it possible to run
a   SQL     UPDATE or INSERT     STATEMENT in the kexi  sql window?
I tried but kept getting a error message.
Could be kexi only allows SELECT  statements  to be run.

example:                    select * from inventory;           --runs ok

                                 update inventory set part  = 'a1000' where id = 14;            --- error message


                                                    any ideas?   please help

                                                  Thanks/bob

---

