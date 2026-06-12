---
title: "Delete Multiple Files All In One Go."
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by tickmike on 2007-01-16
If I do a 'Search' for files and find 163 I want to remove all at once, How do you do it ?

On the search engine it will not let me send them to the  'wastebasket'

The problem I have installed multi lots of realplayer in various locations and want to remove them, then start again.

sudo apt-get remove realplayer     does not work   'cannot find'

Its not in add/remove program because 'synaptic package manager' will not let me mark it , has to be downloaded from the real site ( that's what I did).

Michael.

---

### Post by zerhacke on 2007-01-16
Highlight all the files listed on the search tool and right click them.  Delete should be one of the options listed.

To highlight more than one file hold down the control key and click each file you wish to delete.  Alternatively, highlight one file and press CONTROL and A at the same time, which will highlight every file.

---

### Post by tickmike on 2007-01-16
Hi zerhacke.
 You put....Highlight all the files listed on the search tool and right click them. Delete should be one of the options listed.
I put in my first post....
**On the search engine it will not let me send them to the 'wastebasket'**

Next idea.:)

---

### Post by JuCa_Elite on 2007-01-16
You would have to go and find each individual file.

---

### Post by tickmike on 2007-01-16
What 163, there's got to be an easier way !  :-k

---

### Post by chipdip on 2007-01-16
OF COURSE THERE IS! :p 
Highlight the file(s) by holding CTRL and selecting each file and hit DEL on your keyboard. ;)

---

### Post by ardchoille42 on 2007-01-16
You can open a terminal, write rm and then put a space, then open nautilus and drag and rop each file into the terminal. When all files are in the term, press the ENTER key.

Are all these files in the same place or have the same file extension?

---

### Post by tickmike on 2007-01-17
Can you open the 'search' under 'root'  with 163 files it will be a big job to go and look for them under 'nautilus'

something like        'sudo search'     ?.

---

### Post by zerhacke on 2007-01-17
> **tickmike said:**
> Hi zerhacke.
 You put....Highlight all the files listed on the search tool and right click them. Delete should be one of the options listed.
I put in my first post....
**On the search engine it will not let me send them to the 'wastebasket'**

Next idea.:)

It will delete them to the wastebasket, tickmike.

---

### Post by Ben Sprinkle on 2007-01-17
> **tickmike said:**
> Can you open the 'search' under 'root'  with 163 files it will be a big job to go and look for them under 'nautilus'

something like        'sudo search'     ?.

```

sudo locate *keyword*

```
I think.

---

### Post by tickmike on 2007-01-17
Hi ,
    Done it,  :D 
Thank you all for your help.

sudo gnome-search-tool

opens up the search tool in root , then it let me delete or put in the wastebin.

Michael :cool:

---

