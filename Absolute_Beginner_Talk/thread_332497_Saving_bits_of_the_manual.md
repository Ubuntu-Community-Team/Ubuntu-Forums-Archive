---
title: "Saving bits of the manual"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-01-06
Hi there, a very simple question, I want to print off a few of the entries from the manual (for a bit of reading into things I'm interested in) and viewing the manual with 
```

man *name*

```
means I have to scroll down little by little and its a real pain.

Ideally I want to open the man file in gedit/openOffice so I can print off bits I want easily, search the whole document quickly and so forth - how can I do this?

Thanks very much,
Il

---

### Post by sardion on 2007-01-06
I suggest using man2html (don't know if its installed by default but it should be available via synaptic).  Take a look at that and see if it works for you.

---

### Post by quartzy on 2007-01-06
The man pages are stored in /usr/share/man, but there are LOTS there.  If the package is apt-get installed running a 

```
dpkg -L packagename
```

Will list all the files including the man files.

They are just tar's files and once untared can be opened with a web browser (well konqueror worked)

---

### Post by jvc26 on 2007-01-06
> **sardion said:**
> I suggest using man2html (don't know if its installed by default but it should be available via synaptic).  Take a look at that and see if it works for you.

Right - bit more work found on synaptic and now some other issues: have unearthed [http://hydra.nac.uci.edu/indiv/ehood/man2html/doc/man2html.html](http://hydra.nac.uci.edu/indiv/ehood/man2html/doc/man2html.html) 
However trying :
```

man topic | man2html [-options]  > outfile 
**In the format:**
man mount | man2html  > /home/james/Desktop/search2.html

```
When I open search2.html I get a page with
> 
Status: 403 Forbidden Content-type: text/html
Invalid Man Page
The requested file (stdin) is not a valid (unformatted) man page.

The other method I tried was:
```

man topic | man2html [-options]  > outfile
**Using the options -k**
man -k mount | man2html -k -cgiurl > /home/james/Desktop/search3.html

```
Which gives me
> 
Status: 500 Internal Server Error Content-type: text/html
man2html: bad invocation
Call: man2html [-l|-h host.domain:port] [-p|-q] [filename] or: man2html -r [filename] 

Any ideas?
Il

---

### Post by jvc26 on 2007-01-06
Edit: SOLVED!

If anyone wants to know how to use this:

The syntax would me (for man mount)

```

man mount man2html > /path/you/want/to/save/to/mount.txt

```

Why a .txt?:
This is because it makes it readable with formatting, saving as a .html comes out as a horrific mess with all the lines merged

Why do you get error messages when you put the extra tags in from:
[http://hydra.nac.uci.edu/indiv/ehood/man2html/doc/man2html.html](http://hydra.nac.uci.edu/indiv/ehood/man2html/doc/man2html.html)
I havent the faintest - it spans up the error message and then the output file is affected as you tell it to be - so who knows? It doesnt seem to do anything wrong though - if anyone would care to tell me that would be cool.

Anyways, no worries, cheers for the pointer to man2html sardion - legend.

Il

---

