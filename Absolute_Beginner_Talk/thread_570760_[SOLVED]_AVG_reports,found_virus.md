---
title: "[SOLVED] AVG reports,found virus"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-10-08
Hi all
every day AVG reports its found a virus,
in the results part it says
can not open ; checked ! invalid argument.
does AVG have a virus vault or something,how does it deal with it ?  :confused:

i have also ran avast and this brings up no errors 

i do not have windows installed 
is this a false alarm ?

any help would be welcome
thanks

---

### Post by Seisen on 2007-10-08
I really wouldn't worry about getting virii on Ubuntu and since you are not dualbooting with Windows you really don't have to worry about it.

---

### Post by skymera on 2007-10-08
can you post a screenshot of what the result is?

are you sure its NOT findinf this on your WINDOWs partition? :wink:
common misconception

---

### Post by ThrobbingBrain66 on 2007-10-08
> **skymera said:**
> can you post a screenshot of what the result is?

are you sure its NOT findinf this on your WINDOWs partition? :wink:
common misconception

[quote=nikef]i do not have windows installed
is this a false alarm ?[/quote]

He doesn't dual-boot with Windows

EDIT:  Does it give you the name of the virus?  Have you googled it to find more information on it?

---

### Post by FuturePilot on 2007-10-08
I'm guessing a false alarm. For all practical purposes, there are no viruses for Linux. If any do exist they exist in the lab or in theory only.

---

### Post by skymera on 2007-10-08
no viruses?

thats a half true.

theres been some,. very little, but could be 1 or 2 about some where.

---

### Post by Malibu Illusion on 2007-10-08
> **skymera said:**
> no viruses?

thats a half true.

theres been some,. very little, but could be 1 or 2 about some where.

You're being picky for no reason.  His post was intended to highlight the absolute minimum risk there are to users and the trouble you'd actually have to go to in order to acquire a virus yourself and install it.  Even then it'd have great difficulty in replicating and distributing itself to others, let alone getting it installed on their systems as well.

For all intents and purposes, noone is going to go through the process of compiling a virus and installing it as a superuser.  The majority of software which people want is in the repositories anyway, which is verified as clean.

His post was accurate entirely for what it was trying to convey.

---

### Post by skymera on 2007-10-08
buts its not right leading him to believe there is none.

you have to make peop,e aware of the very very few about.

---

### Post by om1 on 2007-10-08
most likely it was a false alarm or you downloaded a file and it is finding a file that has M$ Windows virus on it... dont worry bout it unless you are file sharing with a windows computer

---

### Post by nikef on 2007-10-08
thank you all
He is a she lol
 here are some screenshots

---

### Post by skymera on 2007-10-08
that not much help :wink:

but it shows it found something :lol:

whats the name of the virus?

when you scan it should actually say

---

### Post by nikef on 2007-10-08
sorry its not much help :(

i don't do a manual scan,its automatic ,goes on in the background
so i don't get to see any names of the virus

---

### Post by ajgreeny on 2007-10-08
Get a copy of clamav from the repos, run ```
clamscan -ri
``` in a terminal, and it will find anything you have with a virus, and tell you where it is and it's name.  But I really wouldn't worry too much.

---

### Post by nikef on 2007-10-08
> **ajgreeny said:**
> Get a copy of clamav from the repos, run ```
clamscan -ri
``` in a terminal, and it will find anything you have with a virus, and tell you where it is and it's name.  But I really wouldn't worry too much.


thanks just installed clam av ,but can not find on my pc,even after re-boot

also when i try command it says
WARNING LibClamAV is out of date,i need to update  :confused:

---

### Post by mivo on 2007-10-08
Just means it wants you to update the virus definitions. I haven't used ClamAV on Linux, only on a Windows box, but there should be an option somewhere in the GUI to update the data. :)

---

### Post by Kilz on 2007-10-08
> **nikef said:**
> thank you all
He is a she lol
 here are some screenshots

The screen says it checked one file. In that one file there was a virus? The odds are astronomical.
You also have another antivirus Avast. Having 2 is double kill and one may see the other as a virus and try to make you remove its competition. Do yourself a favor, remove them all they are not needed.

---

### Post by RomeReactor on 2007-10-08
Hi. To update Clam's database, run:
```
sudo freshclam
```
It's problable that you'll get  a warning about not having the newest ClamAV, and a lot of new users freak out about it; don't pay too much attention to that. I've found ClamAV to work best from the command line. For example, if I want to scan my Music folder, which has no sub-folders:
```
clamscan /home/romrereactor/Music
```
or
```
clamscan ~/Music
```

To scan my whole home directory **and** sub-folders:
```
clamscan -r /home/romereactor
```
or
```
clamscan -r ~/
```

To scan your **whole** system:
```
clamscan /
```

If you run clamscan without any parameters, it will scan you current working directory (the directory you're currently on in the terminal).

For more options and usage examples:
```
man clamscan
```

As a side note, you really don't need an antivirus if you don't have a partition with windows; or, if you want to scan files or mail attachments before sending them to windows users (so they don't get infected if a file has a virus, which won't affect *you*). Otherwise, there's no point on having an AV. Do a search for antivirus on these forums; there are plenty of threads discussing this.

---

### Post by kyphi on 2007-10-08
AVG may come with a test file included and that is the one that triggers the "Found Virus" message.  If that is the case, then the removal of the test file would be the remedy.

AVG would be in a better position to answer your question.

---

### Post by odzk on 2007-10-08
invalid argument, i think its more like a bug or something, i dont think its a virus

---

### Post by da Wookiee on 2007-10-09
Actually, I'm having the same problem, and I think it's a permission error, not a virus.  

See, I've got avg set to scan on reboot.  Every time it does, it gives the virus message and indicates it's scanned no files.  When I get in, I run a scan and get prompted for the root password.  It functions perfectly, finds no virus, but gives the "could not open /" error.   

What I think is happening on the boot,  is that avg is trying to scan but doesn't have the root permission at boot.  The later error is caused by / being unreadable in any case.

What I don't know is how to fix it.

Mindseye

---

### Post by por100pre1 on 2007-10-09
That AVG version is buggy. Try the latest one or remove AVG for good.

---

### Post by Perfect Storm on 2007-10-09
The error means it can't or havn't permission to check the file. It's no virus.

---

### Post by nikef on 2007-10-14
thanks all
will mark solved and put it down to permisions  :)

---

