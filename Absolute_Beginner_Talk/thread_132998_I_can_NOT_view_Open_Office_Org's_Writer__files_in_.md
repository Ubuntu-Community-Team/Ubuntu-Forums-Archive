---
title: "I can NOT view Open Office Org's Writer  files in MS Word"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-19
Hello All !!!

I would like to be able to view Open Office Org's "Writer" files in MS Word.

Basically, I have created a "Writer" File & have used the Font "Nimbus Roman No9 L".

When I try to open that file in MS Word, I see some "chinese" characters & the File can NOT be Read !!!

How can I install the "Nimbus Roman No9 L" Font into the Windows OS, so that I am able to View Open Office Org's "Writer" files in MS Word?

... and where are the Fonts located in the Ubuntu OS, to go & copy that Font?

I performed a "Places\Search for Files" & found NO "Nimbus Roman No9 L.ttf" File...

Thanks for the help.

---

### Post by nalmeth on 2006-02-19
hmm, sorry I can't offer you anything definitave, but try to resave your openoffice document as a .doc?

---

### Post by NoWhereMan on 2006-02-19
I don't know what menu, but there should be an option to embed ttf fonts into the document file

---

### Post by dvarsam on 2006-02-19
What will change if I rename the File as ".doc"?

MS Word opens the File - it is just UNREADABLE !

The problem is with the Font - it is NOT in readable format !

Can somebody Help?

Now regarding the option to embed .ttf fonts into the document file, then....

... will that file be readable in MS Word - or will it make things worse?

Please Help !!!

---

### Post by xtacocorex on 2006-02-19
MS Word can't open Open Office documents yet as they haven't implimented the OASIS document format.

You need to save the document written in OOWriter as a .doc for it to work with MS Word.

As for installing the font, locate it on your system (I don't know the file name of it) and then create a copy of it on a floppy or usbkey and move it over to Windows. If I remember correctly, if you right click on a font, you can choose to install it, otherwise copy it to C:\Windows\Fonts\

---

### Post by cwaldbieser on 2006-02-19
[QUOTE=dvarsam]What will change if I rename the File as ".doc"?

MS Word opens the File - it is just UNREADABLE !

The problem is with the Font - it is NOT in readable format !

Can somebody Help?

Now regarding the option to embed .ttf fonts into the document file, then....

... will that file be readable in MS Word - or will it make things worse?

Please Help !!![/QUOTE]

You can't just rename the file to ".doc".  You need to save it as a ".doc" in Open Office using the "File -> Save As..." menu option.  That way, when Open Office writes the file, it writes it in a way that MS Office can understand.

---

### Post by Cesium on 2006-02-19
[QUOTE=dvarsam]What will change if I rename the File as ".doc"?
[/QUOTE]

As others stated, go "save as" and then select .doc for the type of file.  It will then open in Word.  The formatting may be slightly adjusted by Word.  Otherwise everything else should be fairly similar.

---

### Post by 15index on 2006-02-19
HI,

I am also new so I hope this helps. Go to the Synoptic Package Manager and click on Search. Type in fonts. Read the list and you will see a download for msttcorefonts. Download it and when you start Open Office, it should show some of the more common Word fonts- Ariel, Courier New, Times New Roman, etc. Use one of these and you should have few problems. If you change the document to a .doc with one of these fonts, it will work without any problems, but try it with the .0dt extension to see if it will work.

---

### Post by NoWhereMan on 2006-02-20
Please guys, remember!
extension != format ;)

---

### Post by dvarsam on 2006-02-20
I have created a Tutorial on this, but somebody has to tell the Forum's Administrator. to go & fix the "Customization Tips & Tricks" Folder in this Forum.

The "Administrators" MUST make some categorization of stuff !!!

Everything is a mess in there !

There must be some subfolders like (for example):

"The Basics", "Working with Programs", "Password Problems", "Networking", "Security Conserns", "Printing", etc etc.

Can somebody send some e-mails to the Forums "Administration" to fix this & I am willing (I promise you!) to post a whole bunch of stuff to help beginners (like me) to learn Ubuntu the quickest possible way.

Thanks.

---

### Post by jjf on 2006-02-20
So you got it fixed, dvarsam?

Just in case, I'll summarize: There are two hurdles to overcome.  

First, Word does not read .odt files.  To fix that, within OpenOffice, choose **Save As** and save as file type **Microsoft Word Document**.  If you know that most of the docs you create will be opened by other users in Word, you can set this (or Rich Text Format) as the default.

Second, Windows does not have Linux fonts.  Best fix for this is to install the msttcorefonts (or whatever it's called) package and use Times New Roman and Arial within your OpenOffice docs.

---

### Post by dvarsam on 2006-02-20
[QUOTE=jjf]So you got it fixed, dvarsam?

... to install the msttcorefonts (or whatever it's called) package and use Times New Roman and Arial within your OpenOffice docs....[/QUOTE]

YES, yes I fixed it.

I did not install the "msttcorefonts" pachage though.

But I want to share my knowledge with ALL the Beginners !

So, can somebody send some mails to the "Administration" to make some kind of Categorization to the "How To's Section"?

... And then, hopefully, when ALL can read the "Basics" section, or the "Office" section, they can setup their Ubuntu PC's quicker & start making more serious posts here...

... cause if we keep on this way, then everybody keeps consuming their energy answering (sometimes) TOO easy questions...

Thanks.

---

