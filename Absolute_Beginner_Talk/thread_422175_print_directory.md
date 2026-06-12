---
title: "print directory"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by actioncomics on 2007-04-24
i have search for this with no luck.  I know this has to be something easy i am just missing it.  I need to copy the contents of a directory (folder names and file names) to a text file.  for example

/etc/
--X11/
----filename
----filename
--folder/
----folder/
-------filename

something similar to that but does not have to be exactly.  I am just looking for a text file with folders, subfolders, and fiilenames.   everytime i search I only come up with the pwd Print Working Directory command and this is not what i want.  thanks
ac

---

### Post by jhnthn on 2007-04-24
What about  ls * > textfilename.txt

---

### Post by slimdog360 on 2007-04-24
Do you want to do this in a program, python can do it. I can't imagine you would be talking about the ls or dir command.

---

### Post by actioncomics on 2007-04-24
actually i was talking about the ls command.  i can't figure out how to output the results to a text file.  I could do it real easy in windows but can't figure out how to in linux.  if i used the ls command in a terminal and then copied the files i only get the current directory and that would take me forever on hundreds of files and folders.

ac

---

### Post by actioncomics on 2007-04-24
crap i only read the last post and did not see jhnthn post i will try that first.

thanks

---

### Post by actioncomics on 2007-04-24
perfect.  that is exactly what i need.  Just in case anyone is curious why i would need this.  I am in the process of sorting through hundreds of files and folders and this is an easy way for me to take a listing of my computer at home to work and sort through them at lunch.

thanks for the help

---

### Post by bashologist on 2007-04-24
Maybe something like this? It creates html text of directories. It displays just like ls if the text is preformatted.
[INDENT]find /data/folder/archives -type d | sort | while read line; do printf "<h4><a name=\"${line}\">${line}</a></h4>"; ls "$line"; done[/INDENT]

---

### Post by jhnthn on 2007-04-24
Ah I just found this:
```
ls -R | grep ":" | sed -e 's/://' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'
```
It prints a directory structure kind of like pstree

source: [http://www.macosxhints.com/article.php?story=20060209130749352](http://www.macosxhints.com/article.php?story=20060209130749352)

---

### Post by actioncomics on 2007-04-24
both of those suggestions are great.  but i have a question about both.
the html version places the filenames right next to each other making it hard to read in a browser.  any suggestions?

the mac command only displays the folders anyway to get the files to show up to? 

sorry to be such a pain but both of these command are what i need and would like to see which one would work best.

thanks

---

### Post by bashologist on 2007-04-24
> **actioncomics said:**
> both of those suggestions are great.  but i have a question about both.
the html version places the filenames right next to each other making it hard to read in a browser.  any suggestions?

the mac command only displays the folders anyway to get the files to show up to? 

sorry to be such a pain but both of these command are what i need and would like to see which one would work best.

thanks

For the html you can wrap it in a <pre> tag or use a stylesheet like this:
```
body {
    white-space: pre;
}
```
That should make it a little more readable. More information here: [http://www.w3schools.com/css/pr_text_white-space.asp](http://www.w3schools.com/css/pr_text_white-space.asp)

---

### Post by jhnthn on 2007-04-24
> **actioncomics said:**
> both of those suggestions are great.  but i have a question about both.
the html version places the filenames right next to each other making it hard to read in a browser.  any suggestions?

the mac command only displays the folders anyway to get the files to show up to? 

sorry to be such a pain but both of these command are what i need and would like to see which one would work best.

thanks
Sorry I don't really understand the sed part at all. If you remove the grep part of the pipe it'll print the files, but it messes up the structure when it's printed. Maybe someone more knowledgable with sed can help.

---

### Post by Spam Banjo on 2007-08-22
> **jhnthn said:**
> What about  ls * > textfilename.txt

Thanks dude... helped me too!

Yet another example of something I had to download dirty-free/shareware for when back when I was using windows... God it feels like such a long time ago!

I heart Ubuntu!!!
Shibby! :lolflag:

---

### Post by faction918 on 2008-05-17
ls > file.txt

---

