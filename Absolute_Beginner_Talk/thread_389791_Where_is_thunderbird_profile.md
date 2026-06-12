---
title: "Where is thunderbird profile?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2007-03-21
HI!

I have to reset my computer back to its factory settings, this is due to Windows playing up again!!  The thing is I suspect that it will wipe the hard drive of everything so I am saving all my data before I do it.  I checked the mozilla website and found how to backup my emails, but I can't find where the profile folder is on Ubuntu.  Mozilla say it is here > ~/.thunderbird/<Profile name>/ or possibly ~/.mozilla-thunderbird<Profile name>  but how do I find that?  There are so many places to look.

Also, if anyone has any tips on how to backup Ubuntu easily, I would like to know.

Russty.

---

### Post by eljalill on 2007-03-21
As far as I read this, it says that the file is in 
/home/username/.thunderbird.......etc
the ~  usually refers to your home directory.

Or was it something else you were asking?

---

### Post by Obor on 2007-03-21
~/ = /home/username
Therefore it should be in /home/yourusername/.mozilla-thunderbird

---

### Post by Russty of Oz on 2007-03-21
Well when I go to home/russty/ there are just my general folders that I have made, such as photos, videos etc. no mention of thunderbird or any other programs.  I thought they might be somewhere in File System, but that is such a mine field.  Is there a command I can type into a terminal to find the thunderbird folder?

---

### Post by eljalill on 2007-03-21
you can try locate .
Else you have to enable hidden files:
ls -a or Cntrl H in nautilus, to see the folder
Folder starting with "." are hidden. :)

---

### Post by Russty of Oz on 2007-03-21
I tried nautilus and this is all that showed up. :(

---

### Post by adam s on 2007-03-21
use a terminal and type :

cd ~
ls -la

this will show all your hidden directories.

Adam.

---

### Post by Russty of Oz on 2007-03-21
OK, that did it!! :) 

Thanks guys!  now I can get on with it.

Much appreciated

Russty ):P

---

### Post by eljalill on 2007-03-21
Possibly you didn't find it in nautilus, because you were in root's home folder, not in your own home folder... unless you always log in as root...

Good to know, that the problem is solved :)

---

