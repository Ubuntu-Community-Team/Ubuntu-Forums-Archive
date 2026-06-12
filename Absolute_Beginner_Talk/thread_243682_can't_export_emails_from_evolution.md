---
title: "can't export emails from evolution"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Pragmatist on 2006-08-25
I'm unsuccessfully trying to export emails from evolution.  

Everywhere I read that it is possible to Right-Click on an email(s) and choose Save As... and then save it in mbox format. 

I can Save As.... but I see no option for saving as mbox or any other particular format.

I'm using Dapper and most of the suggestions I've seen are dated before the Dapper release.  Could it be that the current version of Evolution has no way of exporting emails????

I've tried copying the .evolution folder, but I don't consider this a good solution.  First, it is no good in migrating from evolution to other programs.  Second, it is messy.  I copied my .evolution folder to my laptop, which also runs Dapper, and I had files that wouldn't copy over, duplicates of some emails, etc...

---

### Post by electricshoes on 2006-08-25
I just did this the other day going from Evolution to Thunderbird.

What I did since Evo keeps the mail in mbox format in ~/.evolution/mail/
is just open Thunderbird and import mbox format and point there.

Are you trying to export and then import into another mail client? or just backup the mail.

If you are going to your Dapper laptop then I would just backup the .evolution folder like you did, then open the mail client on the laptop and import the .mbox files from the .evolution folder into the new mail client.

---

### Post by Pragmatist on 2006-08-25
Thanks for answering.

Ok, when I use the Import feature, I'm given two choices:
1.) import data and settings from older programs
2.) import a single file

#1 won't work since it isn't looking for evolution, it is only looking for:
Pine, Netscape, Elm, iCalendar  and I get a message to this effect and am only given the choice to go back and pick choice #2 (import a single file)

#2 will work ONE file at a time.  I have two problems with this.  First, there is no way to tell what is an mbox file. There is no extension indicating an mbox file and the command:
 ```
file
```  doesn't recognize anything as an mbox file. Nor does nautilus show any file as an mbox file format.

So, the only way seems to be:

(a) Go into evolution, choose File-->Import and then choose "import a single file"

(b)  Navigate to  ~/.evolution/mail/local/folder name  and try and guess which file is an mbox file.

  Second, I have many files!  I'd have to create folders and individually import each file corresponding to each folder.  This is very tedious.  Why would evolution have a simple way of importing from other mail clients but not from itself!  That would be like being in MS Excel and being able to save in every format but its own (.xls) !!!

Finally, this all doesn't answer my original question which was: How do I export from evolution.  Other people mention being able to Right-click, select Save As..., and choose mbox as the format to save to.  I'm given no such option.  I can Right-click, Save As..., and I'm given no choice as to format.  I can't even use some extention (for example, if .mbox was the extension for mbox format).

All I really want to do is have my emails backed up and saved in some basic format so I can use them with most email clients.  I'm trying to switch from hotmail and downloaded over 1,000 emails yesterday.  If I can't have a secure way to store the data, what is the point of using a non-web email client??

---

### Post by electricshoes on 2006-08-26
Sorry I couldnt be of more help. That is how I did it. I created folders (20 or so), imorted a single file and went through all of my mbox files in the evolution folder and imported 1 at a time. They should look like this.

~/.evolution/mail/local

mailboxname      (this is the mbox file)
mailboxname.ev-summary
mailboxname.ibex.index
mailboxname.ibex.index.data

 It should look like this for each of your folders from evolution.

I looked around for the export in evolution, i can't find it either.

---

### Post by wirewalker on 2007-05-14
Hi There :)

You can drag and drop your mail to a folder of your choise, and drag them back again,
it's not what youre a looking for, but a work around ;)

---

