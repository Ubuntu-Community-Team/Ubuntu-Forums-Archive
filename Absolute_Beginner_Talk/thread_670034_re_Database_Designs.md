---
title: "re: Database Designs"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by badbadputer on 2008-01-17
I am looking to broaden my horizons, so to speak and make an attempt to create a database for work.

Basically we currently have one, or several, however what I have access to sucks, plain and simple.  So my thought process, perhaps alittle small and slow at this time, is to create something thats workable for me and co-workers, test it out for a bit, then present it to the higher ups with proof that it can be done, if at all....Im hoping.
I can either continue to complain about what they have or try to help myself and them with something workable and hopefully easier.

My problem, and it's a biggie is I have no clue where to begin.  I know what I need it to contain and how I need it to work, so just need help in finding out how to get it together.

Any and all advice would be appreciated.

---

### Post by pjkoczan on 2008-01-17
First, I'd recommend not trying to re-invent the wheel. You'd probably do well learning to use a database from an existing RDBMS (Relational DataBase Management System). MySQL and PostgreSQL are both quite good, and free. Learn SQL, and go from there.

Second, you really have to think about how all your data will be tied together. If you want formal theory, check out the "entity-relationship model." If you want to be a little more casual, at least draw out a concept of what the data will look like.

Third, make sure it's robust. Make updates transactional, make sure that columns that are supposed to be unique have primary keys and unique indexes.

Last, make sure it performs acceptably. Learn about indexing and how to remedy slow queries. Also remember that "More computing sins are committed in the name of efficiency (without necessarily achieving it) than for any other single reason - including blind stupidity." -Gary Oliver

Database design is a bit involved for a beginner's forum. It's half art and half science. You'd be best off searching the internet for "database design" and "schema design" and work from there.

Hope this helps.

---

### Post by badbadputer on 2008-01-18
the info you provided is quite helpful, thank you....

---

### Post by anewguy on 2008-01-18
Another thing to keep in mind is that if the current database(s) contain the data you need, then you can create "views" of that data to present it many different ways.  "View" is a database term, not the standard usage, so you may want to check into it.

RDB development can be difficult - determining relationships, setting keys, setting referencial integrity, etc..  You would be best served I think to approach your manager with the idea that you'd like to learn more about actual database design, and let things grow from there.  It can only help you in your career.:)

---

### Post by Frogbarf on 2008-01-18
Database design is a lot more difficult than you might think. Unless the data is *extremely* simple in structure, a rookie/newbie/amateur/beginner is liable to create a design that doesn't work very well.

I used to work as a systems analyst, and over a period of 10 years learned relational database design by contemplating a single problem: the design of a database for holding information about a collection of classical music recordings. It took a lot of reading and a lot of thinking before I finally evolved a truly functional design.

[Note that the design I came up with was *not* appropriate for a collection of pop music recordings; that's how tricky this stuff can get.]

I actually implemented the thing in Paradox, but the learning curve for building the necessary interface to keep it updated was too steep, so I went to a much simpler DB manager.

If you are interested in actually learning this stuff, the first step is to learn entity-relationship analysis.You don't have to master every last jot and tittle of the subject, but you should get at least a broad understanding under your belt. Normalization is next, mainly 1st, 2nd, and 3rd normal forms. (I admit to never quite understanding 4th & 5th normal forms.)

The normal forms are best understood by learning what happens if you don't normalize! A few well-chosen examples can make the matter infinitely clearer than convoluted, wordy explanations. An advanced understanding of normalization involves learning when, why, and how to de-normalize a database schema. Example: theoretically "best" database structures often need to be denormalized for performance reasons.

I can appreciate what the OP wants to do, but in my experience, as a beginner he's almost certain to get it wrong. And if you don't believe me, let me give an example:

Recently I was tinkering with my CD inventory database and wanted to add a new feature. The first kick at that particular cat was WRONG and I had to back up and take a significantly different approach to get it right. (Part of the problem was the package I was using, Lotus Approach, which is not a fully general DB manager.)

Sorry, but I am now retired and am not up to date on good references on these subjects. Google is your friend.

PS: Somewhere along the line, you need to learn SQL, but it you have a good database design, your SQL will be fairly straightforward. In fact, that's a good test of a database design: what does the SQL look like to extract this or that data.

Hope this helps. I don't like to throw cold water on someone's desire to extend their knowledge and be helpful to their employer, but the subject is a great deal hairier than it may look like.

---

### Post by badbadputer on 2008-01-19
frogbarf....thanks for the info, going to have a better read tomorrow when not so tired...but definitely looking into entity-relationship analysis.

---

### Post by badbadputer on 2008-01-19
anewguy...thank you also for the info.  Although I have some experience in database view, it was quite a while ago, im hoping that once i get into it that stuff will come back to me.

---

### Post by stevenvu on 2008-01-19
try dabbledb.com It's a pretty simple way of mocking up a RDBMS structure and seeing if it works.

---

### Post by badbadputer on 2008-01-19
sam
sounds like good idea, will let you know how it goes, perhaps it is a programming issue.  Either way, thanks for info/advice.

---

