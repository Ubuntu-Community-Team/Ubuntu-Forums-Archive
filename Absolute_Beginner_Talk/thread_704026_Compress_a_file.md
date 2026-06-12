---
title: "Compress a file"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-02-21
With a quick search I found a few ways to compress a folder using terminal commands.  Is there a simple way to use GUI?  I've right-clicked on the folder, chose archive, then choose a compressed format like .zip and it works but the file is the exact same size:confused:  Where can I get the options to select the compression ratio?

---

### Post by PeterJS on 2008-02-21
What kind of archive did you use? Vanilla tar archives aren't compressed which is why they're usually combined with gzip or bzip2.

---

### Post by cartisdm on 2008-02-21
> **PeterJS said:**
> What kind of archive did you use? Vanilla tar archives aren't compressed which is why they're usually combined with gzip or bzip2.

I'm not quite sure what you mean.  What format am I trying to convert to? Or what program am I using to compress it?

I want to convert it to .zip so I can email it to my mom and she can simply open it without much hassle.  As for the program I'm just using "archive manager"

---

### Post by PeterJS on 2008-02-21
Zip should be compressed all on it's own. You might try putting all the files you want to compress in a seperate folder, and compressing that from nautilus by right clicking on the folder and selecting create archive, and then from the drop down box choose zip. See if that works.

---

### Post by TheBoat on 2008-02-21
It is easier to just use the command line type:```
zip *newfilename oldfilename*
```
where newfilename is the name of the zip file you are creating (file.zip) and oldfilename is the name of the file you are zipping (file.txt)

---

### Post by cartisdm on 2008-02-21
> **TheBoat said:**
> It is easier to just use the command line type:```
zip *newfilename oldfilename*
```
where newfilename is the name of the zip file you are creating (file.zip) and oldfilename is the name of the file you are zipping (file.txt)

For some reason it stays the same size if I right click and choose archive then .zip.  However, using zip newname oldname worked great.  Weird, but thanks!


Edit: Nevermind, it only zipped the folder that's why.  How can I include the contents of the folder as well?

```
dan@dan:~/Desktop$ zip oldname My_fish!
  adding: My_fish!/ (stored 0%)
dan@dan:~/Desktop$ 

```

---

### Post by osx424242 on 2008-02-22
Try
```
zip myfish.zip My_fish\!/*
```
Note the backslash ('\') character before the exclamation character, to escape it. Without it, you'd get an error like:
```
$ zip myfish.zip My_fish!/*
bash: !/*: event not found
$
```
Adding "/*" after the directory name tells zip to include all the files inside that directory.

edit: what kind of file are you trying to compress?  Zipping it up may not be able to decrease the file size, if it's already in a compressed binary format.

---

### Post by asmoore82 on 2008-02-22
right-click on the MenuBar ("Apps/Places/System") and click "Edit Menus;"
Click on "Accessories" on the "Tree View" in the left pane;
the very first item in the right pane should be "Archive Manager," make sure it is checked.

Now, you can launch the Archive Manager from the Menu "Applications -> Accessories -> Archive Manager"
When creating a new archive, the best overall format for speed and compatibility[COLOR="Blue"]*[/COLOR]
would be *.tar.gz; the best format for size and compression ratio would be *.tar.bz2

[COLOR="Blue"]*[/COLOR]Gzipped Tarballs are easily usable on all 3 major platforms:
1. Linux; obviously
2. Mac you can double-click the file to un-zip it; and then double-click the resulting tarball to extract the files;
it's not quite as eloquent as using Linux, but then again, what is :D?
3. Windoze can deal with the files by using WINRar;
it's no more nor less painful than the 100's of other
"I've got to get *X* free of charge proprietary App to make Windows useful" situations

---

### Post by TheBoat on 2008-02-22
Use the -r flag for recursion:```
zip -r *newfilename directoryname*
```

---

### Post by cartisdm on 2008-02-22
> Adding "/*" after the directory name tells zip to include all the files inside that directory.

edit: what kind of file are you trying to compress? Zipping it up may not be able to decrease the file size, if it's already in a compressed binary format.

That included them all, thanks.  It still kept the same file size of 11.3MB.  I'm trying to compress some pics so I can send them easily in email.

> 3. Windoze can deal with the files by using WINRar;
it's no more nor less painful than the 100's of other
"I've got to get X free of charge proprietary App to make Windows useful" situations

Yeah winRAR is simple for most people but try emailing your mom a .RAR file and getting her to open it without complication or a 40 minute phone call....:D

---

### Post by osx424242 on 2008-02-22
Glad it helped.  Pictures probably won't compress much, no.  Another option is to put them up on a photo-sharing website (flickr, picasaweb, etc.).  Mark the pictures as private and send her the direct link.  That way she isn't forced to download them to view the e-mail (if she's still on dialup; finally got my Mom onto broadband a couple months ago :)), but can follow the link whenever it's convenient and depending on where they are hosted she can look at thumbnails first, add comments, etc.

---

