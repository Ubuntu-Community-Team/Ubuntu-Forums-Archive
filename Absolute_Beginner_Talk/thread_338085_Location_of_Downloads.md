---
title: "Location of Downloads"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-01-13
I'm having trouble finding files that I have downloaded. For example: Using Synaptic, I downloaded gimp-help-common and openclipart-svg. But when I did a file search for them, it said NO SUCH FILE. 
    I assumed that clipart was a file that I could use to import art, but where is it?
And when I tried to use HELP on Gimp, I had to download gimp-help-en so that it would work.
Any help would be greatly appreciated.

---

### Post by MkfIbK7a on 2007-01-13
well you need both
gimp-help-common 
and
gimp-help-en
to look at the help on gimp

i dont know what openclipart is but if you do
alt+F2
and type the name see what happens
also try to find it in 
/usr/bin/
in nautilus

---

### Post by ComplexNumber on 2007-01-13
did you install them or merely download them? if you installed them and are wondering where the files are installed, you need to fire up synaptic, highlight the file (eg gimp-help), select 'properties', then click on the 'installed files' tab.

---

### Post by Stunt Double on 2007-01-14
When I was selecting files to download, Synaptic was flagging other required files but I guess it missed gimp-help-en.  At any rate, Gimp help does now work even though I can't find the common file.
 Synaptic says that openclipart-svg was installed. Perhaps Synaptic failed to flag another dependency.
   Openclipart-svg isn't in any of the suggested locations. In the future, I'll use aptitude to install. Hopefully, it will do a more complete job.

---

### Post by Madpilot on 2007-01-14
Synaptic installs the Open Clip Art packages just fine.

The trouble is that the stuff then gets buried deep in / space...

/usr/share/openclipart/

... to be exact.

Setting up a symlink from your home directory into /usr/share/openclipart is the easiest way to get at the stuff.

---

### Post by Stunt Double on 2007-01-14
Thanks to all for the help.
Is there a way to search for the file? I tried both "which openclipart" and file search. Neither one produced the location of the file. Is there a more effective way to search?

---

### Post by haiku99 on 2007-01-14
> **Stunt Double said:**
> Thanks to all for the help.
Is there a way to search for the file? I tried both "which openclipart" and file search. Neither one produced the location of the file. Is there a more effective way to search?

there is!...in a terminal window type wheris programname  and the locations of the various program files are displayed

e.g 

bill@bill-laptop:~$ whereis gimp
gimp: /usr/bin/gimp /etc/gimp /usr/lib/gimp /usr/X11R6/bin/gimp /usr/bin/X11/gimp /usr/share/gimp /usr/share/man/man1/gimp.1.gz
bill@bill-laptop:~$

---

### Post by Stunt Double on 2007-01-14
"Whereis" did find openclipart but the response for gimp-help-common was "gimp-help-common:"  What does the colon signify? Where is that file?

---

