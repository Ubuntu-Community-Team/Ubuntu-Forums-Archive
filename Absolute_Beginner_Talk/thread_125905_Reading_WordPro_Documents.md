---
title: "Reading WordPro Documents"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Pudwud on 2006-02-05
If I receive a document in Lotus WordPro format is there any way to read it?

Thanks.

---

### Post by Stinger on 2006-02-07
Yes I would think so , Open Office has support for the Lotus word pro format
( *.lwp ).:D 

I use the Open document format myself ( *.odt ).

---

### Post by Pudwud on 2006-02-08
I have not been able to get it to read them properly.  Have you had any luck?

Thanks.

---

### Post by Stinger on 2006-02-13
Well the wordpro support in Open office seems to be , lets just say problematic.
I found a [guide at the Open office webpage]("http://user-faq.openoffice.org/new-faq/faqcompatibility/faqgeneralcompatibilityoffice/49.html") , it's a bit outdated but I think it's still valid.

Goes like this.
1. install Wine (windows emulator)

2. download [wordpro viewer for windows]("http://www-10.lotus.com/ldd/ssforum.nsf/47f741a63df5db1e85256d6b0054cb26/85f2ca8d41a4acd9852570f2006fc1cb?OpenDocument") from [here]("ftp://ftp.lotus.com/pub/lotusweb/product/smartsuite/") , look for the Kvlotus.exe file.

3. Extract the Kvlotus.exe file using wine

4. Install the viewer using the SETUP.EXE file from the KVLOTUS folder , most likely located in your home-folder.

5. Open your document using the Kvlotus viewer and copy the contend to Open office for futher processing.

Phew ! :p

---

### Post by Pudwud on 2006-02-26
Details appreciated on how to carry out this step:

4. Install the viewer using the SETUP.EXE file from the KVLOTUS folder, most likely located in your home-folder.

Thanks.

---

### Post by Stinger on 2006-02-26
I did see your PM , but aswering here would be better , maybe more user can benefit that way.

I assume you have [installed and setup wine.]("https://wiki.ubuntu.com/Wine?highlight=%28wine%29")

Next goto your downloaded Kvlotus.exe file ( if you haven't changed Firefox defaults , it will be right on your Desktop) , right click the file select properties ,goto the "open with" tab , click on "add" , in the "add program" window goto the bottom and click on the "userdefined command" option and type "wine" (whithout the quotes) and click the "add" button.
Now wine will execute all your *.exe files just by clicking them twice.

Doubleclick on the Kvlotus.exe file , winzip selfextractor appers.
Click on "unzip" should produce a KVLOTUS folder in your home directory.
Enter the KVLOTUS directory and look for the SETUP.EXE file.
Doubleclick the SETUP.EXE file to launch the installer.
When you are approx. 97% through the installer freezes a bit (give it some time) and the wine-filebrowser will appear a couple of times , just close it every time (give it the neccesary time to close itself, don't force it)
The finish dialog appers (click on finish)
Thats it ! :rolleyes: 

Now try to launch the viewer.
When you are in your home directory select show > hidden files.
Goto the ".wine/drive_c/Program files/Verity/Kvlotus" folder and doubleclick the KVLOTUS.EXE file.
Bingo ! KeyView for Lotus will now apper.

If you want to we can make a nice menu entry for the KeyViewer too ?

Coffee break !!
:mrgreen: :mrgreen: :mrgreen:

---

### Post by Pudwud on 2006-02-26
See attachment.  Stuck here.

Thanks.

---

### Post by Stinger on 2006-02-27
I have no trouble with Installshield , strange ?

What wine version do you have ?

I have succesfully installed the KeyViewer on two machines using two versions of wine , 0.97 and version 0.98 , it never stopped at the Installshield.

It could be your wine setup (winecfg) too I know you need to be carefull when you setup the drives , the drive type need to be right.

---

### Post by Pudwud on 2006-02-28
0.9.8

The drives seemed to be the problem and I had it working for a while and then I seemed to have done something that rendered it inoperative.  Is there a way to uninstall and reinstall it?  Also what did you mean by “If you want to we can make a nice menu entry for the KeyViewer too”? 

Thanks.

---

### Post by Pudwud on 2006-02-28
It seems that if I close the program as a given user I cannot restart it but I can install it as another user.

---

### Post by Qrk on 2006-02-28
It could be because you don't have some of the services the wordpro viewer depends on installed.

Try winetools (from the repositories) to install these services automatically. From memory (I no longer use wine) it installs installshield, the windows explorer/internet explorer (which many programs need) and other important apps. 

get it with a:

```
sudo apt-get install winetools
```

Note that it probably will complain about not having the correct version of wine installed. For instance, it may want wine 9.0, but you have wine 9.8. As far as I can tell, this won't be a problem.

---

### Post by Stinger on 2006-03-01
[QUOTE=Pudwud]It seems that if I close the program as a given user I cannot restart it but I can install it as another user.[/QUOTE]

To understand this you'll need to know that wine makes a new ".wine" directory and setup for each user.
So if you need a fresh uncorrupted wine just rename the ".wine" folder to ".wineBU" and run "winecfg" again.
If you don't need anything from your previous wine install , you can delete the ".wineBU" folder.

Don't bother with un-installing and installing wine again , you don't need to.
_________________________________________________________________

[QUOTE=Qrk]
Try winetools [/QUOTE]

It's not recommeded to use winetools anymore , please use winecfg instead , it's part of the wine package.
_________________________________________________________________

I'm currently doing som test with the KeyViewer and an Lotus Smart Suite 96 installation.
I'll be back ASAP.
:-k

---

### Post by Stinger on 2006-03-01
I'm getting closer , here is your sample and a couple of other samples.
The last two samples are from the KeyViewers own readme which also is a *.lwp  file , click help > Readme in the toolbar.
You might also have noticed that I use the "Page Layout" view for correct displaying of the document.

---

### Post by Pudwud on 2006-03-02
How do you:

"rename the ".wine" folder to ".wineBU""?

I do not know how to get into the list of files.

Thanks again.

---

### Post by Stinger on 2006-03-02
when you are in your home directory in the file browser , select View > show hidden files , then right click your ".wine" folder to rename it.

Better yet , I'll show you.

---

### Post by Pudwud on 2006-03-03
Two additional questions:

Is there something magical about “BU” or if I have to rename the ".wine" folder again can I use any letters?

How do I make a nice menu entry for KeyView?

Thanks again.

---

### Post by Stinger on 2006-03-04
[QUOTE=Pudwud]
Is there something magical about “BU” or if I have to rename the ".wine" folder again can I use any letters?
[/QUOTE]

Nothing magical about BU , just short for backup , you can use any letters you like.

[QUOTE=Pudwud]
How do I make a nice menu entry for KeyView?
[/QUOTE]

If you follow the [Wine user guide]("http://www.winehq.com/site/docs/wineusr-guide/index")

[4.1. Basic usage: applications and control panel applets]("http://www.winehq.com/site/docs/wineusr-guide/running#BASIC-USAGE")

You can see that you can launch an app. by typing something like
```
wine "c:\program files\appname\appname.exe"
```
OK , let's try with the KeyViewer
```
wine "c:\program files\verity\kvlotus\kvlotus.exe"
```
(the quotes are needed this time).

The menu entry are made like this , goto Applications > System Tools > Applications Menu Editor , select "Office" and press "New entry" at the bottom of the window.
Entry Editor window appers .
I made an entry like this:

Name: Lotus KeyVeiwer

Comment: Viewer for Wordpro documents

Command: wine "c:\program files\verity\kvlotus\kvlotus.exe"

Now you can pick an icon by clicking the "No Icon" button.

Piece of cake.
:rolleyes: :rolleyes:

---

### Post by Pudwud on 2006-03-06
Thank you very much - it works like a charm.  One last question:

Is there a way to set it up so that when I doubleclick on a WordPro document that KeyView automatically opens it.

Thanks again.

---

### Post by Stinger on 2006-03-07
I tried to make a small shell script to do the trick but the only thing it does is to open the KeyViewer without the document.:-k 

So the answer to your question , > Is there a way to set it up so that when I doubleclick on a WordPro document that KeyView automatically opens it. , must be no , I'm afraid.
Or I don't know howto.:???: 
You have to launch the KeyViewer first and open your "*.lwp" document with the KeyViewer.:-|

---

### Post by Pudwud on 2006-03-07
Thanks for trying.

---

