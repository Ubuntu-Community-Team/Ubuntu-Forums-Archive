---
title: "problem with c ide anjuta1.2.4a"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by jimboj on 2006-09-02
I just switched to ubuntu. I am starting to get annoyed with my lack of knowledge installing things I download.  I also cannot find any information on it. Whenever I download something and follow the instructions something errors out.  With Anjuta logged in as root at the command prompt: I typed ./configure and it gets a few lines and then errors out saying:
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool:
I've downloaded many things and tried to install them.  So far none have worked - not one!!  Someone please help or I'm going to smash this computer!!!:mad:

---

### Post by cilynx on 2006-09-03
Do you have a reason for trying to compile the source version instead of just grabbing the version in the repositories?
```

sudo apt-get install anjuta

```
That should handle all of your installation dependencies.

And just as an fyi:
```

sudo apt-get install libxml-parser-perl

```
Will take care of installing XML::Parser for you 

Good Luck

---

