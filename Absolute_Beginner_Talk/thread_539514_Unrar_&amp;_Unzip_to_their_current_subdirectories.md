---
title: "Unrar &amp; Unzip to their current subdirectories"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2007-08-31
I have a folder /books filled with subfolders containing zipped or rar'ed ebooks. I'm trying to figure out how to unzip and unrar them in their current folders. All I've managed to do is unzip them into the main /books directory. I can't find a toggle to recursively unzip and leave files in those subfolders.

Any help would be appreciated.

---

### Post by mohnkern on 2007-08-31
The -d parameter lets you specify what directory to put the file in.

aka  unzip <filename> -d <directory>


it might be possible to write a perl script (or something else) that would go through and use this to unzip them like you like.

---

### Post by bashologist on 2007-08-31
Before you try the last command type the following so you know what it'll be unzipping:
```
find . -iname '*.zip'
```

Here it'll unzip into their subdirectories as you requested:
```
find . -iname '*.zip' -execdir unzip {} \;
```

---

### Post by taddy_porter on 2007-09-01
Works like a charm. Thanks. I was able to unrar and unzip all those files then RM them.

I'm having trouble with converting my .LIT files in batch though.

Using LIBPRS500 I need to get it in lit2lrf NEWNAME.LRF format. I'm not sure how to make that happen.

I want to take mybook.lit and run lit2lrf mybook.lrf on it in the  subdirectories. Any idea how to do that?

---

### Post by taddy_porter on 2007-09-02
> **taddy_porter said:**
> Works like a charm. Thanks. I was able to unrar and unzip all those files then RM them.

I'm having trouble with converting my .LIT files in batch though.

Using LIBPRS500 I need to get it in lit2lrf NEWNAME.LRF format. I'm not sure how to make that happen.

I want to take mybook.lit and run lit2lrf mybook.lrf on it in the  subdirectories. Any idea how to do that?

Nevermind. Moronic moment. I didn't realize how long it took to convert lit files.

---

### Post by rascalli on 2007-10-07
how does this work for rar files ?

as  : 

find . -iname '*.rar' -execdir unrar {} \;

does not seme to work ;-/

---

### Post by taddy_porter on 2007-10-07
find . -iname '*.rar' -execdir unrar e {} \;


You need the e after unrar

---

### Post by SpiritIsReality on 2007-10-07
> **taddy_porter said:**
> find . -iname '*.rar' -execdir unrar e {} \;


You need the e after unrar
taddy_porter ... ftw ... thankyou so much for responding.

comin from here [http://ubuntuforums.org/showthread.php?t=569452](http://ubuntuforums.org/showthread.php?t=569452)

buds

---

### Post by rascalli on 2007-10-07
Thank you very much ...it works  great <3  !!!

one last question , how can I delete all the unwanted files (rar, sfv , nfo) ? as all I need is the avi.

---

### Post by SpiritIsReality on 2007-10-07
howdy
!!! 
I don't know it well enough to be giving advice, but I know somebody, not personally, well I've been to his place, and you can too ...
[www.linuxcommand.org]("http://www.linuxcommand.org") 
use the .bashrc and don't worry about not finding the other one whatever it was, Things Change . all the best ...
after linuxcommand I wandered over to [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
Omnios has a library for command line here oh, it's in the Important Links sticky at the Absolute Beginners under the heading 10 Terminal Commands.
buds

---

### Post by taddy_porter on 2007-10-08
find . -iname '*.zip' -execdir rm {} \;


Change the ZIP to whatever other files you want as you go along. Be careful what directory you're in at the time you run the command.

---

### Post by Poromenos on 2008-02-16
> **bashologist said:**
> Before you try the last command type the following so you know what it'll be unzipping:
```
find . -iname '*.zip'
```

Here it'll unzip into their subdirectories as you requested:
```
find . -iname '*.zip' -execdir unzip {} \;
```

Thanks for that, I've been searching for a command to do it for a long time. Unfortunately, I haven't been able to thank you through the forum because I didn't find the "thanks" link, so here it is!

---

### Post by nicho12 on 2008-03-08
just for reference incase anyone else struggles,
if you have multiple rars of a file in folders in subdirectories you will find that this command will try tyo extract every one of them individually.
you can stop this for example if the files are in part01.rar and part02.rar etc. by:
```

find . -iname '*.part01.rar' -execdir unrar e {} \;

```
then it will only attempt to extract the first rar file which should extract the whole thing.

---

### Post by MarshyTheKid on 2008-03-08
I have a folder with a bunch of other folders inside, all with a couple zips each. In each zipped folder is a rar.
I used ```
find . -iname '*.zip' -execdir unzip {} \;
``` to extract the zips in each folder. I switched it to ```
find . -iname '*.r*' -execdir unrar e {} \;
```  to unrar each rar file(.rar, .r00, .r01, etc), but the problem is it just extracts them all to the main folder. How can I change it to unrar to the folder the rar file is in?

---

### Post by nicho12 on 2008-03-09
when you unrar one file that is split into parts like xxx.rar xxx.r00 xxx.r01 then it unrars the whole lot
you only need to 
```

unrar e xxx.rar

```
and it will unrar the rest into that folder
the code 'e' after unrar specifies you unrar the file(s) into the folder they are in, if you want to unrar them to the full file path there will be a similar code just type ```
unrar --help
``` to see all the available options

---

