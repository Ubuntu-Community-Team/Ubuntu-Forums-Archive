---
title: "Execute php script using crontab!?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by JuicedJuice on 2007-07-01
Ok, I always get feedback to use cron for exceuting my php scripts on a timer but I have read through a whole ton of web sites at this point, all filled with overly technical and non-related info about what I want to do with crobtab and I have yet to find a single example of everythng that must actually be done to execute the code in a php script on a timer. If I had a single step by step example i'd be good but it's apparently impossible to find. For example, if I need a php script called "crontest.php" that is located in /var/www/somefolder to run every 5 minutes what would I do exactly? Apparently I need to open up the crontab editor and do something like "*/5****/var/www/somfolder/crontest.php" but I dont know how to do this at all or whether the syntax is right or what. I open up terminal, type in crontab -e and some editor screen appears and on the first line where the blinking curson is, it says "# m h  dom mon dow       command". I assume im supposed to maybe delete this text and type something here, but what, and after i'm done typing it then what do i do/press exactly step by step because hitting enter does nothing but move the cursor to the next line. I'm a linux newbie, using ubuntu 7.04 64-bit. Since the OS install i've installed the stuff for web server (apache, mysql, php etc) do I need to manually install anything else for cron to work?

---

### Post by Malibu Illusion on 2007-07-01
Okay,  from the top....

This will bring up vi: a CLI text editor to edit your crontab:

```
crontab -e
```

Your crontab should then be formatted correctly, telling Linux when and what to execute.  Enter:

```
*/5 * * * * path_to_script
```

The format is:

Minute, Hour, Day of Month, Month, Day of Week, Command to execute.  The reason there is a */ in front of the 5 is to execute it every 5 minutes.  If there was no slash, it would execute at 5 minutes past the hour only.

The initial line that you'll notice is informing you of the correct format.  This can stay as it has a # in front of it, which means the line is treated as a comment and ignored.

To save this file, enter :wq when out of insert mode in Vi.

Issue:

```
crontab -l
```

This will show you that the crontab is installed and working. 

There are numerous tutorials and whatnot regarding crontabs on the internet, as well as information pertaining to Vi.  I suggest googling those terms if you wish to know more.

Also bear in mind that you will need to install the PHP CLI package to be able to call scripts from the CLI like you're attempting to do.  You'd then call the script with:

```
php path/to/file/here.php
```

---

### Post by JuicedJuice on 2007-07-01
Alright, thanks man. The whole PHP CLI package is what i was missing.

---

