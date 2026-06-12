---
title: "[SOLVED] Scripting help"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2008-01-23
Ok, this is somewhat difficult to explain how it works, and what I want to be able to do, but I'll do my best and maybe somebody will be able to help me out.

On my parent's server, their apache access logs are rotated daily.
The default apache log is websitename.datetime

When logrotate hits it, it then becomes websitename.datetime.tar.gz and then creates a new log websitename.datetime, where datetime would be the new date and time of the log creation.

The date and time constantly change every day, so there is no way to pinpoint exactly what those numbers will be.

But, I need to write some type of script (well, I'll be doing it in php, but it can be bash because I can run exc(bash) in php) that can capture the name of the latest tar.gz file, or the access_log right before it gets rolled (with the help of crontabs).

The problem is, how do I write something that will know what tar.gz to copy, because there are 4 other tar.gz'ed access_logs for 4 days, and then they drop off the scene. 

Is there any way to do this with a script?

Best regards,
Dr Small


Edit, by the way, I have no control over logrotate, because it is on a shared server with many other websites, so that wouldn't be an option.

---

### Post by Rocket2DMn on 2008-01-23
I don't know much of anything about php, but since you can run bash commands, what if you listed the contents of the directory in order of date and took the newest .tar.gz file?  This is assuming you can get feedback from commands.
```
cd /path/to/logs
ls -lt *.tar.gz
```
You can grab the first line that is returned and pull the filename from it (8th column or so)

A C-like command would be like
```
string var[] = exc(ls -lt *.tar.gz)
string filename = var[0].parse(blah blah)
```
I think you get the idea.

---

### Post by bhold on 2008-01-23
I haven't written shell script code for a while, but you should be able to use the ls command to get a list of web log filenames, then sort the list of filenames. If the date/time portion of the filename is in Unix epoch seconds, this should guarantee that the final filename in the list is the most recent (which sounds like what you are trying to get at).

---

### Post by asmoore82 on 2008-01-23
```
ls -t *.tar.gz | head -1
```

---

### Post by Dr Small on 2008-01-24
Thanks for all the help guys. I stayed up pretty late last night trying to get my script to work functionally, but couldn't get it all straightened out last night, so I fixed it up this morning.

I did for awhile use the examples you all gave me, and they did work as needed, but occasionally my parents will untar the archives to go back and read them (from several days ago) and then recompresses them, so that messed all of the modification time up on it.

I just came up with the solution to copy all of the archives from the logs directory over to another backup directory where I could compress them into one, deleted the copied archives, and setup a script with crontab on my machine to download the archive, rename it and remove the archive from the server.

So, now instead of running a crontab every day to download the latest log, I am downloading a bundle of 6 logs, so I ran the crontab every 6 days to get the latest like that. It's working great so far.

Thanks for all the suggestions and help!

Dr Small

---

