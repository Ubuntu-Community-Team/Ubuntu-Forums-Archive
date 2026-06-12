---
title: "Is there any archive manager utility that can make spawn compressed files?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by rev_b on 2006-11-18
I still haven't figured out how to compress like 80 Mb of data in 10Mb spawned zip/rar/whatever files. Any ideas?

Thanks.

---

### Post by rev_b on 2006-11-18
Ok, I found a good solution in [http://ubuntuforums.org/showthread.php?t=206978&highlight=rar+multiple](http://ubuntuforums.org/showthread.php?t=206978&highlight=rar+multiple)

But is there a GUI interface that allows to do the same thing as on the command line?

---

### Post by unbuntu kid on 2006-11-18
If you are looking for GUI's, you have come to the wrong OS.  Linux is all about terminal.  Windows is for "GUI"ing

---

### Post by rev_b on 2006-11-18
> **unbuntu kid said:**
> If you are looking for GUI's, you have come to the wrong OS.  Linux is all about terminal.  Windows is for "GUI"ing

Unfortunatly it's people like you who prevent Linux from reaching the masses, not all people find "all about terminal" that L33T. So I suppose you're posting this from Lynx, right?

Thank you for nothing.

---

### Post by ComplexNumber on 2006-11-18
> **unbuntu kid said:**
> If you are looking for GUI's, you have come to the wrong OS.  Linux is all about terminal.  Windows is for "GUI"ing
whats up, kid? still using a linux distro from 1996 or what? time to fast forward to 2006 (you've got 10 years of linux advancements to catch up on).

---

### Post by beameup on 2006-11-18
rev_b WinRar is still command line only for Linux. I haven't found any other archiving software with a GUI that creates split archives in Ubuntu.

---

### Post by DigitalAxis on 2006-11-18
I don't know of any...  Most systems on Linux (file-roller, Xarchive, ark) seem to be... well, shells that simply call the command-line programs.  This would be fine, if the GUI frontend was designed to offer up all the functionality of the command line programs, but most of them aren't...

Spanned compressed archives are unfortunately only handled on the command line; my best suggestion is to open two terminals; get the man-page in one and construct your command in the other.

The next step would be to make an alias to whatever command you come up with, so you can call it whenever you need to (slightly less painful- write once, use frequently).  
I once had to use commandline rar to break up a DVD iso into files I could transfer on my 1 GB flash drive (no DVD burner on my laptop), and I just wrote it once and saved it somewhere.

I can help you with the alias if you want.


Obviously the best solution would be to file a bug about this with the file-roller people (or whoever makes the default archiver of your favorite DE)

---

### Post by rev_b on 2006-11-18
Thanks beameup and DigitalAxis. Ok, command line it is then. I don't have to do it too often, but sometimes it gets handy to e-mail bigger files in 10Mb attchements.

So it's $rar a -v<size in kB>k <filename>.rar <filename>

About the bug report, well, it's not actually a bug but more lacking a feature, right?

---

### Post by ComplexNumber on 2006-11-18
doesn't mattter

---

### Post by adamkane on 2006-11-18
!

---

### Post by DigitalAxis on 2006-11-18
Bugzilla is used for both, usually.  Some (most? I've only used Launchpad and something on Sourceforge lately) have tags for "FEATURE REQUEST".

As for your command, that looks right.  You will need to experiment to find the right volume size, because I'm not sure how much size is added when you send it via email (formatting for transmission is something like 20% overhead).

I would also consider the -m*n* option, where *n* is 0 to 5.  When I made my DVDs, well, iso files don't compress well and take FOREVER so I set it to -m0.  On the other hand, the RAR format is very good at compressing most data, so you might want to use -m5 and -mdg (better prediction) for maximum compression and minimum resultant filesize... depending on what kind of files you're sending.

As for automation, looking at your command it may be a lot trickier than I thought- you might need shell scripting (mega voodoo)

```

#! /bin/bash
# The preceding line tells the computer that this file is a script.

# This prints out some usage information if there was bad input.
# (ie, less than two arguments)
# $# is the number of arguments specified on the command line.
# [ is actually a program that runs our test (for 'less than')

if ([ "$#" -lt 2 ])
then
        echo "rarpart.sh:  Creates multipart RARchives"
        echo "Usage: rarpart.sh foobar.rar file1 [file1 file2...]"
        exit
fi

# This script will have to be run as 'rarpart ARCHIVENAME file1 file2 file3...'

# The first argument ($1) is the name we want our compressed archive to
# have when we're all done.

ARCHIVENAME=$1

# Now we 'shift' the argument list over ($2 becomes $1, $1 is deleted) so I
# can use $* to refer to all the _files_

shift 1

# now we run the command.
# $* refers to all the arguments specified on the command line
# $ARCHIVENAME is where we saved the name of the archive to create
# (to _use_ variables they have to have $ in front of their name)
#
# 8532k is my estimate of the maximum size of a file (minus padding that
# can be transmitted through email- feel free to correct)

rar a -v8532k -m5 -mdg $ARCHIVENAME $*

```

uh... you'll need to rename the attached file to rarpart.sh to get it to work as described (it's a copy of the above code in a file)
I do tend to go overboard with commenting, but that's because I like to be able to come back to a program knowing exactly why I did what I did.

---

### Post by rev_b on 2006-11-18
That's awesome, thank you. It works just fine. I just edited the last line to 
rar a -v10500k -m5 -mdg $ARCHIVENAME $*

As it's more or less the max file size Gmail takes as an atachment. With 2 Gb to spare, I can as well put some files online to access them where needed.

---

### Post by beameup on 2006-11-20
After further review I found a couple of front ends for WinRAR.

[http://www.win-rar.com/index.php?id=24&kb=1&kb_article_id=78](http://www.win-rar.com/index.php?id=24&kb=1&kb_article_id=78)

[I]Is there a graphical user interface available for Linux?  

We don't have a GUI for Linux ourselves. However, Gnochive is a Linux frontend for RAR. You can download it here. [http://gnochive.sourceforge.net/download.html](http://gnochive.sourceforge.net/download.html)

Also another project named LinRAR is in the beta state. You can download it here. [http://linrar.sourceforge.net/about.php](http://linrar.sourceforge.net/about.php)[/I]

I haven't used them myself yet. No deb packages that I can see.

---

### Post by steve.horsley on 2006-11-20
Once you have a script that can process a list of files you give it and produce the output you want, you can create a launcher for that script, and then just drag/drop a set of files from nautilus to the launcher icon.

---

