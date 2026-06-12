---
title: "tar.gz archive troubles"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-06-19
Ok, I have this tar.gz archive of stuff I've collected over the years, and went to extact it the other day, and it stopped at the ~4.1Gb mark.  The whole thing is ~6.9Gb (when compressed) and I really want to get the other bit out!!!

I've tried gunzip and a few other methods, and so far am considering some of it is not recoverable.  But I was wondering if there is some technique that would allow me to make it skip over "corrupt" files and continue to see if it can get any others?  Also, I've read some stuff about how these archives work ,and baybe since I can get out about 4Gb, if I can somehow chop that off of the archive and let it reset and restart it's stuff that it counts (like blocks or whatever they are) from there, in hopes that it can get the other bit then?

#-oI guess I should have looked more into what tar.gz archives can and can't do, insted of just thinking "it's a linux thing, it'll work fine!" :p

Please help with this!! [-o<

---

### Post by st33med on 2007-06-19
Uhhh... didn't you just post this???

You know you can move a thread to the top of the list by doing a post with anything in it? I would prefer, however, to at least allow an hour or two before trying.

---

### Post by KIAaze on 2007-06-19
Maybe you could extract the files one by one.
It shouldn't be too hard to write a shellscript doing that automatically for you.

Use ```
tar -tf tarfile
``` to list the contents of the tarfile.

If you store the output of it in a list, you can loop over it and extract each file separately.
Additionally, you might store the standard/error outputs in logfiles to check which ones got out correctly and which ones haven't.

I'll post again if I write a script for it. No guarantee of course. ^^

---

### Post by ryanVickers on 2007-06-19
Wow, thanks!  It still got an eror at the end, but it read way more files than it can extract!  I'm still suspicious that it didn't read all of them, but it probably did :p

I've been thinking this to my self for a while now, that even if I couldn't recover it, it would be nice to know what was in it, and now I do!  I suppose if it can do that, then yes, it should be able to pick out certain files.  I't's alot of data, but now looking through it, it's really only one directory that means alot to me, just a bunch of save files from a 3D program I use on windows sometimes.

again, thanks alot for that, and anything yet to come!  If your script works out (assuming you write it) it might not be a bad idea to actually send it to whoever puts stuff in the available packages for ubuntu using synaptic!

---

### Post by KIAaze on 2007-06-19
Oh, and you have to add a "z" for tar.gz files in case you haven't noticed yet:
```
tar -tzf file.tar.gz
tar -tf file.tar

```

To extract one file or folder (it extracts recursively in case of folders):
```
tar -xzvf file.tar.gz filename
tar -xzvf file.tar.gz folder
tar -xvf file.tar filename
tar -xvf file.tar folder

```

It's basically:
x=extract
z=zipped
v=verbosely
f=file
t=? (can be replaced by the more explicit "--list")

See ```
man tar
``` for more.

I think I'll be writing the shellscript quite soon. ;)

---

### Post by ryanVickers on 2007-06-19
WOW!! I got pretty much everything!

I noticed I also have this ~2GB (about ~40Mb over) archive inside, and of course it's corrupt too.  It's not nearly as important, but I would like to know why it seems only about to extract about 250Mb worth of files?!

NOTE TO ALL USERS!!!  tar.gz archives should not be used for anything 2Gb or over!!! :p

---

### Post by KIAaze on 2007-06-20
A bit later than expected, but here it is:

**untar_one_by_one.sh:**
```
#!/bin/bash

# Check if all parameters are present
# If no, exit
if [ $# -ne 1 ]
then
	echo
	echo "usage :"
	echo "$0 tarfile"
	echo
	exit 0 
fi

#delete previous log files eventually
rm out.log >/dev/null 2>&1
rm err.log >/dev/null 2>&1

#start extracting files (empty folders are excluded)
echo "======================"
echo "contents (only files):"
echo "======================"

for f in `tar -tzf $1 | grep -v '\/$'`;
do
	echo "$f"
        tar -xkzvf $1 $f 1>>out.log 2>>err.log        
done

#display log files
echo "========"
echo "out.log:"
echo "========"
cat out.log

echo "========"
echo "err.log:"
echo "========"
cat err.log

```

Note: This script is meant for .tar.gz files, not .tar files.
In case of tar files, remove the "z" option in the tar commands.

I hesitated between extracting everything using the -k option (do not overwrite existing files) and only extracting files.
In the end, I stayed with only extracting files, since using the -k option generates a lot of useless error messages when a file already exists.

The script could probably be improved to also extract empty folders, but do they really matter?

---

### Post by Bluecircle on 2007-06-20
> **ryanVickers said:**
> 

NOTE TO ALL USERS!!!  tar.gz archives should not be used for anything 2Gb or over!!! :p

No, I don't think this is correct at all. I have a 15.6 GB tar.gz file which extracts perfectly.

[http://en.wikipedia.org/wiki/Tar_(file_format](http://en.wikipedia.org/wiki/Tar_(file_format))

"For historical reasons numerical values are encoded in as ASCII text octal numbers, with leading zeroes. The final character is either a null or a space. Thus although there are 12 bytes reserved for storing the file size, only 11 octal digits can be stored. This gives a maximum file size of 8 gigabytes on archived files. To overcome this limitation some versions of tar, including the GNU implementation, support an extension in which the file size is encoded in binary. Additionally, versions of GNU tar from 1999 and before pad the values with space characters instead of zero characters."

---

### Post by ryanVickers on 2007-06-20
> [quote] NOTE TO ALL USERS!!!  tar.gz archives should not be used for anything 2Gb or over!!! :razz:No, I don't think this is correct at all. I have a 15.6 GB tar.gz file which extracts perfectly.[/quote]Interesting, I just saw that somewhere, and it's my personal experience that this is true, but if it's not in some cases, ok, great!  Just a warning to everyone, check this stuff out first! :p

As for the script, it didn't seem to be able to extract anymore than the regular "right-click > Extract here", but that's just this one file.  I think it would probably work just fine on larger archives (like my first one).  Also, it did seem very slow, like each file took as long as extracting the "whole" archive in the built-in fashion!

---

### Post by ryanVickers on 2007-06-21
Oh, while we're on the topic of scripts, I'm brand new to this, like started when you showed me yours :) and I would like some help with this:
```

#!/bin/bash 
COUNTER=0
while [ $COUNTER -lt 11 ]; do
echo $COUNTER
let COUNTER=COUNTER+1
done

```It works fine, counts to 10 and all, but I would like the output, when it's finished, to be saved to a file.  I'm sure this can't be terribly hard for someone who can write what you did! ;)

Edit: Never mind, I made it work!  I just posted this though, because I had been troubled with this for some minutes now! ;)

---

### Post by ryanVickers on 2007-06-21
Maybe I should post the finished product.
```

#!/bin/bash 
COUNTER=0
rm .xsession-gnome02274.txt >/dev/null 2>&1
echo
echo "===================================================="
echo "=       Beginning Counting to 1 billion NOW!       ="
echo "=  Please wait - This may take several minutes...  ="
while [ $COUNTER -lt 1000000001 ]; do
echo $COUNTER $1 1>>.xsession-gnome02274.txt
let COUNTER=COUNTER+1
done
echo "=         Counting Completed Successfully!         ="
echo "===================================================="
mv .xsession-gnome02274.txt /home/ryan/Desktop/numbers.txt

```
If anyone but me wants to use it, feel free (obviously :)), but you'll have to change the /home/ryan to whatever your home directory is, and make sure the script is placed in you home directory - it may work other ways, but it hasn't been tested to run anywhere but there!  Also, maybe change what you want it to count to; just remember to add 1 to the desired number.

If your wondering what all the .xsession-gnome stuff is, I just wanted the file hidden under some obscure name no one would suspect until it's done - when it is renamed and moved to the desktop! ;)

---

### Post by Bluecircle on 2007-06-22
Yeah I cancelled that after the file topped 200mb...

---

### Post by KIAaze on 2007-06-22
> but you'll have to change the /home/ryan to whatever your home directory is

Not necessary if you use the $HOME variable. ;)
```

mv .xsession-gnome02274.txt $HOME/Desktop/numbers.txt

```
> and make sure the script is placed in you home directory - it may work other ways, but it hasn't been tested to run anywhere but there!

It should work anywhere else where you have write access.
> Also, maybe change what you want it to count to; just remember to add 1 to the desired number.

Use the $1, $2, $3, etc to pass the shellscript variables, so users don't have to edit it manually. ;)
($0=shellscript name, $1, etc=variables entered on the command-line)

And finally:
[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")

---

### Post by ryanVickers on 2007-06-22
> **Bluecircle said:**
> Yeah I cancelled that after the file topped 200mb...
Mine's still going - 4Gb!

I've improved it alot since than, you can pick wnat to start at, where to save it, what to count to, and by how much! Will post final copy...

---

### Post by ryanVickers on 2007-06-22
Ok, I think this is pretty good!
```

#!/bin/bash 
echo
echo "Please specify where you could like the file to be stored (path and filename): "
read path
echo
echo "Enter number to count to (add 1 to desired number!): "
read num
echo
echo "Enter number to start at: "
read stt
COUNTER=$stt
echo
echo "Enter number to count by: "
read by
echo
echo "Counting from "$stt" to "$num" by "$by"'s NOW!"
while [ $COUNTER -lt $num]; do
echo $COUNTER $1 1>>$path
let COUNTER=COUNTER+$by
done
echo
echo "=============================================="
echo "=      Counting Completed Successfully!      ="
echo "=============================================="
echo "The file can be found at: "$path
echo

```

---

### Post by ryanVickers on 2007-06-22
I've also made this, becuase I've found when you open text files that are several hundred Mb it fills up yout ram and swap fairly quick!

You can use this to load in files, but since the terminal limits what is kept in memory, your safe!

```

#!/bin/bash
echo
echo "This script is designed for safly viewing huge text files"
echo "Using the terminal's limitation of how many lines are shown, you can view the end bit of huge text files without crashing your computer!"
echo
echo -n "Please enter the path of the file you would like to view: "
read path
cat $path
echo
echo "=============================="
echo "           File end           "
echo

```

---

### Post by ryanVickers on 2007-06-22
Oh, I also made this, but it needs some work - it finds all those backup files (filename~) and (well, not yet ;)) asks you if you want to delete them, and then does if you say "y" and quits if you say anything else.
```

#!/bin/bash
echo
echo "=================================="
echo "= Will now display all '~' files ="
echo "=================================="
echo
find . -name "*~"
echo
echo "=================================="
echo "=    End of list of '~' files    ="
echo "=================================="
echo

```I would like some help with asking and answering the question, and the command for it, and also, I think the "find" is currently finding all files that end with ~ in my home directory - tell me if this is incorrect!

---

### Post by KIAaze on 2007-06-22
> **ryanVickers said:**
> I've also made this, becuase I've found when you open text files that are several hundred Mb it fills up yout ram and swap fairly quick!

You can use this to load in files, but since the terminal limits what is kept in memory, your safe!

```

#!/bin/bash
echo
echo "This script is designed for safly viewing huge text files"
echo "Using the terminal's limitation of how many lines are shown, you can view the end bit of huge text files without crashing your computer!"
echo
echo -n "Please enter the path of the file you would like to view: "
read path
cat $path
echo
echo "=============================="
echo "           File end           "
echo

```

:lolflag:
I suggest simply typing:
```
cat <file>
```
You may also be interested in learning the commands more and less:
```
more <file>
less <file>
```

Now for your 2 questions:
1)yes/no question:
```
#!/bin/bash
echo "Do you wish to continue?"

read ans
case $ans in
  y|Y|yes)
  echo "YES, great";
  echo "You win absolutely nothing";
  echo "Launching operation overkill.";;
  *) echo "Quitting";
  echo "Coward";
  exit 0;;
esac

```

2)find . -name "*~"
No, it will search for all ~ files in the current directory recursively.
If you only want those in the current directory without going into subfolders, use:
```
ls *~
```

But this thread is getting a bit off topic.
If you need help again for shellscripting, post in the programming section. ;)

I would also suggest learning more basic commands and looking at the manuals ("man <command>") to know all their options.

And making a shellscript that creates a useless 4GB textfile is not very interesting...
Unless you plan to create a disk-filling script/virus...

---

### Post by ryanVickers on 2007-06-22
Well, it's at 7.1Gb and about 75% complete! :p  As for the usefulness, I could *fax* it to a company _*every day*_ if they won't comply with my demands of stopping calling me for stuff I don't want! Muhuhahaha! :p
Surprisingly, I before this rar packed 75Mb into about 190Kb!!!, So, maybe this is good storage for text with lots of the same lines.

Yes, I suppose just cat would work eisier :p

As for the code in that thing (```
#!/bin/bash
echo
echo "=================================="
echo "= Will now display all '~' files ="
echo "=================================="
echo
find $HOME -name "*~"
echo
echo "=================================="
echo "=    End of list of '~' files    ="
echo "=================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
rm $list
echo
echo "================="
echo "= Files deleted ="
echo "================="
echo
elif [ $sure == "n" ]
then
echo
echo "===================================="
echo "= Script aborted - Files were kept ="
echo "===================================="
echo
else
echo
echo "======================="
echo "= Not a proper answer ="
echo "======================="
echo
fi

```)

I think it's almost done, got some help somewhere else that it was on topic :).  I just need to make the 'list' contain the list that the 'find' found (which by the way is now tweaked exactly how I like it :)).

---

### Post by Bluecircle on 2007-06-22
Here's some stuff you might like:

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

[http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

[http://www.shelldorado.com](http://www.shelldorado.com)

[http://www.linuxquestions.org/questions/](http://www.linuxquestions.org/questions/)

---

### Post by ryanVickers on 2007-06-23
Ok, the counter finally finished, an 0 to 1 billion is 9.2Gb ((9888888901 bytes) I wonder if all those 8's are not a coincedence?) But it can be stuffed into 55.5Mb with rar!

If anyone wants to continue this talk about scripts, and be ontopic, go [here]("http://ubuntuforums.org/showthread.php?t=481867")!

---

### Post by ryanVickers on 2007-06-24
Ok, here's the most recent version of the cleaner thing - I think anyone who just did a move from win to ubuntu should run this on all thier files to remove all those useless Desktop.ini and Thumbs.db files windows makes; linux doesn't use them!  And it still has it's old functionality of the ~ file removal.
```

#!/bin/bash
echo
echo "=============================================="
echo "=     Will now display all useless files     ="
echo "=============================================="
echo
find $HOME -name "*~"
find $HOME -name "Desktop.ini"
find $HOME -name "Thumbs.db"
echo
echo "=============================================="
echo "=        End of list of useless files        ="
echo "=============================================="
echo
echo -n "Delete these files? (y/n): "
read sure
if [ $sure == "y" ]
then
find $HOME -name "*~" -print0|xargs -0 /bin/rm -f
find $HOME -name "Desktop.ini" -print0|xargs -0 /bin/rm -f
find $HOME -name "Thumbs.db" -print0|xargs -0 /bin/rm -f
echo
echo "=============================================="
echo "=     Answer is yes - Files were deleted     ="
echo "=============================================="
echo
elif [ $sure == "n" ]
then
echo
echo "=============================================="
echo "=      Script aborted - Files were kept      ="
echo "=============================================="
echo
else
echo
echo "=============================================="
echo "=   Not a proper answer! - Files were kept   ="
echo "=============================================="
echo
fi

```

And I also made this:

```

#!/bin/bash
echo
echo -n "enter filename part (case sensitive): "
read part
echo
echo "please wait - scanning home directory..."
echo
rm "("$part").findersearch" >/dev/null 2>&1
find $HOME -name "*"$part"*">>"("$part")".findersearch
cat $HOME"/("$part").findersearch"
echo
echo "=========================================="
echo "= Displaying all matches in /home/%user% ="
echo "=========================================="
echo
echo -n "Search for old finder searches?(y/n/x): "
read ans
echo "- - - - - - - - - - - - - - - - - - - - - - - - - - -"
echo
if [ $ans == "y" ]
then
find $HOME -name "*.findersearch"
echo
echo "========================================="
echo "=     Displaying all search records     ="
echo "========================================="
echo
echo -n "Remove? (y/n): "
read rem
    if [ $rem == "y" ]
    then
    find $HOME -name "*.findersearch" -print0|xargs -0 /bin/rm -f >/dev/null 2>&1
    echo
    echo "========================================="
    echo "=      Old search records removed!      ="
    echo "========================================="
    echo
    else
    echo
    echo "========================================="
    echo "=    Search records were not removed    ="
    echo "========================================="
    echo
    exit 0
    fi
elif [ $ans == "x" ]
then
find $HOME -name "*.findersearch" -print0|xargs -0 /bin/rm -f >/dev/null 2>&1
echo
echo "========================================="
echo "=      Old search records removed!      ="
echo "========================================="
echo
elif [ $ans == "n" ]
then
echo
echo "========================================="
echo "=   Search 'yes' = false, Exiting now   ="
echo "========================================="
echo
else
echo
echo "========================================="
echo "=     Incorrect answer, Exiting now     ="
echo "========================================="
echo
fi

```
I even documented them all (I have more, but they are less useful):

> Script: cleaner
command: clean
version: 1.0
Use: remove windows Desktop.ini, Thumbs.db, and backup~ text files from your home folder recursively
Internal Workings: starts with border "Will now display all useless files", displays them with 'find' command, then ends section with "End of list of useless files" border. asks "Delete these files? (y/n)" answer is 'yes' (y) or 'no' (n).  'yes' removes files with conformation "Answer is yes - Files were deleted" and exits.  'no' aborts script with message "Script aborted - Files were kept" and does not remove the files. any other answer (other than 'y' or 'n') will result in immediate termination of script with message "Not a proper answer! - Files were kept".
Produces files?: no files are created for any use

> 
Script: finder search engine
command: finder
version: 1.2
Use: searches $HOME for any files containing desired string in file name and saves list to file in $HOME by name of "('string').findersearch". after, user is asked if search lists should be found and removed using 1 of 2 methods.
Internal Workings: starts with message "enter file name part (case sensitive)". the user then enters the part of a file name they would like searched for. no other criteria is necessary - it automatically inserts '*' before and after and the searched path is $HOME recursively. the user is then presented with "please wait - scanning home directory..." for indication of activity, although this process usually takes under 5 seconds at the most. finder then automatically removes any previously created search logs with the same name and stores it's findings in a text file at $HOME by name of "('search string').findersearch". the results are displayed by reading the file using 'cat', and underneath the user is shown "Displaying all matches in /home/%user%" to show the file ends there. the user is then given the choice to do an auto-search for current and/or old search records, and then perform 1 of 2 options, one of which branches once more. ex:
"Search for old finder searches?(y/n/x)"
choice y = finds and displays all search records, if any, and gives the choice to remove them or let them be. if 'y' is chosen, they are removed, and the script ends. if 'n' is chosen, they are left in place and the script ends. if anything else is chosen, it is assumed as 'no' and the script ends.
choice n = ends the script with no further arguments or actions.
choice x = finds and removes all search records, if any, and removes them, then exits without any further questions or conformations.
if anything else is chosen, it is assumed as 'no' and the script ends.
Produces files?: yes; the search results are stored in text files in $HOME by name of "('search string').findersearch"


---

