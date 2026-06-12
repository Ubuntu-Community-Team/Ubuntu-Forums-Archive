---
title: "openoffice question"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by benx009 on 2007-07-20
is there a way to modify openoffice so that when you click "Save," it saves your file to its default location (something like /home/itsme/Documents/myfile.odt) as well as some backup location (like /media/hda1/Documents and Settings/itsme/My Documents/myfile.odt)?  i really hate having to nagivate through my hard drive to save in two different locations since backing up my essays is standard for me... i mean, sometimes i even save to three locations (like an external flash drive) if i really don't want to lose a file.

if there is no way to do this, then that would be a pretty good addition for the future openoffice releases, yah???

---

### Post by nichipet on 2007-07-21
Take a look at Tools:Options:Load/Save:General

There is a checkbox in there for "Always create backup copy"

I found this OpenOffice.org 2.2. If you don't see the option and you're not using 2.2, upgrade first.

I don't see anything about putting the backup in a different location, so you may need to test it and see where it saves. Personally, I've never really run across anyone who wants backups in a location other than the default.

---

### Post by sancho panza on 2007-07-21
****Removed by poster****

---

### Post by benx009 on 2007-07-21
> **nichipet said:**
> Take a look at Tools:Options:Load/Save:General

There is a checkbox in there for "Always create backup copy"

I found this OpenOffice.org 2.2. If you don't see the option and you're not using 2.2, upgrade first.

I don't see anything about putting the backup in a different location, so you may need to test it and see where it saves. Personally, I've never really run across anyone who wants backups in a location other than the default.

sweet!  you **can** change where openoffice saves the backup!  just do  Tools - Options - OpenOffice.org - Paths, and change where you want the backup to be saved.  sweet!

the only thing i don't like is that openoffice saves the backup w/ the extension *.BAK:(.  i can see why you would need this if you were saving the file in the same directory as the original, but i don't do that, so all it does it make my life more complicated....

---

### Post by nichipet on 2007-07-21
A shell script could be written to convert them and then cron could run it every day, for example. I can't write a script for it until I get home tonight, but I think searching Google for "shell scripting foreach" (without the quotes) should get you started. And I'm sure mv or cp will be in there. Basically just get a list of files in the directory that end with .BAK and then tell it to move (mv) each of them to filename.odt will do it. Hope this helps.

---

### Post by benx009 on 2007-07-21
thanks for the suggestion *nichipet*, but i know no code lol....  i follow what you are saying though.  what would make the script even better though is right after it creates the .odt files, it then deletes the unnecessary .bak files.  i seriously need to learn how to code lol....

---

### Post by nichipet on 2007-07-22
I searched the Web a little and found that there is a built-in command in Linux that will do what you want. Here's what to do, assuming your backup directory is found in /home/myname/backups (change it of course to where you keep them) and they all end with .BAK. Just copy and paste the lines in the Code boxes, one at a time (I don't mean to oversimplify, but since you are new to coding, I don't want to take any chances.)
Read all of this post before you start, it may save you some trouble.

I'll use vi as an editor, since it's the one I know best, these instructions will work for vi/vim.

First open Terminal, you can just type Alt-F2, type Terminal, hit Enter, and it should open. Then:

```
cd /home/myname/backups
vi removebak.sh
i
```

Enter after each of the first two lines, but not the i. The i puts you into insert mode. The next part can be a straight copy and paste.

```
#!/bin/sh
rename 's/\.BAK$//' *.BAK
```

Use the Edit menu for Paste in Terminal, I can't remember the keyboard shortcut for it and I'm in a different program right now.

Next hit the Esc key, then type ZZ (must be capital letters). You're just about done.

```
chmod 700 /home/myname/backups/removebak.sh
```

You can test the script, assuming there are some files in the directory that end with .BAK by typing ./removebak.sh (that's period, slash, removebak.sh)

If all of this works, I can then help you with setting up cron to run the script as often as you want (I'd recommend once per day). If you run into any problems, reply here with exactly what you typed and what Terminal responded with.

---

### Post by benx009 on 2007-07-22
ok, well, i couldn't really follow your intructions w/ vi (when i tried to paste, it just dumbed in some weird symbols, not what i wanted to paste; also had problems scrolling lol) so i did everything you said w/ gedit instead, and the script did exactly what it was supposed to do.  however, since linux is case sensitive, i had to change your code to rename ".bak" files, not ".BAK" files, since openoffice creates backups as ".bak" not ".BAK" (srry, that was my mistake, i totally forgot about linux's case sentivity complex for a while lol).  the script worked then, but then i noticed that the file that remains is extension-less (for example, Myfile.bak renames to just Myfile).  so is there a way to have the script rename the extension-less files back to ".odt" (I know I'm asking way too much, but I seriously appreciate all your help:D )

btw, sometimes I save a file as .doc for compatibility reasons (need I explain?)  so I was wondering, is there a way to have the script discern ".odt" .bak files from ".doc" .bak files despite the fact that they both end in the same ".bak" extension.  (example, since i made that too confusing to uderstand:  what if there was a "Helloworld.bak" file and a "Myfile.bak" file both in /media/hdb6/Backups, but "Helloworld.bak" was originally a .doc file and Myfile.bak was originally .odt?  Is it possible to have a script rename Helloworld.bak to Helloworld.doc while simultaneously renaming Myfile.bak to Myfile.odt?)  It's probably not possible, huh?

---

### Post by benx009 on 2007-07-22
oh yeah, one more question: do I really have to give the script root permissions?  couldn't I just make it executable and leave it at that?  tia a lot!

---

### Post by nichipet on 2007-07-22
I'll answer the last question first. It's not root permissions, chmod 700 does make it executable, while still allowing you to read and write the file.

To add the extension change

```
rename 's/\.BAK$//' *.BAK
```

to

```
rename 's/\.bak$/.odt/' *.bak
```

To break down the code a little, rename uses sed to process the files. The s at the beginning means substitute, the \.bak$ means to look for .bak at the end of a line, and the .odt tells it what to change the .bak to. The final *.bak is what the script is searching for, you could change it to TEMP* and it would only change files that start with TEMP and change .bak extensions to .odt.

I don't think there is a way to have the script figure out which files are .odt and which are .doc. There may be a way to handle that from within OpenOffice.org. I'll look at OpenOffice.org and see if I can find something.

---

### Post by nichipet on 2007-07-22
OK, I found a way to do it, I think. I'll work on modifying the script, it will probably take about an hour. I have today off, so it's not a problem to work on this.

---

### Post by benx009 on 2007-07-22
thanks so much! changing the script did the trick for me.  ok now i see why the file got root permissions: it seems that everything i put in my /media/hdb6 folder (where i have my backups folder stored; it's a fat32 partition) gets root permissions, w/ the owner being "root" and the group being "plugdev."  well, i don't think this matters though because i can still edit stuff on that drive w/o root permissions so no worries:)  i just have to remember that when i configure the script to autostart w/ cron (which you will probably have to help me out with too:) ), i should have the script run *after* all the partitions on the disk have been mounted.  should be no problem.

btw, if you can find a way to get the ".doc" thing to work, it would be greatly appreciated, though if it's too much hassle don't worry about it. once again, thanks!!!

---

### Post by nichipet on 2007-07-22
Alright, it all works. :)

This script will go through all of the .bak files in the directory the script is found in, check if the file is OOo (OpenOffice.org) or MS Word, and then change the extension correctly. It will only work with OOo and MS Word files, if you need it to change extensions for other file types, it can be done but will need some tweaking (not hard to adjust). (And it's possible that it will move files that are not OOo or MS Word, so try to keep only those two types in there unless we tweak the script first.)

Just copy all of the Code box into the removebak.sh file, completely replacing what you had there previously. I saved two files in OOo, one as .odt  and one as MS Word, changed both extensions to .bak, and then tested the script. It moved the OOo file to .odt and the MS Word file to .doc.

Let me know if there are any problems. It should be fairly well commented, explaining what the lines do. If it all works correctly, we can move on to cron to have it run on a regular basis.

```
#!/bin/sh
# Author: nichipet
# Created: July 22, 2007
# Shell script to move backup files created in OOo to .odt and .doc, depending on MIME type
# This will handle all of the .bak files in the same directory as this script
# at one time and move all of them to the correct extension, assuming all
# of them are OOo or MS Word files
#
echo "Starting moving process..."; echo " "
# First, tell it to handle each file with the .bak extension separately
for i in `ls *.bak`
  do
# Find the MIME type of the file
    thefile=`/usr/bin/file $i`
# Next create a variable of the last four characters of the MIME type output, should be
# 'data' or 'ment' (from Document)
    newfile=`echo $thefile | awk '{ print substr( $0, length($0) - 3, length($0) ) }'`
# Test if the file is .odt, a MIME type of 'data'
    if [ $newfile = "data" ]
# If it is, move it to an extension of .odt
      then
        mv $i `basename $i .bak`.odt
        echo "Moved $i to .odt"
        echo " "
    fi
# Now test if the file is .doc, a MIME type of Microsoft Office Document
    if [ $newfile = "ment" ]
# If it is, move it to an extension of .doc
      then
        mv $i `basename $i .bak`.doc
        echo "Moved $i to .doc"
        echo " "
    fi
  done
  echo "All finished"; echo " "

```

---

### Post by benx009 on 2007-07-22
hmm... i did exactly as you said and ran the script.  i used three files as test subjects, two of which were .odt files and the other a .doc file.  but when i ran the script, only one .bak file got converted to the .odt it's supposed to be.  so two other files, one .odt and one .doc, did not get converted.  the .odt file that did get converted was really small compared to the other two (6.4KB, against the other 12.5KB .odt file and the 224KB .doc file).  hmmm.... does the script only work for small files?  btw, none of the files contained any pictures or charts or anything (if that matters).  just all out text

p.s.  .odt and .doc are all i ever use in openoffice:); for .txt files i just stick to gedit

---

### Post by benx009 on 2007-07-22
ok, i just tried the script w/ a small .doc file and it worked:)

so is this a filesize-related issue?

---

### Post by benx009 on 2007-07-22
thanks for all your help by the way!!!

---

### Post by nichipet on 2007-07-22
OK, I copied a free book from Project Gutenberg into OOo, saved it as odt and as doc, ran the script, and it moved both of them perfectly in just a second or two. Here is the output it gave me:

```
Starting moving process...

Moved hildadoc.bak to .doc

Moved hildaodt.bak to .odt

All finished


```

What output did it give you when it did not work? This script only moves files from one name to another, it does not handle the content of the file so the size (or text versus graphics) should not matter.

---

### Post by benx009 on 2007-07-22
don't you hate when the answer to something is right in front you?  i spent like an hour diagnosing what the problem was while it was staring me in the face all along.  i was totally on the wrong track w/ the filesize thing.  the only reason that some files didn't convert while others did is because of spaces in the file name.  in other words, your script is perfect:)  but is there a way to make it account for spaces in the file name? (i always name my files w/ spaces) however, your script works flawlessly, i tried it with 20 of my files, .odt and .doc alike, with file sizes ranging from 6.2KB to 4.4MB and **all** of them converted!!!!!!!! (well, yeah, after removing the spaces from the filenames of some of them lol)  anyways, thanks again *nichipet* for all your help, i will come to you whenever i need something coded!!!!!!!!!!!!!!!

---

### Post by nichipet on 2007-07-22
I'll see what I can do about spaces in the names.

And you're quite welcome.

---

### Post by nichipet on 2007-07-24
Considering they are backups, do you mind if the spaces in their names are changed to underscores? If you don't mind the underscores, I can incorporate that into the script to handle files with spaces, I think.

---

### Post by benx009 on 2007-07-24
of course not lol... 
now about having the script run on startup w/ cron....:confused:

---

### Post by nichipet on 2007-07-24
From a prompt:

```
sudo apt-get install kcron
```

Then open KCron (Alt-F2 for a Run Command window and KCron if nothing else) and follow its instructions. I looked at it, looks fairly intuitive. Let me know if you run into problems with KCron. There is a way to do it from a command line, but KCron is easier to use.

---

### Post by benx009 on 2007-07-24
well, i already had kcron installed (must have auto-installed when i got kubuntu-desktop) so i decided to create a new task.  i browsed to the location of the script, and had it set to run at 16:00 (4 pm) everyday.  but when 16:00 came along, nothing happened.  i mean, i'm sure the task must have ran, but the bak files i had stored in /media/hdb6/Backups did not convert:confused:  to be safe, i even clicked "run now" in kcron, but nothing happened.  so then i closed kcron, opened up a terminal, and typed in kcron from there so i could see some output.  here's what i got: 

```
carboxyl@FeistySys:~$ kcron
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
no crontab for carboxyl
Starting moving process...
 
ls: *.bak: No such file or directory
All finished
```

those first errors don't matter, kcron opened up anyway.  however, notice the last two lines.  i got that error when i tried "Run Now" in kcron.  yet i know that i have some .bak files (yes, w/o spaces:) ) in the same directory the script is located in.  what's going on?:confused:

---

### Post by benx009 on 2007-07-24
lol, my hypothesis was correct:)  if i *cd* to the directory where i have the script stored, and then run kcron from there, the script runs w/o flaw:

```
carboxyl@FeistySys:~$ cd /media/hdb6/B*
carboxyl@FeistySys:/media/hdb6/Backups$ kcron
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Starting moving process...
 
Moved HelloWorld.bak to .odt
 
Moved What_a_World.bak to .odt
 
All finished
```

that's all good, but how do i have the script run the way it should w/o having to browse to my /media/hdb6/Backups directory?

---

### Post by nichipet on 2007-07-24
I'm at work right now, but I'll change my setup at home to mimic yours and see if I can find the answer. Off-hand, did you put the full path of the script in kcron? If you just entered it as removebak.sh, it might be trying to run it from your home directory or from the / directory.

---

### Post by benx009 on 2007-07-24
no, i put the full path alright: /media/hdb6/Backups/removebak.sh
all i really want is for the script to start when i startup ubuntu.  nothing more...

btw thanks for all the help! much appreciated!!!

---

### Post by Martin on 2007-07-24
A simple way would be to add to your your Sessions. On the main menu go System then Preferences then Sessions. Once in the Sesions dialog - Choose the Startup Programs tab choose Add and away you go.
Nice work nichipet, I might use this myself. Cheers

---

### Post by nichipet on 2007-07-24
Yeah, if you just want it on startup, go with Sessions and put it in there. If you're using KDE/Kubuntu, put a link to the script in the directory ~/.kde/Autostart

Thanks, Martin. Still have some work to do on it, though.

---

### Post by nichipet on 2007-07-28
I think I know how to handle the spaces, but I'll have to wait until I'm home from work to test it. I'll update the script and post the changes if it works.

---

### Post by benx009 on 2007-07-30
okay that would be appreciated, i am finding it rather annoying to name all of my openoffice files w/ underscores:)

---

### Post by nichipet on 2007-07-31
Sorry it took so long to get this done, but now I have it working with spaces. If a file has no spaces in its name, it will give an error:

> mv: `test1.bak' and `test1.bak' are the same file

which is quite harmless. I can try to find a way to have it not do that, but it's almost 2am, I want some sleep. :)

Here is the code, just copy and paste this and replace what you had before.

```

#!/bin/bash
# Author: nichipet
#
# Version history:
# 1.1 - 7/31/07 - Added conversion of spaces to underscores
# 1.0 - 7/22/07
#
# Shell script to move backup files created in OOo to .odt and .doc, depending on MIME type
# This will handle all of the .bak files in the same directory as this script at one time
# and move all of them to the correct extension, assuming all of them are OOo or MS Word files

echo "Starting moving process..."; echo " "

# First, tell it to change the spaces to underscores

for i in *.bak
  do
    mv "$i" `echo $i | tr ' ' '_'`
  done

# Next find the MIME type of the file

for i in *.bak
  do
    thefile=`/usr/bin/file $i`

# Now create a variable of the last four characters of the MIME type output, should
# be 'data' or 'ment' (from Document)

    newfile=`echo $thefile | awk '{ print substr( $0, length($0) - 3, length($0) ) }'`

# Test if the file is .odt, a MIME type of 'data'

    if [ $newfile = "data" ]

# If it is, move it to an extension of .odt

      then
        mv $i `basename $i .bak`.odt
        echo "Moved $i to .odt"
        echo " "
    fi

# Now test if the file is .doc, a MIME type of Microsoft Office Document

    if [ $newfile = "ment" ]

# If it is, move it to an extension of .doc

      then
        mv $i `basename $i .bak`.doc
        echo "Moved $i to .doc"
        echo " "
    fi
  done
echo "All finished"; echo " "

```

This should work. I tested it with two OOo files and two MS Word files, all created in OpenOffice Writer. One of each had no spaces and one of each had a space. I did not test it with multiple spaces in a file name, but I don't see any reason that would not work. There is a line in the script to replace all spaces with underscores.

---

### Post by benx009 on 2007-07-31
yes, the script works!!!  you are the ultimate coding monster, *nichipet*!!!  

however, believe it or not, i still haven't been able to get the script to start up w/ my system.  adding it to "sessions" in the system menu did not work:?  i was thinking about creating a symbolic link in my /bin folder (not the best place to put it, but i have no where else;)) that points to the actual script, and then seeing if the "sessions" will allow the script to operate from there.

---

### Post by benx009 on 2007-07-31
hmmm... did not work....  

it seems that scripts that aren't on the same partition as ubuntu will be complicated to start up...

---

### Post by nichipet on 2007-07-31
OK, I found a fix for startup as well. I'll assume you're in GNOME, if you're in KDE, I can adjust the instructions for that too. (Sorry if you mentioned before which environment you use, I don't recall now.)

You'll need a new file in the same directory, it's small and easy. I called mine runremovebak.sh so I know what it does just from the name.

```
!#/bin/sh
cd /path/to/backups
./removebak.sh
```

It has to cd first to the correct directory, I think that may be what kept it from working before.

Do this in a terminal from the same directory:

```

chmod 755 runremovebak.sh
```

Then go into System:Preferences:Sessions (I think that's where it is, I'm in KDE right now) and add /path/to/runremovebak.sh to your Startup tab.

All of that should work (I tested it with a user in GNOME and it renamed the files). Of course let me know if it doesn't, we'll get it figured out.

---

### Post by benx009 on 2007-07-31
yes, doing it your way worked for me!  i use gnome, so that made your directions all the more easy to follow.  once again, thanks for all your help, i think i [finally] have the backups thing the way i want it!!!  i know i already said this before, but i will come to you if i ever need anything coded!  

<humbly bows down before an almighty leader:)>

---

### Post by nichipet on 2007-07-31
You are quite welcome, I enjoyed the challenge of figuring it all out. Feel free to ask me if you need another shell script, I'll enjoy writing that one too. :)

---

