---
title: "How do I open a 2.5 gig .xml file?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by atorch on 2008-03-16
Hi,

This is going to sound a little silly, but...  I have an .xml file I want to open, and I can't.  It's very big (2.5 gigs), and I imagine that's part of the problem.

Firefox wants to open it by default, but it only takes me to a blank page, exactly the same as about:blank.

Text Editor tells it to me like it is:  it cannot open the file because it is "too big."

OpenOffice Database just eats up tons of RAM when it tries to open the file...

I tried to open it with Notepad (through Wine), but it didn't do anything at all.  Didn't eat up any memory, didn't open the file...



What can I do?  I need to either i) open this file or ii) convert it into something that I can open.

---

### Post by Oldsoldier2003 on 2008-03-16
> **atorch said:**
> Hi,

This is going to sound a little silly, but...  I have an .xml file I want to open, and I can't.  It's very big (2.5 gigs), and I imagine that's part of the problem.

Firefox wants to open it by default, but it only takes me to a blank page, exactly the same as about:blank.

Text Editor tells it to me like it is:  it cannot open the file because it is "too big."

OpenOffice Database just eats up tons of RAM when it tries to open the file...

I tried to open it with Notepad (through Wine), but it didn't do anything at all.  Didn't eat up any memory, didn't open the file...



What can I do?  I need to either i) open this file or ii) convert it into something that I can open.
Depending on what you want to do with it... if its a repetitive edit you could just use SED and make replacements without ever "opening the file". If its something you have to be able to read you might be better off splitting the file into usable chunks.

---

### Post by atorch on 2008-03-16
> **Oldsoldier2003 said:**
> If its something you have to be able to read you might be better off splitting the file into usable chunks.

Yes, I have to be able to read it.  How do I go about splitting the file?  (I didn't create it myself -- it's data downloaded from a site whose entire history is kept in one big .xml file.)

Edit:  Is there any way to lift Text Editor's file size limit?

---

### Post by jaakan on 2008-03-16
you need to import that in to a database like mysql or postgresql and just run queries against them.

---

### Post by lavinog on 2008-03-17
what happens if you use head?
```
head myxmlfile.xml
```
(do this in a terminal)

or does this work?
```
 less myxmlfile.xml 
```

gedit?

---

### Post by bruce89 on 2008-03-17
Jings, is that the OpenStreetMap planet file? Can't be, it's 3.7 GB compressed with bzip.

---

### Post by atorch on 2008-03-17
> **jaakan said:**
> you need to import that in to a database like mysql or postgresql and just run queries against them.

Sorry to be a total nublet, but how do I do that?

Google has led me here:
[http://codeghar.wordpress.com/2007/10/30/install-mysql-on-ubuntu-710-gutsy-gibbon/](http://codeghar.wordpress.com/2007/10/30/install-mysql-on-ubuntu-710-gutsy-gibbon/)

So I ran these commands:
sudo apt-get install mysql-server
sudo apt-get install mysql-client
sudo apt-get install mysql-admin
sudo apt-get install mysql-query-browser

Now under Applications > Programming I find:
MySQL Administrator
MySQL Query Browser

But both those applications seem to be made to connect to databases on other computers...  how do I use them to open an .xml file on my own desktop?  (If it is at all possible to do so...)

Edit:  Or, how do I convert .xml into a format the MySQL works with?

(As you can probably tell, I have at best a very very vague idea of what MySQL is.)

---

### Post by atorch on 2008-03-17
> **lavinog said:**
> what happens if you use head?
```
head myxmlfile.xml
```
(do this in a terminal)

or does this work?
```
 less myxmlfile.xml 
```

gedit?

head
yes, but it seems to be opening only the the first few lines of the file.  (The **head**er?)

less
yes, this works, and I can use the down arrow to move through the file.

the problem with both head and less is that they open the file without any formatting...  but at least I know the file opens and isn't corrupted or something

gedit does *not* work, it tells me the file is too big, just like Text Editor did.  in fact, gedit seems to be the same as Text Editor

---

### Post by jflaker on 2008-03-17
MySql 6.0 seems to have an implementation of Load XML......based on Load Data..

[http://dev.mysql.com/doc/refman/6.0/en/load-xml.html](http://dev.mysql.com/doc/refman/6.0/en/load-xml.html)

I may be worth playing with the new version just to get your data into a DB so you can do something useful with it.  There is no mention of max file size for the XML

Good luck

---

### Post by lavinog on 2008-03-18
> **atorch said:**
> head
yes, but it seems to be opening only the the first few lines of the file.  (The **head**er?)

less
yes, this works, and I can use the down arrow to move through the file.

the problem with both head and less is that they open the file without any formatting...  but at least I know the file opens and isn't corrupted or something

gedit does *not* work, it tells me the file is too big, just like Text Editor did.  in fact, gedit seems to be the same as Text Editor

Well what information are you trying to view?
less gives you the same output notepad would.
I also don't think firefox makes it much better.

it looks like tools such as grep and sed would also work
you can use:
```
split -l 5000 myxmlfile.xml newxml
```
this would split up the xml file into smaller files
you can change 5000 to whatever number of lines you need
there is a way to split it up at every occurance of a certain word using csplit

---

### Post by lavinog on 2008-03-18
> **atorch said:**
> Yes, I have to be able to read it.  How do I go about splitting the file?  (I didn't create it myself -- it's data downloaded from a site whose entire history is kept in one big .xml file.)

Edit:  Is there any way to lift Text Editor's file size limit?

The MySQL approach may be overkill for you, and not even be what you want

If you give us a portion of what the file is and how you want it formated we can help you with a sed statement that converts the file to a format you need.

```
sed -e 's~\<xmltag\>~~g' -e 's~\</xmltag\>~~g' < myxmlfile.xml > newxmlfile.xml 
```
replace xmltag with one of the tags that are used in the file
(there is a better expression, but I am still pretty weak with regexp)

---

### Post by atorch on 2008-03-18
Here's where I've gotten:

In a terminal, I run 'mysql -p', enter my password, and that takes me to the MySQL Monitor.

When I type 'show databases;' I see:
information_schema
mysql
test

The third one, 'test', is an empty database I created.  I want to get my XML in there.

Here's my new problem:  the .xml file has a fairly complex format, and it comes with a .xsd file that describes its structure.  What commands do I run within MySQL Monitor to load myfile.xml into the database test using myfile.xsd?

---

### Post by atorch on 2008-03-20
Maybe it would be helpful to give you links to the actual files:

ProsperDataExport_xml.zip

containing
    *  ProsperDataExport.xml (~2 GB) – The Prosper Market Export Data in XML format.  Click here to view a condensed example of this file.
    * ProsperDataExport.xsd (~13 KB) – The Schema Definition of the Export Data in XML format. Click here to view the file.

hosted at
[http://www.prosper.com/tools/DataExport.aspx](http://www.prosper.com/tools/DataExport.aspx)

---

### Post by frisket on 2008-03-20
> **atorch said:**
> Hi,

This is going to sound a little silly, but...  I have an .xml file I want to open, and I can't.  It's very big (2.5 gigs), and I imagine that's part of the problem..

Emacs.

P

---

### Post by atorch on 2008-03-20
> **frisket said:**
> Emacs.

Emacs prompts me with something like "File [filename] is large, really open?"

Then the file fails to open:  "byte-code:  Maximum buffer size exceeded."

Edit:  I've never used Emacs before, so maybe there's some easy way to get around this.  Anyone?

Now, my purpose in opening this file is to perform some statistical analysis on the data is contains.  I'm waiting for a prof to give me a copy of Stata, but, until then, would getting it into a MySQL database be helpful?  Perhaps I should have pointed this out when I started the thread...  Are there any (free) Stata-like programs for Ubuntu?

---

### Post by atorch on 2008-03-27
I'm sorry to Bump Up My own Post, but...

I'm attaching the .xsd to this post.  I've never seen the xsd format, but it seems to me to be a template for the larger xml file.

(Note:  I'm saving the .xsd as .txt so that the forum's little uploader will accept it.)

So, the question is:  is there a MySQL command to create a new database using an .xsd file as a template?

---

### Post by atorch on 2008-04-11
Anyone?

The .xsd is definitely a schema for the .xml, but I still have no idea of how to use it.  

Thanks in advance for any help,

- Adrian

---

