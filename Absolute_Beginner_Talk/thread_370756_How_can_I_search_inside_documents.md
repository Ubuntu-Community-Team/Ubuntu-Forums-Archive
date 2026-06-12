---
title: "How can I search inside documents?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-02-26
Is there a way to search not just for words contained in the document title but also inside the documents (without having to open all the documents individually, I mean)?
I. e. is there a way or software to search for file contents?
Like what Sherlock does for MacOS.
Thanks.

---

### Post by floke on 2007-02-26
Depends what search tool you are using.
If you use the applet for the gnome panel (right click panel; select 'add to panel'; select 'search'; click 'add'). Then click the search applet; and select the 'more options' bit to search in text.

---

### Post by girishv on 2007-02-26
If you are searching for a pattern in an ascii file, you can use grep

grep searchword filename

You can use different switches and wildcard entries too.
For a case insensitive search, use -i
For a recursive search, you can use -r like

For example, a case insensitive recursive search can be done with
grep -ri searchword *

This will search for all the files in the directory and sub-directories. Check out the manual pages for other flags

Girish

---

### Post by Blofeld on 2007-02-26
@Steve:  Alas, Xfce (Xubuntu) offers no such nifty search applet.

---

### Post by mcduck on 2007-02-26
> **Blofeld said:**
> @Steve:  Alas, Xfce (Xubuntu) offers no such nifty search applet.

You can run Gnome panel applets inside XFCE panel.

But to search inside files with Deskbar you need to also install Beagle.

---

### Post by Blofeld on 2007-02-26
@Steve:  Did you mean Beagle?  Thanks for the hint, I'm looking into it.

---

### Post by Blofeld on 2007-02-26
I have installed Beagle but unfortunately it doesn't search RTF text documents.

---

### Post by Blofeld on 2007-02-26
... nor hidden files or directories.

---

### Post by amd-64 on 2007-02-26
You can use beagle-settings to force beagle to search any directory (hidden on not). 

Note that beagle runs with user permissions only. Your user  must have read permissions to any file or directory they wish to index.

---

### Post by CCBalla10 on 2007-02-26
are you just talking about using ctrl + F to find something in a document?

---

### Post by Blofeld on 2007-02-26
@CCBalla:  No!

---

### Post by Adramelech on 2007-02-26
use grep as girishv said.
remember to: man grep for options

---

### Post by Blofeld on 2007-02-27
Can I search directories (= a collection of files) with grep?  Coz that's what I'm after.  Thanks.

---

### Post by Blofeld on 2007-02-27
Hey, I eschewed having to use my brain or the command line by going for Beagle and Searchmonkey.:guitar: 
Both work great, except that they won't find Umlaute ("Dürüm Döner"), which cost me about half a day to find out.

---

