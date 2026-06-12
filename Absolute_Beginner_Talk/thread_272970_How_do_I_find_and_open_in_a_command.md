---
title: "How do I find and open in a command?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-10-07
How do I find all files that says "campingtrip*" and open it with eog in a single command?

---

### Post by deadgobby on 2006-10-07
This link is on todays topic.
[http://ubuntuforums.org/showthread.php?t=272957](http://ubuntuforums.org/showthread.php?t=272957)

---

### Post by jaboua on 2006-10-07
Locate database is fast but often outdated as it's updated once a day iirc, unless you manually run "sudo updatedb".

I would do something like:
find /some/folder/ -iname campingtrip* -type f|xargs eog

If the names contains spaces, you may need to put a "sed" command (man sed) in between find and xargs to wrap the filenames in quotes. Run "man find" and "man xargs" to understand what the command I gave you does. The pipeline ("|") redirects output from one command as input to another command.

---

### Post by tux101 on 2006-10-07
> **deadgobby said:**
> This link is on todays topic.
[http://ubuntuforums.org/showthread.php?t=272957](http://ubuntuforums.org/showthread.php?t=272957)



The question is: How do I find all files that says "campingtrip*" AND open it with eog in a single command?

Not: How do I find all files that says "campingtrip*"

You gave me a link to some guy who cannot find his songs.  I can find the files with

```
find campingtrip*
```
But the above would not open it.
```
eog campingtrip*
```
The above would open it, but I have have to know the dir path it is stored or be in it.

I would like to know the single line command to find and open files under the condition that I do not know where the files are.

EDIT: Kind of long, but worked.  Thanks, jaboua!

---

