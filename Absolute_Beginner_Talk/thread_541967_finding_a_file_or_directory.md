---
title: "finding a file or directory"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by DarkDancer on 2007-09-03
Hi! I'm not precisely an absolute beginner, but this really is an absolute beginner question that I should have figure out a long time ago.

The background of the current issue. I am following [IMG]this[/IMG] thread, rather dilligently, except for one thing. It tells you to download an extract the tarball, but I used synaptec to just install the program for me. The instructions then go on to say "Now go into the "sql" sub-directory in torrentflux (depends on where you untared torrentflux, of course):" well, since I didn't unpack the tarball, I have no clue where synaptec put it, I can't **find** it, I can't **locate** it and **Search For Files** alsom comes up with a blank. This happens most of the time when I try to find a file. what am I doing wrong?

---

### Post by taurus on 2007-09-03
Try

Applications -> Accessories -> Terminal
```
sudo find / -name torrentflux* -print
```

---

### Post by moffa on 2007-09-03
It is probably in /usr/lib/torrentflux

but you can try running whereis [file name] or locate [filename]

---

### Post by DarkDancer on 2007-09-03
moffa,

I always try find and locate, have never tried whereis. It's not there though.

taurus,

That seems to have worked, better than any of the things I tried, I found torrentflux.mysql, but not sql......may be the same thing though...don't know, will have to checkl back with the thread to see if there has been a change in the naming convention....

Now, let me see if I understand this 

sudo, of course gives you root access.

find, finds things.

/ is a modifier telling ubuntu where to start looking.

-name means you are looking for a file name?

torrentflux* is looking for torrentflux with anything after it

-print means show the results.

Sorry, I have to understand what the commands do before I even have a chance of remembering them.....

---

### Post by taurus on 2007-09-03
> **DarkDancer said:**
> moffa,

I always try find and locate, have never tried whereis. It's not there though.

taurus,

That seems to have worked, better than any of the things I tried, I found torrentflux.mysql, but not sql......may be the same thing though...don't know, will have to checkl back with the thread to see if there has been a change in the naming convention....

Now, let me see if I understand this 

sudo, of course gives you root access.

find, finds things.

/ is a modifier telling ubuntu where to start looking.

-name means you are looking for a file name?

torrentflux* is looking for torrentflux with anything after it

-print means show the results.

Sorry, I have to understand what the commands do before I even have a chance of remembering them.....

You've got the arguments for the **find** command down to a tee.  :)

---

### Post by DarkDancer on 2007-09-03
Thanks... ;)

---

### Post by Paul133 on 2007-09-03
Yup. Did you read the find man page?

---

### Post by philinux on 2007-09-03
You could always use Places > Search for files.

---

### Post by schorsch on 2007-09-03
To find a file that you recently installed with synaptic via the locate command you have to refresh the internal file "database" first:
```
sudo updatedb
```
And as you installed the precompiled package via synaptic just forget about the advices from the website you got the tarball from: They are useless ...
But there is an easy way to find where synaptic put the files:
Fire up synaptic; choose the installed package and click on "Properties": There is a tab called "Installed Files" ... ;-)

---

### Post by DarkDancer on 2007-09-04
> You could always use Places > Search for files.

Yeah, that never works for me....

---

