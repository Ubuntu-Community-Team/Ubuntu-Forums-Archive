---
title: "the &quot;man&quot; pages"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-06-17
Where does this Info come from? some where on the internet? or text files on the computer?

---

### Post by catlett on 2006-06-17
> man - an interface to the on-line reference manuals Just run```
 man man
```
To get the whole run down.

---

### Post by 5-HT on 2006-06-17
Just to add to catlett's post, the man pages are kept locally on your system and  are gzipped to help save space. 'man' handles the decompression.

HTH

---

### Post by adam.tropics on 2006-06-17
Also, if you go [here]("http://mycroft.mozdev.org/download.html?name=&submitform=Find+search+plugins") and let the page load (it's huge!), you will find a man search which runs from your firefox searchbar, as well as a couple handy ubuntu ones. I wouldn't mention it except to say, should you happen to use deskbar in your panel, by default your firefox search plugins work with that too.And whilst it's just personal preference, man pages are a lot less intimidating when nicely formatted in a browser window.

---

### Post by blair on 2006-06-17
The man pages you see when you use the man command are physical files residing on your PC. They can also be found on the Internet as a convenience n Linux documentation sites. 

If you run the command whereis [command name], e.g. whereis ls, whereis dir, whereis cd, etc. it will list the directories where commands and files associated with that particular command reside. Do this a few times and you can see that the man pages for most system command reside in the directory /usr/share/man. Any apps you install on your own may or may not install their man pages in the same directory. 

If you look in the man folders, you will see that the man pages are actually individually compressed files. These files are uncompressed on the fly and loaded into a viewer program by the man program when you run the man [command name] command. The files are specifically meant to be used by the man command. If you want to read it with some other viewer, there are sophisticated hacks that make it possible, but it is a lot easier to just view the HTML files available on the Internet using a browser.

---

### Post by catlett on 2006-06-17
[http://man.splitbrain.org/](http://man.splitbrain.org/) I find it easier to read a man page from this site. It has all the man pages and they are given a fill web page to be displayed in as opposed to a terminal, text output.

---

