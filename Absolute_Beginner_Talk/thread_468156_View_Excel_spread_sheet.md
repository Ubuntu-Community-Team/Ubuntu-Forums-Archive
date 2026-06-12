---
title: "View Excel spread sheet"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by BirdZerk on 2007-06-08
I am having difficulty viewing an Excel spread sheet in OO spread sheet, it views in Excel with no problems.  The cells with errors are actually lookups, I assume since Excel can display the data correctly that there is information in the spread sheet that OO can't use.  Is there a plugin that will enable OO spreadsheet to display the data the way Excel does?  The link to the spread sheet is

[http://www.budgerigarassociation.com/azbs_spring_2007_show_report_revised5_19_07.xls](http://www.budgerigarassociation.com/azbs_spring_2007_show_report_revised5_19_07.xls)

---

### Post by srt4play on 2007-06-08
It's not going to work because those cells are trying to lookup data from another excel file referenced by a Windows filesystem address, but I think you know that much already.  I'm afraid there's not a way to make it display properly.

---

### Post by nickpaton on 2007-06-08
The way to sort this out is to move all the associated Excel file links into your home folder (or whereever you store stuff in Ubuntu).

You will then have to change the file association part of each cell from Doc and settings to the new association and drag the cell formulae down accordingly.

Alternatively if you want to be able to read the spreadsheed in either Windows or Ubuntu, create a new FAT32 partition and put all your files in there.

Then you will be able to sort out the associations and be able to read the spreadsheet from either Ubuntu or Windows.

HTH

---

### Post by BirdZerk on 2007-06-08
What I don't understand is when my friend views that same file with Excel, she can see all the data, so does that mean the spreadsheet file has the data in it and only an Excel program can fill in the cells and other spreadsheet programs can't see the data within the spreadsheet file?

I just tried the file in Gnumeric and it opened it with all of the data, so why won't OO?

---

### Post by nickpaton on 2007-06-09
I don't know why OO won't open the linked work books, but can only assume that it cannot read into your Doc & Settings folder in Windows.

I haven't got anything suitable to experiment with right now on my Windows XP partition, but will see if I can find something I've done in the past, or create something and get back to you in the next few days.

In the meantime if you need this desparately in Ubuntu, I would think that creating a new FAT32 partition and moving all the workbooks there and changing the links will give you a common access between your ubunutu and Windows spreadsheet programs.

Sorry - best I can come up with at the moment!

---

### Post by nickpaton on 2007-06-09
Been experimenting......

The basic reason why you cannot link to the Windows workbooks is due to the unspecified disc partition to where the folders are located in Windows.

When you simply open the OO linked spreadsheet it typically will look like: 

> ='file:///Documents and Settings.......etc etc

However, what OO is looking for is the disc name as well as the folder path, typically as follows:

> ='file:///media/hda1/Documents and Settings........etc etc

Where hda1 is the Windows partition as seen by Ubuntu.

There is however one "small" problem and that is that you cannot change the file path within each cell in OO because the cells are Read Only, so that isn't going to work!

I then tried the same in Gnumeric, and yes it does link to other Windows workbooks, BUT...again if you make any changes and try to save, again you will find that the files are Read Only, so again you are no further forward.
In other words it seems that you can read only but not make adjustments and save them in Gnumeric.

I then moved the two workbooks into my FAT32 partition and ran it with Excel and OO and again I needed to change the path name as above, but this time I was able to add stuff and save it OK.

Moving to Gnumeric I found that it would not link properly to other workbooks and I did try making a couple of new workbooks and linking between them.  Unfortunately it seems that it cannot do this, so I would say that this is not suitable for you.

Sorry for the length of this, but HTH

Nick

---

### Post by BirdZerk on 2007-06-09
I don't think I made myself clear, the file was created by someone else in the club and posted to the net for everyone to see.  Excel and Gnumeric will display the file correctly but OO spreadsheet won't.  I have no access to any original info, just the file posted to the net.  If it was just me, I would just use Gnumeric, but I have started getting friends to use OO instead MSO and I am starting to hear about things like this file not opening correctly.  Any help would be greatful.

---

### Post by nickpaton on 2007-06-10
Thanks for the clarification on that, but my explanation above still holds true unfortunately.

Oo needs to have the full file path INCLUDING specifying the disc drive partition because it needs to know where to go to, to see the links.

I proved this almost 100% myself in my own experiments last night.  

Simply going *='file:///Documents and Settings.......etc etc* is not enough.

Oo needs to have something along the lines of *='file:///**[SIZE="3"]media/hda1[/SIZE]**/Documents and Settings........etc etc * to point it to the partition.

My conclusion is that unfortunately it appears not to be practical in this case to use Oo, and maybe you will have to ask others to use Gnumeric.

(BTW why not simply suggest this to your other people - it's there in Synaptic and it should be simple enough for them to download.)

As a by the by, it does appear from my experimentation last night too with Gnumeric, that if you attempt to write a full spreadsheet program which  requires links to other worksheets, that Gnu does not have the linking facility written in (try it!).

The only suggestion I can make is that you ask the person who created the original program to create a new FAT32 partition and to put the whole program with all the linked workbooks there, and to modify the cell links accordingly in the final page.
Maybe as an experiment you could ask them to set up a V simple two workbook program with links between them in a new FAT32 partition to see if that works.

I have a little FTP site but not an actual server at home so it would not be a lot of help to set something up for us to experiment with, but I do understand what you're saying and it looks like Oo simply won't do it for you.

---

### Post by forestpixie on 2007-06-10
I've been watching this thread - haven't had any suggestions though.

But out of interest I have just installed Gnumeric to open the spreadsheet, as has been said it will open there and cells can be read. 

However now when I open it in oo - the cells can be read!

If anyone knows how to check difference between my oo and theirs I am only too happy to help.

I will say at the outset that I have uninstalled the oo which comes with Ubuntu and reinstalled the version from the oo site.

:)

---

### Post by forestpixie on 2007-06-10
Sorry - opening in oo doesn't work - as all have said. Gnumeric got added as default app - I didn't notice until just now.

---

