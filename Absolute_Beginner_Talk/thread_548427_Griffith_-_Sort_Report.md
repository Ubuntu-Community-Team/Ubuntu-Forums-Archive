---
title: "Griffith - Sort Report"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-09-11
I have one problem with Griffith, the report generator.  What I want is a list of all the movies in the database sorted alphabetically.   Griffith does not manage this, the reports are in the order that the movies are entered into the database and cannot be sorted or a general mess (all information for one record and then the next).

The database seems to be a .db if this helps.

Any suggestions how to get an alphabetic report?

---

### Post by kellemes on 2007-09-11
Excuse my ignorance..
Yesterday I started using Griffith so I don't know too much about it..
But I don't see any report-generator. Where can I find it?

---

### Post by expatCM on 2007-09-11
File / Export / select the format

Apart from this weakness, Griffith is a VERY good program...

---

### Post by Terl on 2007-09-11
I noticed at the web site ([http://griffith.berlios.de/wiki/User_Guide]("http://griffith.berlios.de/wiki/User_Guide")) that it does say it filters.  It does not say it will filter an export.  Have you tried importing the resulting text/csv file into a spreadsheet or a database?  I notice the site does say it interfaces well with databases.

---

### Post by expatCM on 2007-09-11
Yes, the filters are good.  But they do not export on the report.

I looked at the CSV output but I have no idea how to sort it.  The problem (from my perspective) is that the output is all the record details are in a single column and not clear.  For example, the title appears on every 25th line BUT so does a lot of other information in the same column after the title.  

For example, this is the third record, starting on line #51.  The following is line #51 with the title first.
3,Schindler's List,Schindler's List,,1993,R,USA,Biography / Drama / History / War,8,195,,False,False,,http://www.imdb.com/title/tt0108052,http://www.imdb.com/title/tt0108052/trailers,"Oskar Schindler uses Jews to start a factory in Poland during the war. He witnesses the horrors endured by the Jews, and starts to save them.","Liam Neeson as Oskar Schindler

I see that there are two commas at the end of every title.  So I guess it must be possible to search for every 25th line and then extract the text up to the point that ,, appears and then move onto the next 25th line.  The problem here is that I have precisely no idea how to do that ...  not even in OO Calc.

---

### Post by Terl on 2007-09-11
You should import the csv into the spreadsheet program (easiest unless you are familiar with database programs).  I am at work and am on windows right now.  Do you have open office installed?  Or a spreadsheet program?  If so there should be an option to import data - might be under a menu for file, data, or even edit.  Once the data is in the sheet you will be able to sort, just remember to sort the whole sheet not just the column.

EDIT:  use calc.  The import tab is probably under the data menu item.  (I got a screenshot up at work :) )  This is the kind of thing I do at work, I am a data analyst :)  You could also pull the file into base but I think calc would do what you need.

---

### Post by kellemes on 2007-09-11
Find "PluginExportCSV.py" in your plugin directory and change..
```
for movie in self.db.Movie.select():
```
into
```
for movie in self.db.Movie.select(order_by=self.db.Movie.c.title):
```

That did it for me..

---

### Post by expatCM on 2007-09-11
erm ... the plugin directory you mention ....  sure I must have one but I have been trying to find it and come up blank.  Any suggestions where I should look?

---

### Post by kellemes on 2007-09-12
I'm using this on Windows so I don't where it is on GNU/Linux actually..

Does this bring up something?
```
sudo updatedb
locate PluginExportCSV.py
```

---

### Post by expatCM on 2007-09-12
oh .. the locate command.  I had used whereis and find.  Locate works.

I edited the file as suggested but it does not quite work.   What now happens now is that I get the title from records #51, 62, 141, 146, 165, 167, 168, 169, 150 (followed by False,False on each line) at the start of the report  and then it is blocks of record information and then individual tiles and records .....

---

