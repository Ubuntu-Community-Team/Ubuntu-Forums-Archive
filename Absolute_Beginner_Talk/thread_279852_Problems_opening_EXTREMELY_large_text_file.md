---
title: "Problems opening EXTREMELY large text file"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-18
Hey all. I didn't think it was possible, but a 250M zip file has produced a 2.0G text file, one that I simply cannot open with any application... gedit and all of the rest simply crash. Windows apps are even worse... the comp shuts down completely.

I'm not entirely sure what's in the file, but it's probably a CSV text file that I need to break down into *many* smaller files if I am ever to be able to work it into a database. Any clues as to how I might be able to just "peek" at the file without opening the whole thing? Can I break it up before opening it? TIA.

P.S. - The contents are kosher... it's not a virus or corrupted file. That much I can sort of guarantee.

---

### Post by ZiRo on 2006-10-18
Stupid question, but have you tried opening it with nano?

```
$ nano /path/to/your/file
```

Just a thought.

---

### Post by ricardisimo on 2006-10-18
> **ZiRo said:**
> Stupid question, but have you tried opening it with nano?

```
$ nano /path/to/your/file
```

Just a thought.

Not a stupid question... I don't even know what nano is. I'll give it a try. But tell me this... is nano going to give me the same error message as gedit?
```
GLib-ERROR **: gmem.c:135: failed to allocate 2145137207 bytes
aborting...
```

---

### Post by ZiRo on 2006-10-18
I'm not sure. nano is a console based text editor.

If that error is from nano, then i'm sorry :)

---

### Post by ricardisimo on 2006-10-18
> **ricardisimo said:**
> Not a stupid question... I don't even know what nano is. I'll give it a try. But tell me this... is nano going to give me the same error message as gedit?
```
GLib-ERROR **: gmem.c:135: failed to allocate 2145137207 bytes
aborting...
```

Here's the answer:
```
No such file or directory
```
Mind you, I dragged and dropped the file into terminal, so the path is correct.

---

### Post by ZiRo on 2006-10-18
you mis-pathed your file then.

I don't believe anything less. I don't see why it would through an incorrect path if the file is too big :\

---

### Post by ricardisimo on 2006-10-18
> **ZiRo said:**
> you mis-pathed your file then.

I don't believe anything less. I don't see why it would through an incorrect path if the file is too big :\

You're right... I didn't hit space after nano before drag-n-drop.:oops: 

So, now I'm looking at a the file (I think), but it's a blank white screen with command options at the bottom. I need a crash course in nano here. I'm assuming "Read File" and "Cut Text" are exactly what they would appear to be. Must I first open the file before cutting/uncutting? Please bear with me... I'm a total retard, but eventually i get it.

---

### Post by Anonii on 2006-10-18
This means that either the text file is empty or it just doesnt exist.

Try this one:
Go to the directory of the text file and execute:
**cat <text_file> | tail**

This will print the last lines of that file. I want to see if it will give you an error, an endless waiting time or something.

Also the nano idea was good. Command line apps, are always stabler and faster than GUI ones.

---

### Post by ricardisimo on 2006-10-18
> **Anonii said:**
> This means that either the text file is empty or it just doesnt exist.

Try this one:
Go to the directory of the text file and execute:
**cat <text_file> | tail**

This will print the last lines of that file. I want to see if it will give you an error, an endless waiting time or something.

OK... there's info there, exactly what's supposed to be there. I think it's confidential stuff, so I can't post it here. What's the next step for me? What's the largest file that either Gedit or my system can handle? I believe I've got 256M RAM, unless I'm very much mistaken. I need to break this up into smaller files - I guess smaller than 256M. Thanks again for any help.

---

### Post by Anonii on 2006-10-18
A solution would be copy-pasting. Which is hard, boring and obviously not precise.

[SIZE="1"][COLOR="Silver"]
You can do that with:

**cat <text_file>**

which will flood your terminal (if it doesnt crash) with ~500.000lines, or more, of text? And then, manually, you can copy-paste it in other text files.
Actually, much more than 500k, I have a log which is 2MB and it has 20k lines inside... 
The smaller text files, can aswell be in gedit. Just be sure to not copy-paste too many lines at once.[/COLOR]
[/SIZE]

EDIT: My mistake, you cant do that like this. Your terminal cant handle too many lines at once, and you wont be able to capture them all in a single terminal.

Its doable with a bash script too. But I lack the knowledge to create something like that. Probably someone else...

So, I'm out of ideas :/

---

### Post by mcduck on 2006-10-18
how about 'split' command?

'split -db xxxx filename outputname-' will split file into smaller pieces of xxxx bytes and name them as outputname-01 outputname-02 etc..

or use 'split -dl xxx filename outputname-' to split the file to pieces of xxx lines.

See 'man split' for more options.

---

### Post by ricardisimo on 2006-10-18
> **mcduck said:**
> how about 'split' command?

'split -db xxxx filename outputname-' will split file into smaller pieces of xxxx bytes and name them as outputname-01 outputname-02 etc..

or use 'split -dl xxx filename outputname-' to split the file to pieces of xxx lines.

See 'man split' for more options.

Very cool. Thanks! :D Seems to be doing the job. I still have no clue how large a text file I can work with... the larger the better, I would think. Anyone know the upper limit on text files and/or database files in OpenOffice Database? Thanks.

---

### Post by cwaldbieser on 2006-10-18
> **ricardisimo said:**
> Very cool. Thanks! :D Seems to be doing the job. I still have no clue how large a text file I can work with... the larger the better, I would think. Anyone know the upper limit on text files and/or database files in OpenOffice Database? Thanks.

It is probably proportional to the amount of RAM in your computer since a lot of text editors try to load all the contents into memory at once.  Line oriented tools like sed, awk, grep, or tail only read small chunks of the file into memory and output what they have processed so they are capable of dealing with large files without running out of resources.

What exactly do you want to do with the file?  If you are just searching for certain records, it might be easier to just grep for them.

---

### Post by ricardisimo on 2006-10-20
> **cwaldbieser said:**
> It is probably proportional to the amount of RAM in your computer since a lot of text editors try to load all the contents into memory at once.  Line oriented tools like sed, awk, grep, or tail only read small chunks of the file into memory and output what they have processed so they are capable of dealing with large files without running out of resources.

What exactly do you want to do with the file?  If you are just searching for certain records, it might be easier to just grep for them.

I might as well tell you guys the whole story:

It's voter contact information for the political campaign and GotV in which I'm involved. The file was given to one of our statewide candidates, so I fear that it might be the entire state of California, which would explain the size of the file. Hopefully it's "just" Los Angeles County... small potatoes, no? In either case, someone at the Secretary of State's office clearly failed to give us the right format, but it's too close to election time to do anything other than make this work.

Also, it's a database issue I'm having. I suspect grep would find specific things, but with a comma (or space)-separated-values format it makes no sense to find specifics and pull them out... You need whole lines, and lots of them to get the bigger picture. Thanks for all of the help, guys.

P.S. - I going to be posting and asking for suggestions from the OS crowd regarding legislative possibilities for Ubuntu et al. Partly what I've been doing here the past few months with Ubuntu is finding out just how viable the Gnu-Linux varietals really are, and if I could say with any confidence that a state like California could save some serious cash on software charges that could be better spent on paying teacher salaries. Please feel free to contact me with any suggestions along these lines. Thanks.

---

### Post by cwaldbieser on 2006-10-21
> **ricardisimo said:**
> I might as well tell you guys the whole story:

It's voter contact information for the political campaign and GotV in which I'm involved. The file was given to one of our statewide candidates, so I fear that it might be the entire state of California, which would explain the size of the file. Hopefully it's "just" Los Angeles County... small potatoes, no? In either case, someone at the Secretary of State's office clearly failed to give us the right format, but it's too close to election time to do anything other than make this work.

Also, it's a database issue I'm having. I suspect grep would find specific things, but with a comma (or space)-separated-values format it makes no sense to find specifics and pull them out... You need whole lines, and lots of them to get the bigger picture. Thanks for all of the help, guys.

P.S. - I going to be posting and asking for suggestions from the OS crowd regarding legislative possibilities for Ubuntu et al. Partly what I've been doing here the past few months with Ubuntu is finding out just how viable the Gnu-Linux varietals really are, and if I could say with any confidence that a state like California could save some serious cash on software charges that could be better spent on paying teacher salaries. Please feel free to contact me with any suggestions along these lines. Thanks.

I would probably get a database like PostgreSQL or MySQL, create a table for the data, and then bulk load your flat file (e.g. the "COPY" command for PostgreSQL).  Then you should be able to sift through the data using SQL to get the information you want.

I haven't worked with OO Base, so I don't know how well that will deal with large files.

You can always use "awk" to massage your flat files to get them into a format that is easier to load into your database.

At work, I convert customer flat files from their old systems to our system this way pretty regularly.

---

### Post by ricardisimo on 2006-10-21
> **cwaldbieser said:**
> I would probably get a database like PostgreSQL or MySQL, create a table for the data, and then bulk load your flat file (e.g. the "COPY" command for PostgreSQL).  Then you should be able to sift through the data using SQL to get the information you want.

I haven't worked with OO Base, so I don't know how well that will deal with large files.

You can always use "awk" to massage your flat files to get them into a format that is easier to load into your database.

At work, I convert customer flat files from their old systems to our system this way pretty regularly.

By flat, I'm assuming you mean CSVs. This one is just tabs, or spaces - haven't figured out which yet. But still, it shouldn't matter, right. I've never been able to maneuver through a database app, but I did have luck with these split text files in a spreadsheet, namely MS Excel on the home comp... just dropped the whole page into the first cell and Excel did the rest. I'm hoping the move from spreadsheet to database will be easier than giga-text file to database.
I'm also hoping I can get the programs you mention via Add/Remove or synaptic. I'll check now, but if you're on right now I'd love a link. Thanks.

---

### Post by localuser on 2006-10-21
Depending on the political party in question, you may be able to use the [COLOR="Red"]rm[/COLOR] command ;)

---

### Post by cwaldbieser on 2006-10-21
> **ricardisimo said:**
> By flat, I'm assuming you mean CSVs. This one is just tabs, or spaces - haven't figured out which yet. But still, it shouldn't matter, right. I've never been able to maneuver through a database app, but I did have luck with these split text files in a spreadsheet, namely MS Excel on the home comp... just dropped the whole page into the first cell and Excel did the rest. I'm hoping the move from spreadsheet to database will be easier than giga-text file to database.
I'm also hoping I can get the programs you mention via Add/Remove or synaptic. I'll check now, but if you're on right now I'd love a link. Thanks.

Well, at work we mostly use MS SQL Server, but I have worked with PostgreSQL before.  It is actually available for Windows, if that is the platform you are working on (see the home page [http://www.postgresql.org/]("http://www.postgresql.org/")).  You should be able to get the software from the Ubuntu repositories, too.  You probably also want the "pgadmin" package, as this will give you a nice graphical client to work with the database and see results.

By a flat file, I just mean that the data is in a plain old text file.  The way it normally works is that each record is its own line in the file.  Fields in the records are usually delimited in some fashion.  Commas are common, tabs are sometimes used, sometimes the pipe (|) character, etc.
Most databases I've worked with have the ability to pull large amounts of data in from flat files in a single shot.  The exact commands depend on the database, but they are all very similar.

For example, with MSSQL, you can use the "bcp.exe" utility to import/export data to/from flat files.  The "BULK INSERT <table> from '<filename>'" can also be used to import data.

With PostgreSQL, the command is "COPY <table> from '<filename>'".

This is usually the most efficient way to load lots of data.  A (much) slower way is to have a script generate the "INSERT" statements from each row.

Be careful about loading data into spreadsheets!  The problems you may encounter are:
+ For large files, different programs have a row limit (32,000 or 64,000 rows in some cases).
+ Spreadsheets tend to want to format your imported data, and sometimes this is especially bad if some of your fields are ID numbers with leading zeroes.  The spreadsheet may hapilly recognize the data as a number and remove the leading zeroes.

---

### Post by JayTee on 2006-10-21
Do you have Excel for Windows? If so, try opening it as a CSV file with that. It will ask you several questions about the file's record structure and give you a preview of what each record will look like. It should be able to handle even a huge file like that by using virtual memory. Each record should parse to a single row and that way you can select multiple rows to copy to other worksheets and do a Save As and choose text Comma Separated as the save format for however many files you'll need to break it into. I'd try grabbing at least a 1000 rows at a time to copy to another workbook and then save in csv format. That way you'll have fewer files to work with in Ubuntu.

---

### Post by ricardisimo on 2006-10-24
> **JayTee said:**
> Do you have Excel for Windows? If so, try opening it as a CSV file with that. It will ask you several questions about the file's record structure and give you a preview of what each record will look like. It should be able to handle even a huge file like that by using virtual memory. Each record should parse to a single row and that way you can select multiple rows to copy to other worksheets and do a Save As and choose text Comma Separated as the save format for however many files you'll need to break it into. I'd try grabbing at least a 1000 rows at a time to copy to another workbook and then save in csv format. That way you'll have fewer files to work with in Ubuntu.

It's all done. Thanks for the tips. I just decided to stick to Excel at home, 50,000 lines at a time, right at that comp's limit. Never did figure out an Ubuntu option... maybe next election cycle. ;)

---

