---
title: "amd64 and 86"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by stanley82 on 2007-09-07
Hi Guys and Gals,

     I installed amd64 ubuntu version edgy then updated to Fissty Fawn.  Was having difficulties so I did a dual boot thing and now have the 32 and 64 versions of ubuntu.  Also my 80gig was partitioned into two 40gig drives.  I have decided to be happy with the AMD64.

      Question, how do I get rid of the 32 bit os and restore back to an 80gig drive?  If I have to reload the Fiesty CD that&#347; oky but I would like to export my evolution e-mail boxes so that I can archive them.

     Also in evolution the F1 help/contents does nothing.

     Any help would be great before I go it on my own.

                          Regards Ian.

---

### Post by John.Michael.Kane on 2007-09-08
Regarding removal of the 32 bit os you should be able to resize/delete the unneeded partitions using gparted which is on the ubuntu livecd. 

Should this not work last resort method is a clean reinstall.

As for exporting your evo mail you can try one of the method below.

To export messages from a Evolution folder:

1) Open the folder in Evolution.

2) Select Edit | Select All from the menu.

3) Now select File | Save As... from the menu.

4) Choose the location and file name where you want to save your emails.
Note: You can give the file a .mbx extension so you will know that it is a mail box file. 
5) Click OK.

Option two.
To backup your mail, addresses and appointments from Evolution, to import them later. All you should have to backup is the ¨mail¨ directory you will find in /home/yournamehere/.evolution.

Next you can either import the files with the import-function or just replace the ¨mail¨ directory.

Using the import function you have to browse to the ¨inbox¨ files you will find in /mail/local/inbox for your mail, any subdirectories you made will also be there.

Hope this helps.

---

