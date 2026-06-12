---
title: "Questions about bash scripting.."
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by xtek on 2006-08-22
I have this question about bash scripting.  I'm a total nub when it comes to linux and I hope that I posted this in the right forum.  I run a linux faxing server (Hylafax) that I threw together, and have been informed that the company that I work for wants to save the outgoing faxes for a specified amount of time.  The thing is that I know jack about bash scripting.

My question is this.  

What I need done is to write a script that will take the contents of location A and zip them up to a file named after the current date, then move that file to another location, then delete the files that were zipped.  

The problem that I'm having is that I believe that you need admin (sudo) rights to delete those files, and I have no idea on how to retrieve the date and set the file name using a script.

I would appreciate it if someone could give me some hints, or point me to a place(s) that would give me a helping hand.

---

### Post by kidders on 2006-09-03
Hi there,

There are lots of bash scripting tutorials scattered around the internet ... too many in fact!

Anyhow, let's see how much help I can be, before you run to Google.

What you're proposing sounds like a one-liner, really. Start with a blank text file and type **#!/bin/bash** at the top, on a line by itself.

The basic commands you want are **tar** and **rm**, to zip and delete. **tar -czf archive.tar.gz /var/tmp/faxes/* && rm /var/tmp/faxes/*** about covers the basics.

Adding the date to a filename is pretty trivial ... type **date --help** for more detail than I'm giving here. To give yourself a sample filename, type **echo fax_archive_`date +%Y%m%d%H%M`**

So, here's a quick sample. It's fleshed out a bit for you, to handle a little unpredictability:

```

#!/bin/bash

# Check source location
if [ -z "$1" ]
	then echo "You forgot to specify a source location"; exit 1;
	else if [ ! -d "$1" ]
		then echo "Directory not found: $1"; exit 1;
	fi
fi

# Check target location
if [ -z "$2" ]
	then echo "You forgot to specify a target location"; exit 1;
	else if [ ! -d "$2" ]
		then echo "Directory not found: $2"; exit 1;
	fi
fi

# Check for something to archive
FILECOUNT=`ls -l $1 | wc -l`
if [ $FILECOUNT -le 0 ]
	then echo "Nothing to archive"; exit 0;
fi

SRC_NAME="$1/*"
DST_NAME="$2/fax_archive_`date +%Y%m%d%H%M`.tar.gz"

# Actually perform the archival
echo "Archiving $FILECOUNT files in $1 to $DST_NAME"
tar -czf "$DST_NAME" "$SRC_NAME"

# In case of error, remove any (broken?) archive
if [ $? -ne 0 ]
	then "Archival failed"; test -e "$DST_NAME" && rm -f "$DST_NAME"; exit 1
fi

# Delete original files
echo "Deleting source files"
rm -f "$SRC_NAME"

# Finished
echo "All done :)"

```

So, say you call this **/usr/local/bin/archive**, the first thing you do is **chown root:root** it and **chmod 755** it. Next, you should create a destination location for your archives, say, **/var/log/archives**

Invoke your script with **archive /var/tmp/faxes /var/log/archives**

At this point, please note three very important things:

[LIST=1]
[*]Don't just blindly copy/paste my script ... I haven't checked it!
[*]**NEVER EVER** "sudo" a shell script, or run one as root. Should an unauthorised or accidental modification be made to the script, it would execute with root privileges. Imagine adding "rm -Rf /*" to the end!!
[*]This script has a **major flaw**: Should a fax be added to the source location during execution, it may be deleted without being archived, since the deletion happens *after* the archival.
[/LIST]

Leaving this aside for a moment, you mentioned privilege difficulties with deletions in your post. I would solve this by adding a new unprivileged group to my system. I would see that the script is run by a member of my new group and that the faxes are given the appropriate permissions to allow that group to delete them. So, let's get started:

[LIST=1]
[*]Create a new group called "faxarc": **sudo groupadd faxarc**
[*]Add myself (kidders) to the group: **usermod -G faxarc kidders**
[*]Change the owning group of /var/tmp/faxes (my archive source location) to "faxarc": **chgrp faxarc /var/tmp/faxes**
[*]Force files added to that location to bear the "faxarc" group marking: **chmod g+s !$** (!$ refers to the last argument of the previous command ... give it a try!)
[*]Update any files that are already there: **chgrp faxarc !$**
[*]Grant the faxarc group write access to both the source and destination locations: **chmod g+w !$ && chmod g+w /var/log/archives**
[/LIST]

I realise this is getting quite long-winded and, for someone who isn't all that accustomed to scripting and other such tinkering, it could be a bit confusing. So, I'll just summarise quickly:

[LIST]
[*]We've created a script capable of handling a certain level of unpredictability in its environment, but is FAR from fool-proof.
[*]We've added a group we intend to use to execute it to our system.
[*]We've tinkered with the archive source + destination to allow members of our new group some nice privileges, thus side-stepping the need to run scripted tasks as the super-user.
[*]We're about to cap this off by periodically auto-executing it.
[/LIST]

Some of the things I've used are:

[LIST]
[*]**if** - Take a look at "man test" for information about the various comparisons it knows how to make.
[*]**$?** - Refers to the "exit code" of the last command.
[*]**The SGID bit** - Google it for more ... it's handy.
[*]**`backticks`** - For embedding commands in eachother.
[*]**cron** - See below
[/LIST]

Especially for what I'm about to describe, the idea of an "exit code" is pretty important. When a program terminates, it returns an integer value to the operating environment indicating exactly *how* it terminated. Things like segmentation faults (memory allocation errors), explicit "kill" instructions, etc. can be detected this way. Any non-zero exit code is considered an error condition.

Now for the master stroke :P Take a peek at the contents of the **/etc/cron.daily** directory. Any script you add to this directory will be executed on a daily basis automatically. I suggest you take advantage of some of the more advanced features cron has to offer and take a *closer* look at **/etc/crontab**. This is where you should put your directive to have your script executed, say, on a 3-hourly basis, 9am to 5pm on weekdays, by a member of your "faxarc" group. Googling "crontab" will give you far more help than I can here.

Anyhow, I really hope all this is of some help!

Best of luck, and post back any difficulties :)

---

