---
title: "What are the equivalent file extensions?"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by DawnDisciple on 2007-11-08
Thanks to this forum I am slowly battling my way though some of the basics of Ubuntu.  What I would reallly find helpful at this stage is to know what the equivalent file extensions from windows such as..

.exe, .rar, .doc, .wmf, .cfg

This way I get a clue how to treat certain files in Ubuntu

I know there are many more but it's early in the morning here.:)

---

### Post by jordanmthomas on 2007-11-08
First off, in Linux file extensions mean absolutely nothing.

That said, here's a semi-correct answer to your question:
.exe -->  generally, nothing...just a name of a program.  For example, the "exe" for firefox is just firefox, nothing more.
.rar -->  You can use .rars or .zips in Linux.  Typically, though, you'll find .tar.gz or .tar.bz2
.doc -->  OpenOffice will open and save .doc files.  Its native format, however is .odt.
.wmf -->  I *think* this is a clip-art like format, no?  If so, you should be able to view them in Linux, but the "new" equivalent would probably be SVG.  Look into Inkscape for editing SVGs, but most any graphics program can view them.
.cfg -->  Usually, (not always) .cfg files in Linux would be .conf files or .rc files.  You can find tons of them in /etc

Anyway, it's important to remember that Linux doesn't discriminate between a binary file and a text file.  Either can be executed, which leads to great scripting abilities.

---

### Post by Maestro23 on 2007-11-08
Just to follow up on JT's post.

[http://www.debianhelp.co.uk/fileext.htm](http://www.debianhelp.co.uk/fileext.htm)

---

### Post by DawnDisciple on 2007-11-08
> **Maestro23 said:**
> Just to follow up on JT's post.

[http://www.debianhelp.co.uk/fileext.htm](http://www.debianhelp.co.uk/fileext.htm)

A-har, that's what I was looking for, last night I got a game with the .rpm extension, took me ages to figure out what to do with it, finally got the archive manager thingy to recognize it and unzipped the file only to end up with a directory called 'usr' so I spent another hour trying to figure out what to do with this directory, no joy I'm afraid and the folder is still stuck on my desk top, unresolved

---

### Post by jordanmthomas on 2007-11-08
rpms are for redhat-based systems, and Ubuntu is Debian-based.

There is a program called alien that converts rpms to be useful for you if you care to look it up.

Ideally, though, you should either find a .deb (debian package) for it or look in Synaptic.  Odds are it's out there somewhere.  What's it an rpm for?

**edit**
just noticed the page Maestro linked to says exactly what I did.  woops!

---

### Post by DawnDisciple on 2007-11-08
Hehe, while I'm here I would like to finish the job, what do I do with the usr folder that I fanally unzipped from .rpm the usr folder has sub folders, its the game scorched3d.

---

### Post by jordanmthomas on 2007-11-08
Well, you could just do this:
```
sudo cp -r usr /
```
**BUT DON'T DO THIS**
The reason is this:  taking things that have been compiled for another system can be flaky sometimes.  Reason 2:  you can install scorched3d compiled just for Ubuntu by installing it from the repositories.

To do this, just enable the universe repository in Synaptic.  (System --> Administration --> Synaptic Package Manager)
(Sorry, but I don't use Ubuntu so I can't tell you the EXACT steps you need to follow, but I believe it's pretty straightforward in the settings once you get in Synaptic.

After you do this, reload the packages in Synaptic and then search for scorched3d and install it.

---

### Post by DawnDisciple on 2007-11-08
I was playing with the Synaptic thingy last night, I don't know what it is or what its for but I will attempt to follow your instructions.

---

### Post by jordanmthomas on 2007-11-08
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
If you're up to it, this is a good read for new users (even has instructions for installing things from .rpms  :)  )

---

### Post by DawnDisciple on 2007-11-08
> **jordanmthomas said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
If you're up to it, this is a good read for new users (even has instructions for installing things from .rpms  :)  )

This is good, I must be warming up to this somehow because I actually started to understand some of the stuff on that link.  Its a lot of hard work and sometimes I feel like throwing my PC out of the window, but if the work starts to pay off then its all worth it.

---

### Post by kvonb on 2007-11-08
-

---

### Post by jordanmthomas on 2007-11-08
A Real Man Just Runs As Root Always
:)

**edit**
The forums don't let you use all caps.  :confused:

---

### Post by DawnDisciple on 2007-11-08
What is the extention .run   I find this on a lot of files

---

### Post by jordanmthomas on 2007-11-08
Usually, a .run is a program that extracts stuff from itself and uses it to run.
Perhaps in Windows you have come across a file that when you run it, it unzips itself and then runs the installer?

To use a .run file, you typically need to run it from a terminal.
1.  make it executable (you must do this because otherwise Linux will not allow it to be run)
     you can either right click on it go to properties and then check the box that makes it executable or in a terminal type (assuming file is on your Desktop)
```
chmod +x ~/Desktop/somefile.run
```
2.  run it
      sometimes, you can just double click it (not usually though)
      always, you can run it in a terminal
      ```
~/Desktop/somefile.run
```
      if it complains about permissions, you'll need to run it with sudo
      ```
sudo ~/Desktop/somefile.run
```
      for more on sudo and what it is, see this:  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Hopefully that wasn't too confusing...sorry if it was.
For the record, .bin files are just the same (unless they're cd images)

---

### Post by DawnDisciple on 2007-11-08
> **jordanmthomas said:**
> Usually, a .run is a program that extracts stuff from itself and uses it to run.
Perhaps in Windows you have come across a file that when you run it, it unzips itself and then runs the installer?
Hopefully that wasn't too confusing...sorry if it was.
For the record, .bin files are just the same (unless they're cd images)

I know exactly the type of files that you are talking about, thanks for making it so easy to get to understand.  The .bin file info is valuable, that would have got me really confused.

---

### Post by Paulmd on 2007-11-08
> **jordanmthomas said:**
> First off, in Linux file extensions mean absolutely nothing.

That said, here's a semi-correct answer to your question:
.exe -->  generally, nothing...just a name of a program.  For example, the "exe" for firefox is just firefox, nothing more.
.rar -->  You can use .rars or .zips in Linux.  Typically, though, you'll find .tar.gz or .tar.bz2
.doc -->  OpenOffice will open and save .doc files.  Its native format, however is .odt.
.wmf -->  I *think* this is a clip-art like format, no?  If so, you should be able to view them in Linux, but the "new" equivalent would probably be SVG.  Look into Inkscape for editing SVGs, but most any graphics program can view them.
.cfg -->  Usually, (not always) .cfg files in Linux would be .conf files or .rc files.  You can find tons of them in /etc

Anyway, it's important to remember that Linux doesn't discriminate between a binary file and a text file.  Either can be executed, which leads to great scripting abilities.


WMF= Windows Metafile. It's generally for vector-based graphics, but can contain raster images as well. This is useful in clipart, as mentioned, where scaling an image is common. Raster images often don't look good when scaled up. 

Similar formats are CGM, and WPG. You won't see many CGMs around anymore, they harken from the days of the 286, and probably earlier.

---

