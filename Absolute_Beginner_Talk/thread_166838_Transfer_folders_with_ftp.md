---
title: "Transfer folders with ftp?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-04-27
How can I transfer folders with content and subdirectories with FTP in console?

---

### Post by cilynx on 2006-04-27
you can use the "ftp" command to open up a standard FTP shell, but that's a little obnoxious if you're looking to script something.  For scripting purposes, look into "wput".  It's like "wget", if you've ever used that, just in the other direction.

---

### Post by halfvolle melk on 2006-04-27
lftp can do that with the 'mirror' option.

lftp 10.1.1.1 <remote_username>
mirror ~/remote_dir
(where 10.1.1.1 is my server)

Run lftp and type 'help mirror' for more details.

---

### Post by Nunyah on 2006-04-27
wput seemed like a good tool, as it can be used cross platform. I'm having trouble transferring directory tree with files in it.

**Example:**
[I]We have a web directory containing 2 sub directories: **gfx** and **includes** as well as **index.php** (1 file)
**gfx** has two images: **banner.png** and **btnlogout.gif**.
includes has 1 file: **functions.inc.php**[/I]

For simplicity im standing in the web folder typing in the command shell:
*wput [ftp://username:password@10.0.0.9/web/](ftp://username:password@10.0.0.9/web/)*

The transfer succeeds, the folders are made, but the files are skipped.
What am I doing wrong? I've tried different methods and syntax'ed it different etc. I've searched both web and reference but I cannot find an appropriate example explaining how.

I'm using XP pro and Win 2003 server in the example, but it would be the same for my ubuntu machine, only a slightly different system path.

---

### Post by cilynx on 2006-04-27
Do the files already exist server side?  wput does lots of neat things worth reading about in the man pages and in /usr/share/doc/wput*/.  I was playing around w/ it just now and realized that it won't put empty files up to the server.  Interesting.  It will also skip files that are newer on the server.  Hope this helps...

---

### Post by Nunyah on 2006-04-27
That explains it, the files where just empty test files. Works like a charm now! ;)

Thanks man, appreciate your input!

---

