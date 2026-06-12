---
title: "[SOLVED] Kexi -- .csv import problem"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by caller#6 on 2007-10-29
Hey all,

I'm trying to import a .csv into a new kexi db.

I'm being very careful to check the field formats, and the import happens without any error messages, but...

I have two fields, a "time" and "date" that kexi detects correctly in the import dialog, but they both keep reverting to "text" during the import process.

Is there either
[LIST=1]
[*]Something I should check to make sure that my data source is clean and suitable for importing, or
[*]Some way to edit the field formats of a table without wiping out the data? (If there's anywhere to run SQL commands, I haven't found it.)
[/LIST]

versions: Kexi 1.1.3 (KOffice 1.6.3) (Using KDE 3.5.8) on Gutsy.

Thanks.

---

### Post by TheDriZZle on 2007-10-30
Are these the only two fields you're trying to import?

Time and Date is tricky because I'm pretty sure it has to be the exact format that KDE recognises for it to be accepted as a time or date field in Kexi.  Time might have to include seconds.

I read:

The default format for displaying dates and times is the same as you have set 
in the KDE Control Centre: Regional->Country/Region&Language->Time&Dates.

This is a 'dirty' change as you cannot change the display format for datatypes in Kexi.

---

### Post by caller#6 on 2007-10-31
> **TheDriZZle said:**
> Are these the only two fields you're trying to import?
No. There are also Text and Number Fields, but Time and Date are the ones that aren't importing correctly.

> **TheDriZZle said:**
> I'm pretty sure it has to be the exact format that KDE recognises for it to be accepted as a time or date field in Kexi.  Time might have to include seconds.
That seems like a good place to start. Thanks.

I didn't notice the first time around, but the import also failed to recognize blank fields, and simply shifted everything "left" in the table to fill those "holes". So I'll keep playing with it and report back when I have a fix.


*Update*

Okay. At least it's not just me. The Date/Time issue has been reported [here]("http://bugs.kde.org/show_bug.cgi?id=151478").

My other question, about a command-line interface to work with a .kexi file is moot. Yes, SQLite has a command-line syntax similar to SQL. No, that doesn't help me modify my table because SQLite doesn't support the "Alter Table Alter Column" command that I was hoping to use. And with that, I suppose I'll mark this question "solved".

---

