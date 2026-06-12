---
title: "How can I search for files in linux?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-28
In windows seaching was something very easy .. it's about F3, a short hint or a destination and the search is done. now what about linux ... if I need to search for certain files or destination, what is the linux command for that?

---

### Post by frodon on 2006-04-28
Similar thread here : [http://ubuntuforums.org/showthread.php?t=166775](http://ubuntuforums.org/showthread.php?t=166775)

If you're using gnome you have a search tool in the menu which is quite good.

---

### Post by Rinzwind on 2006-04-28
There are several ways.

From aTerminal:

**sudo find / -name {something} -print**

Use . instead of / to search from where you are (pwd shows where you are).
{something} can have wildcards (3 of them: * and ? and []).

Which finds the 1st executable that equals your searchterm and that's in your PATH.

**which {something}**
/usr/sbin/{something}

**locate {something}**

Locates requires you to make a database 1st and that database needs to be recreated once every while. 

But you can also use Konqueror or Nautilus and in the gnome menu there's a search too.

EDIT: oh and Beagle is becomming a favourite for lots of people.

---

### Post by Isoss on 2006-04-28
Thanks ... I didn't notice that I have a search tool .. anyway, about the commands .. can you please make them more clear?

---

### Post by garner_nc on 2006-04-28
Check the man pages for more information. At a terminal prompt type:

man find

man locate

man which

man whereis

This should give you plenty of information.

All the Best,
Doug White

---

