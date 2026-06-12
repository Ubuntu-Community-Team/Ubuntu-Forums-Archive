---
title: "finding files..."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by aks44 on 2007-05-21
OK, newb question here, but looking on the web didn't yield relevant results, and man pages are no use to me if I don't already know the command name. :(

I want to find files based on several conditions :
- file name matches some pattern and/or file contains a specific string,
- inside a specific directory (and possibly it's sub directories)

I guess at some point I have to use grep, but by itself it doesn't seem to be enough...

Thanks by advance.

---

### Post by Ateo on 2007-05-21
The command to use would be 'find'. Do 'man find' to get all the details.

---

### Post by Cypher on 2007-05-21
Open a terminal with Appilcations->Accessories->Terminal and type
```

find <starting-dir> -name "<pattern>" -print

```
<starting-dir> would be where you want to start searching, if current directory onward, use ".", or "/" or "/usr" or whatever.
<pattern> is what you want to search for "lib*" will get you anything starting with "lib". The * is wildcard for "anything after lib". If you want exact names, just put that as <pattern>
If you now want to search each file called "foo" for "bar" then you would do
```

find / -name "foo*" | xargs grep "bar"

```

---

### Post by dannyboy79 on 2007-05-21
2 different commands. one uses a database you create whicih can be searched using the "locate" (the man page is slocate) command or you can just use the find command. the find command will make your hard drive spin and be searched whereas using locate will look within a database so it won't really make your hdd spin I don't think.

the bad thing about locate is that you add something to your computer and hten try to search you won't find it becuase you have to update the database first. the database gets updated every day with a cron job by default, I think it's under /etc/cron.daily/man-db or maybe it's slocate. The point is it will update the database everyday automagically.

so to create the database if it's not created is this command

```
sudo slocate -u
```
this will create a database starting at /
then to update it if you download something and want to search for it you would issue
```
sudo updatedb
```
then to find something, it's as easy as
```
locate blah
```
it will search the database for anything that matches blah

OR

you can just use the find command, so the syntax is this
```
sudo find / -name blah
```
this means that it will look within / and any directory under that, and it will look for anything that matches blah. good luck

---

### Post by rich.bradshaw on 2007-05-21
If you don't want it for a script, try beagle or tracker, nice GUI search engines...

or

cat * | grep FINDTHISTHING

will search in everyfile in a directory for some text. THat can obviously be streamined a bit to make it actually useful, but you get the idea!

---

### Post by aks44 on 2007-05-21
> **Cypher said:**
> ```
find / -name "foo*" | xargs grep "bar"
```
That did the trick. Thank you !

**Edit:** Thanks everyone for your numerous and quick answers.

@rich.bradshaw : thanks, I'll have a look at those GUIs... I dumped Windows only two days ago, so I'm not yet very efficient at command lines... :oops:

---

### Post by Peverel on 2007-05-21
Same here...install Edgy about a week ago... :)

Question, when I use Desktop search (which is Beagle, isn't it?), I dont want it to scan a document's contents, just the filenames...is that possible?

Thanks

---

### Post by aks44 on 2007-05-21
> **Peverel said:**
> Question, when I use Desktop search (which is Beagle, isn't it?), I dont want it to scan a document's contents, just the filenames...is that possible
I didn't try Beagle nor Tracker yet, but what you're asking is the
```
find / -name "foo*"
```part of Cypher's answer...

Hope this helps, even if it doesn't answer your specific question.

---

### Post by zvacet on 2007-05-21
```
whereis file_name
```

---

### Post by Peverel on 2007-05-22
Thanks guys, that's done it :)

---

