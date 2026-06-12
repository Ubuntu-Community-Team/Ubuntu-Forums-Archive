---
title: "Running a batch file"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-06-25
If there is such a word in linuxland.........

Say to backup some files (on demand). Do I create a command file, chmod it to become an executable and then link it to a menu option?

Thanks.

---

### Post by kevdog on 2007-06-25
Batch files are known as shell scripts in the linux world.  I think the way you proposed is perfectly acceptable.  If you wanted to automate the process (rather than clicking on the icon or typing via command line), you could add the script to something known as the cron daemon.  You can specify cron jobs to run automatically every 1 minute, 1 hour, once a week, once a year, or any combination of days, hours, minutes that you want.  It just really depends on what your needs are.

---

### Post by FleetAdmiral74 on 2007-06-25
I think there is a command, something like rsync...I can't remember it exactly. Do a quick search on backup, lots of people have asked this before...

---

### Post by mlentink on 2007-06-25
Basically: yes.

Except they're called shell scripts in 'linuxland'. I would recommend [linuxcommand.org]("http://http://www.linuxcommand.org/") (highly, good site) to learn more about writing scripts.
You&#314;l also discover how incredibly powerful they can be...

---

### Post by jimbob on 2007-06-25
You could do it that way if you wish.

Being an old-timer I tend to think of "batch" as some low priority job that runs when the processor is not doing anything else or anything important and is usually started in the wee hours of the morning by a half-asleep computer operator.

Jobs can be started in the background in linux by adding an & on the command line when they are started.  This gives them a lower priority than any foreground jobs that may be concurrently or subsequently running.

You might also investigate using the cron command to run your batch stuff on certain days and times automatically.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by eentonig on 2007-06-25
To create your backup script


> #!/bin/bash
# The first line is needed to tell the shell that this is a bash-script
# 
# Some info regarding the purpose a this script.
# Probably a date of creation and revision number as well.
# Not strictly needed, but helps in good housekeeping and future reference.
# 
rsync --quiet --archive <source_DIR> <destination_DIR>


To make it fancier, you could write the output to a 'logfile' and include datestamps.

Just make the file executable and run it ùmanually or scheduled through cron

---

### Post by kevdog on 2007-06-25
If you want my specific recommendations about a backup program, I would recommend unison over rsync in that it is more robust. 
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

Just my two cents!

---

### Post by Bluecircle on 2007-06-25
Here's my backup script:

```

#!/bin/bash
#
# Backup all my stuff
# Updated 06/21/07 v2.1
#

cd /

tar cvpzf "/media/ONE TERABYTE OMG/Backup/sysbackup.tgz" --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/home --exclude=/media /

tar cvpzf "/media/ONE TERABYTE OMG/Backup/homebackup.tgz" --exclude=/home/brian/.Trash --exclude=/home/brian/Stuff/Fun --exclude=/home/brian/Music /home

tar cvpzf "/media/ONE TERABYTE OMG/Backup/importantbackup.tgz" /home/brian/Desktop/Important /home/brian/.mozilla /home/brian/.mozilla-thunderbird /home/brian/Desktop/datarec

dpkg --get-selections > "/media/ONE TERABYTE OMG/Backup/packages"

exit 0


```

It's probably a lot easier to use rsync, but this is how I like to do it.

To do this, simply make a new file starting with "#!/bin/bash", or whatever shell you wany to use. Then put your commands. After you have finished, do a chmod 775, or chmod +x on the file. Or, you can right click and select Properties -> Permissions -> Allow excecuting as a file. You should then copy the script to /usr/bin/ so that you can simply type the command (name of the file) into the terminal. If you want it to run automatically, run

```

crontab -e

```

and add it.

Shell scripting:
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)
[http://www.shelldorado.com](http://www.shelldorado.com)

Cron:
[http://en.wikipedia.org/wiki/Crontab](http://en.wikipedia.org/wiki/Crontab)
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

Fcron:
[http://fcron.free.fr/](http://fcron.free.fr/)
[http://fcron.free.fr/doc/en/index.html](http://fcron.free.fr/doc/en/index.html)
```
sudo apt-get fcron
```

---

### Post by kevdog on 2007-06-25
Do you find much difference and benefit of using fcron over Vixie Cron (cron)???

---

### Post by Bluecircle on 2007-06-25
> **kevdog said:**
> Do you find much difference and benefit of using fcron over Vixie Cron (cron)???

In more complicated shell scripts I started running into problems with normal cron. for example, If i wrote:

make_page
```

#!/bin/bash

# make_page - A script to output stats

pinf=$(procinfo -m)

cat <<- _EOF_

<HTML>
    <HEAD>
<title>Info</title>
    </HEAD>

    <BODY bgcolor="#000000">

<pre><font face="monospace" color="white">$pinf</pre>

</font>
    </BODY>
    </HTML>

_EOF_

exit 0

```

and then wrote a script to print it to an html file:

stats
```

#!/bin/bash

# stats - A script to produce a HTML file and upload it to a remote server

cd /home/brian/bin/stats/

./make_page > index.html

scp /home/brian/bin/stats/index.html nointernet@rossmore.dreamhost.com:nointer.net/index.html

exit 0

```

This would work perfectly well if I executed it myself, but if I entered:

# 0-59 * * * * /home/brian/bin/stats/stats

into cron, the results of $pinf would be blank. Using fcron this did not happen. This is just one example. Most variables would work fine, but I had problems with a few like this one.

---

