---
title: "how to fix wine for dapper 6.06"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by slirock on 2006-11-17
I am trying to install wine and I dont know what to do I am getting this message

 
E: type http://wine.budgetdedicated.com/apt' is not known on line 39 in source list/etc/apt/source.list
E: The list of sources cound not be read
 Go to the repository dialog to correct the problem.
E:Type:type http://wine.budgetdedicated.com/apt' is not known on line 39 in source list/etc/apt/source.list
E: Unable to lock the list directory



I really need help what do I do to install and fix?

Thank you
 Slirock

---

### Post by nazgulord on 2006-11-17
Could you please list the exact procedure you followed to get to this point (eg: how you installed wine - synaptic, from the WineHQ repositories, compiled from source, etc. along with any other relevant info)?

nazgulord.

---

### Post by slirock on 2006-11-17
I went to the synaptic package manager then went to repositories under settings clicked add then customand added the typed in http://wine.budgetdedicated.com/apt' and several other commands i followed some thread screwed it up i am new at this.

thanks

---

### Post by slirock on 2006-11-17
What do I do?

---

### Post by YokoZar on 2006-11-17
I believe you forgot to put the "deb" at the beginning.

Try opening a terminal window, and run sudo gedit /etc/apt/sources.list

The bottom should be something like this:

deb http://wine.budgetdedicated.com/apt dapper main


whereas I believe you have this:
http://wine.budgetdedicated.com/apt dapper main

---

### Post by CatKiller on 2006-11-17
> **YokoZar said:**
> I believe you forgot to put the "deb" at the beginning.

Try opening a terminal window, and run sudo gedit /etc/apt/sources.list

That was the conclusion I'd come to as well. But they should use **gksudo gedit...** or **sudo nano...** instead.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Or edit the line in Synaptic, of course.

---

