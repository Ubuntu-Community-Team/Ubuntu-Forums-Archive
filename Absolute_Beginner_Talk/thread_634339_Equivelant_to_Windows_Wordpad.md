---
title: "Equivelant to Windows Wordpad"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by HDave on 2007-12-07
I've found gedit...its a good replacement for windows notepad.

But gedit doesn't let me format text.

I'm looking for a way to edit a text document with formatting in a lightweight manner -- open office word processor is too heavy.

I'd take (and actually) prefer a WYSIWYG XHTML editor...

Tomboy  comes close, but the UI is to simple-minded...

---

### Post by Crashmaxx on 2007-12-07
Might want to try abiword, it is a WYSIWYG editor and much lighter then openoffice.org, just do:
```

sudo apt-get install abiword

```
to install.

---

### Post by Jerry N on 2007-12-07
Abiword can be installed through "Add/Remove" under the "Applications" menu

Jerry

---

### Post by nikoPSK on 2007-12-07
Also if you inatll wine you get notepad by default.....

---

### Post by HDave on 2007-12-07
Installed and tried Abiword.

It's exactly what I was looking for...thanks.

---

### Post by ericesque on 2007-12-07
Consider Bluefish-- with support for syntax highlighting for the following languages

Python 
HTML 
PHP 
C 
Java 
JavaScript 
JSP 
SQL 
XML 
Perl 
CSS 
ColdFusion 
Pascal 
R 
Octave/MATLAB 

Install using Add/Remove Applications...

---

### Post by ericesque on 2007-12-07
Another note,  you can typically increase the speed which OpenOffice starts quite a bit by following these quick tips:

[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

The most important options here are disabling the Java settings and increasing the memory used by OpenOffice.  By default it is set to 6MB. Whereas MS Office is probably 10 fold that amount.

---

### Post by stchman on 2007-12-07
> **HDave said:**
> I've found gedit...its a good replacement for windows notepad.

But gedit doesn't let me format text.

I'm looking for a way to edit a text document with formatting in a lightweight manner -- open office word processor is too heavy.

I'd take (and actually) prefer a WYSIWYG XHTML editor...

Tomboy  comes close, but the UI is to simple-minded...

Gedit is like notepad on steroids but it is only a text editor.  Wordpad for Windows is not a tru text editor but a poor man's word processor.  I mean Wordpad doe not do syntax highlighting, etc.  Abiword would be a an alternative for you I agree.

---

### Post by stchman on 2007-12-07
> **ericesque said:**
> Consider Bluefish-- with support for syntax highlighting for the following languages

Python 
HTML 
PHP 
C 
Java 
JavaScript 
JSP 
SQL 
XML 
Perl 
CSS 
ColdFusion 
Pascal 
R 
Octave/MATLAB 

Install using Add/Remove Applications...

I think Gedit is a better editor for programmers than Bluefish IMO.  I don't like the fact that Bluefish does not do matching brace highlighting.  If it does how to you enable that?

---

### Post by HDave on 2007-12-07
> **ericesque said:**
> Consider Bluefish-- with support for syntax highlighting for the following languages


I checked it out. I like the idea of editing the HTML, but it is not WYSIWYG so currently it looks like Abiword.

---

### Post by cerealtx on 2007-12-07
i currently use Kate to do all my html/css/php/mysql programing, yall should take a look at it, i like it :P can be found in SPM search 4 kate

---

### Post by HDave on 2007-12-07
Kate looks good, but I am running Gnome...heard all sorts of scary things about running KDE apps in Gnome.

As a total aside -- given the limited resources of the open source community this whole KDE vs. Gnome thing is irking the crap out of me....  Why can't they get together!!!

---

### Post by stchman on 2007-12-08
> **HDave said:**
> Kate looks good, but I am running Gnome...heard all sorts of scary things about running KDE apps in Gnome.

As a total aside -- given the limited resources of the open source community this whole KDE vs. Gnome thing is irking the crap out of me....  Why can't they get together!!!

I run lots of KDE apps under Gnome with no problem.

K3B
Ktorrent
k9Copy
Gwenview

---

