---
title: "Zip / Compressing files"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-15
Ok... I'd like to take a folder and zip / compress some files inside.
In windows you just use a program like WinZip, WinRar, 
or my Favorite IZarc.

I'm just learning Linux so could someone explain a little to
me what these extensions mean.

.tar
.tar.gz

And what program I need to make these files.

thank you.

---

### Post by RomeReactor on 2007-10-15
Hi. [TAR]("http://en.wikipedia.org/wiki/.tar") is an archive format that also keeps permissions and other information on the files. Ubuntu comes with the ability to create and extract TAR files "out of the box", so all you have to do is right-click on the folder you want and select "Create Archive". If you'd rather compress to ZIP, you need to install the **zip** package through Synaptic; an to extract ZIP files, the **unzip** package. To install both using the terminal:
```
 sudo apt-get install zip unzip
```

TAR.GZ and TAR.BZ are compressed TAR files (by GZIP or BZIP), so they are smaller. TAR files are commonly referred to as "Tarballs".

---

### Post by FuturePilot on 2007-10-15
You can use File Roller
Applications>Accessories>Archive Manager
Alternatively you can highlight some files and right click on them and go to Create Archive.

From what I understand .tar is only an archive, not a compressed archive.
.tar.gz is a tar archive compressed with gzip

---

### Post by RomeReactor on 2007-10-15
> **FuturePilot said:**
> From what I understand .tar is only an archive, not a compressed archive.
.tar.gz is a tar archive compressed with gzip

That's right; previous post corrected.

---

### Post by FredB on 2007-10-16
> **Orbital75 said:**
> Ok... I'd like to take a folder and zip / compress some files inside.
In windows you just use a program like WinZip, WinRar, 
or my Favorite IZarc.

I'm just learning Linux so could someone explain a little to
me what these extensions mean.

.tar
.tar.gz

And what program I need to make these files.

thank you.

Use file-roller. You can specify the format you want.

And if you want to learn how to use console. Archiving / compressing tools are installed.

For a tar.gz :

$ tar xvfz name-of-file.tar.gz name-of-directory/

For a tar.bz2 file :

$ tar xvfj name-of-file.tar.bz2 name-of-directory/

Of course, no need to type $. It is just the first caracter of every single line.

---

### Post by Orbital75 on 2007-10-16
Ah..... I see

(  .tar.gz  )
(  .tar.bz  )

Are compressed files, which makes them smaller in size.

( .tar )  is a Archived file. 

So, I totally understand the advantage of Compressing a file....
What is the Advantage of an Archived file?

I've used winzip and other such programs in Windows, does that not
do the same thing but in one step?

Thanks for all the help I am learning a ton from you guys.....
The switch is going much smoother than I thought.

---

### Post by FredB on 2007-10-17
> **Orbital75 said:**
> Ah..... I see

(  .tar.gz  )
(  .tar.bz  )

Are compressed files, which makes them smaller in size.

Indeed.

> ( .tar )  is a Archived file. 

So, I totally understand the advantage of Compressing a file....
What is the Advantage of an Archived file?

It helps making a batch of file, which is simpler and faster to compress.

> I've used winzip and other such programs in Windows, does that not
do the same thing but in one step?

Yes. In a way.

> Thanks for all the help I am learning a ton from you guys.....
The switch is going much smoother than I thought.

Great. But I've got to tell you something : linux is from far simpler than the first time I touched it... My first encounter was back in 1997. My first long time running a distro : 2002.

My "go-to-h*ll-windows" : end of 2004...

---

### Post by Orbital75 on 2007-10-17
Yeah, I agree I bet Linux was far harder in 97.  I started messing around with Linux
back in 2002 with RedHat 8 and 9.  It had a nice Gui which is what most windows users
want. Back then Multimedia was very hard to get up and running. Linux for the adverage
user as a desktop was pretty far off. People like you and I that like to tinker with things
had no real issues messing around and working with it but for a normal user, they just wanted
it to load and work no questions asked. I myself prefer a Gui but if needed I don't mind getting 
my hands dirty in the command line.  I'm a visual learner so the Command Line just seems to abstract to
me.  I do believe however that everyone needs to learn that a folder is in reality a path.  
Example:  The Users personal Home folder  = /Home/My Folder
These are elementary things a user should understand. Early users that began with DOS understand this
concept but the Windows 95 and on generation just don't seem to understand.

---

