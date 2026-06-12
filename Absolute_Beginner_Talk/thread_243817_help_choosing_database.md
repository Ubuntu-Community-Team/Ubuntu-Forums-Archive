---
title: "help choosing database"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by neilw on 2006-08-25
Hello,
I'm after a linux database system with facilities similar to Microsoft Access, i.e. table/query/form/report creation. It's not for a server, just local personal use.

I've tried OpenOffice Database and it's complete rubbish (sorry, openoffice developers!), in that I get a crash every 5 minutes, clicking on options to open stuff takes an age (or sometimes doesn't even show), windows don't always open, etc.

I also tried gaby and glom, but they didn't do what I thought they described themselves as doing.

Can anyone offer any others to try?

thanks.

Neil.

---

### Post by hobbit1983 on 2006-08-25
One possibility would be to try using mysql with Open Office base as a grapical front end to provide the form generation etc.  It may be (be I can't be certain) that some of the stability issues may be due to the database engine.

HTH

---

### Post by neilw on 2006-08-27
Thanks. mySQL certainly has improved the speed (I didn't know openoffice used hsql and trying to remove it proved fruitless as the package manager wants to remove the whole of OO if I try to remove hsql - so I'm going to assume hsql is a personal database that only starts when office starts - though it would be nice to have it disabled at least?)

However, while the crashes are certainly down as well, it's still the buggiest thing I've used to the point of it being pointless - I get the impression the Database is the equivalent of Thunderbird (nice product but not developed much as it's more popular brother takes precedence). I get random crashes on clicking in textboxes, list boxes aren't always filled, etc. I'm also getting java errors, but I'm putting that down to using JDBC (I couldn't work out how to create ODBC stuff. Even when a crash happens and it does a recovery it opens the wrong thing (e.g. database crashes, it opens the word processor).

So I afraid it's back to Microsoft Office (I haven't booted windows on my computer in 2 months as well now!). I think the last straw is when I open a n Excel spreadsheet (even from within the spreadsheet), it starts up the word processor and shows the file as xml.

---

### Post by garner_nc on 2006-08-27
Neil,


    You don't work for Microsoft do you? (Maybe it's just something in your tone?)

    It would be helpful if you included a description of your machine, CPU, memory, etc.

    I use OO Base religiously with no problems. While it doesn't have ALL the bells and whistles of MS Office it suits my personal needs. 

   Here are some tips:
 
   1. Set-up MySQL to use as the database. You gain a LOT more flexibility and reliability. This is a little involved but well worth the time.

   2. Read the OpenOffice website FAQ's and support forums. If you're having problems, someone else has had the same problems also. 

   3. Contact OpenOffice. I've done so a few times and get fairly quick responses. Not overnight but within a couple of days.

   4. Download the latest version of OpenOffice and install manually. Yes, it's a little more work but I believe it eliminates a LOT of headaches.

   Thunderbird rocks! I've had NO problems with Thunderbird. Again though, I downloaded it from the Mozilla website and installed manually.

All the Best,
Doug White

---

### Post by neilw on 2006-08-27
ha ha, no. I've been MS free for 2 months now. I am using mySQL, but I'd rather not play with newer versions as being a newbie I'd rather stick to the official ubuntu packages until I know what I'm doing :)

I'll check out the open office website and see what it's like.

But I don't suppose you know how to get rid of hsql do you?

---

### Post by msak007 on 2006-08-27
I don't do much with databases so I've never used it, but have you ever tried [Kexi]("http://www.kexi-project.org/")? It's part of KOffice.

---

