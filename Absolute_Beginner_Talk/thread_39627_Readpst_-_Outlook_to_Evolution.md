---
title: "Readpst - Outlook to Evolution"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by Weta on 2005-06-05
Hello

Previous threads have led me to the application Readpst, which can convert Outlook emails to Evolution.  I have therefore installed Readpst using Package Manager.  So far so good...

How do I run the Readpst application to open a Mail.zip file that contains a Outlook.pst file of my old Outlook emails?  

I have tried using Run Application, but I don't know what command line to use, and whether to use the command with "Run with File".  I tried a few command lines based on the Installed File names available under the Package Manager, but no luck...

Thanks

---

### Post by Gtaylor on 2005-06-05
Greetings,

I assume you're trying to extract the .zip so your converter can get to the file? If this is the case, you *should* be able to right click and go to Extract or Actions and say 'Extract Here', but it's been so long that I ran Gnome that I may be entirely wrong (assuming you're running Ubuntu and not Kubuntu).

If you want to do this through the command line, move your .zip file to your home directory and type the following commands:
```

sudo apt-get install unzip
unzip myzip.zip

```
Of course replacing myzip.zip with the filename you want. But you really should be able to do this with right clicks or double-clicking (or single-clicking depending on how you're set up) and finding the Extract button on your archiver.

Let me know if this helps!

---

### Post by Weta on 2005-06-07
Hello 

Thank you.  When I double click on the Mail.zip file it reveals three files - one of which is called Outlook.pst, which I assume is the target file (i.e. of old Outlook emails).  

My question - I think - is how to run the Readpst application?  I assumed that Run Application was the place to do this, but I don't know what to put in the empty box at the top of the Run Application window.  I also don't know whether  to use the "Run with file" option.  

The Readpst application shows up as "installed" in the Package Manager.  I asume that I need to select one of the installed files in the box in Run Application, and maybe select "Run with file" using Outlook.pst.  But maybe not... My attempts so far have been unsuccessful.

Sorry for not being clearer before.  I would be good to recover the old Outlook mail items.  Thank you.

---

### Post by Gtaylor on 2005-06-07
I was just looking at this and without seeing how you're setup and what kind of stuff you're running, it'd be hard for me to walk you through this since I've never used it myself. Assuming you're running Evolution, you should be able to import Outlook mails via some format. I don't run it myself but I thought I moved my windows emails over somehow when I made the switch.

Has anyone done this recently?

---

### Post by C_nemo on 2005-06-07
[QUOTE=Weta]Hello 

Thank you.  When I double click on the Mail.zip file it reveals three files - one of which is called Outlook.pst, which I assume is the target file (i.e. of old Outlook emails).  

My question - I think - is how to run the Readpst application?  I assumed that Run Application was the place to do this, but I don't know what to put in the empty box at the top of the Run Application window.  I also don't know whether  to use the "Run with file" option.  

The Readpst application shows up as "installed" in the Package Manager.  I asume that I need to select one of the installed files in the box in Run Application, and maybe select "Run with file" using Outlook.pst.  But maybe not... My attempts so far have been unsuccessful.

Sorry for not being clearer before.  I would be good to recover the old Outlook mail items.  Thank you.[/QUOTE]


Hi,
haven't imported outlook files into evolution, but i have impoerted mbox files, which is the mailbox format readpst produces. You will need to convert the .pst files in Mail.Zip to mbox files and then import them into evolution.

The following is a step-by-step guide without actually using readpst, but with the man page. I take it from your post that the real problem is using the command line to run readpst to convert the files. 

1) unzip Mail.zip into your home directory.
result---> you should now have 3 files with the .pst extension in your home directory

2) open up a terminal. Go to "Applications->System Tools->Terminal"
result---> Evil looking white box, "just like DOS" for all the MS veterans


Do the following steps for each .pst file:

3) convert the pst file by running readpst from the terminal using the following command. Change NAME.pst to the name of the pst file you wish to import nad remove the quotes.
```

"readpst -r NAME.pst"

```

result---> folders in home directory named like in Outlook

4) import the .mbox files in the newly created folders with evolution. "File->Import" and select "single file". Select the file and let Evolution do its thing. you may have to repeat this step a few times depending on how many subfolders with mbox files was created by readpst



End result (should be): 
your old outlook emails in the "On This Computer" Inbox


Hope this helps

---

### Post by SpaceWolf on 2005-06-08
[QUOTE=C_nemo]Hi,
haven't imported outlook files into evolution, but i have impoerted mbox files, which is the mailbox format readpst produces. You will need to convert the .pst files in Mail.Zip to mbox files and then import them into evolution.

The following is a step-by-step guide without actually using readpst, but with the man page. I take it from your post that the real problem is using the command line to run readpst to convert the files. 

1) unzip Mail.zip into your home directory.
result---> you should now have 3 files with the .pst extension in your home directory

2) open up a terminal. Go to "Applications->System Tools->Terminal"
result---> Evil looking white box, "just like DOS" for all the MS veterans


Do the following steps for each .pst file:

3) convert the pst file by running readpst from the terminal using the following command. Change NAME.pst to the name of the pst file you wish to import nad remove the quotes.
```

"readpst -r NAME.pst"

```

result---> folders in home directory named like in Outlook

4) import the .mbox files in the newly created folders with evolution. "File->Import" and select "single file". Select the file and let Evolution do its thing. you may have to repeat this step a few times depending on how many subfolders with mbox files was created by readpst



End result (should be): 
your old outlook emails in the "On This Computer" Inbox


Hope this helps[/QUOTE]
 hello,

I am also trying to convert Outlook to Evolution.  I've installed the package and have everything running.  The problem is the output.  When I use the -r, I don't get anything, it just runs and there are no converted files.  If use the command 'readpst outlook.pst' I get a bunch of text files.  What am I missing?  I'm not sure how to get the .mbox files to import into Evolution.

Thanks!

---

### Post by matthew on 2005-06-09
I just completed this task...but not by using readpst.

Here's what I did that got me the same end result you are seeking:

First I installed the Mozilla suite on my windows partition. It is able to import all data from Outlook's pst files.

Then I could easily import Mozilla's data, which is saved in mbox format files, into Evolution.

Take a look here for more details: [http://www.ubuntuforums.org/showthread.php?t=40086](http://www.ubuntuforums.org/showthread.php?t=40086)

---

### Post by Weta on 2005-06-09
Hello

Thank you all for your advice.  I only have Ubuntu/Linux software on our PC, but it is supposed to include a back-up copy of the hard drive from our old PC.  

I am however begining to wonder whether the .pst files that I am looking for weren't backed-up  (no worries - I still have the hard drive).  This is because the only relevant .pst file I have is labeled as a "Program" type of file.  Nonetheless I tried running Readpst [as per instructions - thanks] against it, and got the following message:

debug_fp is NULL
cannot open PST file.  Error

I think that I need to check with the person who backed-up the old hard disk onto the new system that the relevant .pst files were indeed copied.  Once I have then I think that your combined advice will enable me to crack this, now that I know how to run the application (and, if that fails, to use the Mozilla solution).

Thanks again for your help.

---

### Post by C_nemo on 2005-06-09
Hi,
I dont thing mailbox files has the .mbox extension (I was alittel bit lazy when i cooked up the howto). They are just plain text files with your emails inside, no ".mbox" extension just a lot of text.

When you run readpst and get a bunch of text files could it be that the "bunch of files" is emails or mbox files? just wodering. You can read about readpst by typing:

```

man readpst

```

In the terminal, it will bring up a description of the program and what options it support. Unfortunatlyt i have no pst files to try this against.

---

### Post by TranceWarp on 2008-03-18
I just tried running readpst with Outlook 2007 PST files.  It can't read them. :(

---

### Post by scramasax on 2008-03-18
> **SpaceWolf said:**
> I am also trying to convert Outlook to Evolution.  I've installed the package and have everything running.  The problem is the output.  When I use the -r, I don't get anything, it just runs and there are no converted files.  If use the command 'readpst outlook.pst' I get a bunch of text files.  What am I missing?  I'm not sure how to get the .mbox files to import into Evolution.

As i read that man page you need that -r option on there to get mbox files out.  Here's the man page online:

[http://alioth.debian.org/docman/view.php/30390/47/readpst.1.html](http://alioth.debian.org/docman/view.php/30390/47/readpst.1.html)

You'll see there's other options.  One will give you KMail format, for example.  That could be maildir, since KMail uses that by default these days, or it could be some variant of mbox that KMail prefers.  the point is that the options matter.  What you get if you don't use an option at all I don't know.

On top of it all, your .pst file could be corrupt.  Or it might be some version of .pst that the program doesn't handle -- I think Microsoft has changed the format before now.

But it seems there's a forum for Readpst, so you might try asking for help there:

[http://alioth.debian.org/forum/?group_id=30390](http://alioth.debian.org/forum/?group_id=30390)

---

