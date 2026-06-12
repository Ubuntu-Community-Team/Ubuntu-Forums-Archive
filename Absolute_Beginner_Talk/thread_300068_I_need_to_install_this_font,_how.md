---
title: "I need to install this font, how?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by wadehel on 2006-11-15
I have to see some presentation made using powerpoint, the maker use the font i attached (zipped), but how to install this font on ubuntu?

Help please, without this font, the file cant be understand properly.


TIA.

---

### Post by Perfect Storm on 2006-11-15
Make a new folder in your home folder called **.fonts** and put your fonts in there. (Note that folders with a . infront will be hidden. To make it work with the font issue there have to be a . infront of the name of the font folder).

---

### Post by yabbadabbadont on 2006-11-15
[http://www.ubuntuforums.org/showpost.php?p=1756711&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1756711&postcount=2)

Basically just create a .fonts directory in your home directory and put the font file there.  It should then be available.

EDIT: Too slow.  :D

---

### Post by wadehel on 2006-11-15
I dont think that will be so so easy!!!

thankyou thankyou thankyou for both of you

I hope God give the best heaven for all of you. amen :D

---

### Post by azurehi on 2007-02-18
I have this font in my .font folder:  /home/neil/Desktop/zekton__.ttf
How do I get it to the preferences/font fold so I can use it as my preferred font?  Or, from /home/neil/Desktop/50553-zekton.tar.gz
how do I accomplish the same thing, i.e., use as font?  I am obviously a Noob!  Any help much appreciated.:confused:

---

### Post by yabbadabbadont on 2007-02-18
> **azurehi said:**
> I have this font in my .font folder:  /home/neil/Desktop/zekton__.ttf
How do I get it to the preferences/font fold so I can use it as my preferred font?  Or, from /home/neil/Desktop/50553-zekton.tar.gz
how do I accomplish the same thing, i.e., use as font?  I am obviously a Noob!  Any help much appreciated.:confused:

Short answer, read the second post in this thread...  :D

Long answer.  Open a terminal window.  Run, "mkdir -p ~/.fonts" (without the quotes).  Copy the font file to that new directory, "cp ~/Desktop/zekton__.ttf ~/.fonts" (without the quotes).  If it doesn't show up in the list of available fonts after that, logout so that you are at the graphical login screen.  Then hit ctrl-alt-backspace all at once.  That will force X windows to restart (not the computer, just X windows).  Login and the font should be available now.

Edit: Here are the commands in a format that will be easy to cut and paste.
```
mkdir -p ~/.fonts
cp ~/Desktop/zekton__.ttf ~/.fonts
```

---

