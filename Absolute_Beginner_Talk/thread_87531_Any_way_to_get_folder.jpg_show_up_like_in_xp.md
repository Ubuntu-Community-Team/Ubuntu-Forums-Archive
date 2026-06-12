---
title: "Any way to get folder.jpg show up like in xp?"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by cafevincent on 2005-11-08
Is there any way to get folders viewed as thumbnails genereted from a picture inside (like folder.jpg in windows xp)? 93% of all folders in my computer have a picture and now when I turned into linux the folder trees look so crummy. From now on I'd have to select my music/movie/book/game/whatever by title only, not by cover+title.

---

### Post by patrick295767 on 2005-11-08
rox-filer 
  ([http://rox.sourceforge.net/phpwiki/static.html)](http://rox.sourceforge.net/phpwiki/static.html)).
    
---------------
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)

---

### Post by patrick295767 on 2005-11-08
[http://rox.sourceforge.net/phpwiki/static.html](http://rox.sourceforge.net/phpwiki/static.html)

---

### Post by HJThis on 2005-11-08
Hello,cafevincent

Well i maybe way off here new at this but did you try & see if
opening say one of your disk then goto Edit > Backgrounds & Emblems
is any help to you at all.

Best of luck :D

---

### Post by cafevincent on 2005-11-08
Neither of these suggestions help on my problem. Rox supports thumbnails for picture files but I don't see any thumbnails for folders in any of the numerous screenshots.

---

### Post by kalin on 2005-11-08
You can use any picture for a folder's icon (righclick -> Properties -> Select Custom icon).

I'm not aware of a way to do that automatically though. A simple bash script could do the job for multiple folders.

---

### Post by cafevincent on 2005-11-08
[QUOTE=kalin]You can use any picture for a folder's icon (righclick -> Properties -> Select Custom icon).

I'm not aware of a way to do that automatically though. A simple bash script could do the job for multiple folders.[/QUOTE]

Thanks! Making them all manually is an unimaginable job but I bet I'll be making scripts some time so this pretty much settles it! After all, the only rush I have is to get rid of Windows permanently :)

If anyone has ideas for this sort of script please give me some pointers. I can't really use them until I learn to script but I will keep all help stashed until I need it.

---

### Post by ow50 on 2005-11-08
[QUOTE=cafevincent]If anyone has ideas for this sort of script please give me some pointers. I can't really use them until I learn to script but I will keep all help stashed until I need it.[/QUOTE]
The folder pictures are defined in XML files in ~/.nautilus/metafiles. You need to edit the parent folder's XML file.

Here's an example entry in "file:%2F%2F%2Fhome%2Fosmo%2FDocuments.xml"
```
<file name="pictures" timestamp="1131474679" custom_icon="file:///home/osmo/Documents/pictures/folder.jpg"/>
```
You should probably use some programming language that has some existing functions to help in editing XML files, e.g. Python or Perl.

I set the previews for all my 171 music folders manually. :D

---

### Post by NinjitsuStylee on 2006-07-30
How did you manage to do this?  I tried to manually enter data and for some reason the changes aren't reflected in nautilus.  Can you give us some more insight?

---

