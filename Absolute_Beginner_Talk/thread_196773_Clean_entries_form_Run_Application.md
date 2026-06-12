---
title: "Clean entries form Run Application"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by someusernoob on 2006-06-14
You know: alt+F2 - Run Application

I got a list of old entries and i want them out of there!  :-({|= 

How? :confused:

---

### Post by someusernoob on 2006-06-15
A little bump. Really cant find the file which is holding those commands for me.

---

### Post by bruce89 on 2006-06-15
These are all commands that will work, why do you want to remove them?

---

### Post by someusernoob on 2006-06-15
I have one application that i open very often with alt+F2, and its in that list, but there are some other commands before i "scrolled" to that specific command. And i want to save myself some time scrolling so emptying that list and putting in one new entry is just what i wish for.

Note: i'm not talkin about that list of applications when you click "Show list of known applications". Im talkin about that entry field. The thing where you can type commands, that thing is full of sh*t. I WANT IT EMPTY lol, im getting tired of that thing.

---

### Post by bruce89 on 2006-06-15
No, I don't think so, but you could create a menu launcher for it.  Just right-click on the Applications menu, and select edit menus.

---

### Post by someusernoob on 2006-06-15
No, thats is not what im looking for. I want a solution for my problem, not an alternative.

But say, all those commands i type in alt+F2 has to be stored somewhere. And if there is no way of deleting them, i just can go on and on typing different commands until the file that keeps them reaches the disk limit...?* So there must be a way to clean that stupid field. No-one seems to know how :S

*Im not planning on doing that, but it is possible.

---

### Post by bruce89 on 2006-06-15
They are just taken from the list of commands that can be run, there is no way to delete any.  If you mean the drop down list on the right of the field, it doesn't appear so.

---

### Post by someusernoob on 2006-06-15
No, if i type 12SFG154DSAFDSAWET for example, it stores it, and it is not a existing command.

---

### Post by bruce89 on 2006-06-15
[QUOTE=someusernoob]No, if i type 12SFG154DSAFDSAWET for example, it stores it, and it is not a existing command.[/QUOTE]
Damn, now that's in my list too.  Does anyone else know the solution?

---

### Post by someusernoob on 2006-06-15
lol, i didnt say you had to try it. It's driving me mad since i started this thread. There really must be a way to get that field clean.

---

### Post by bruce89 on 2006-06-15
I think not putting in bogus commands might help in the future.

---

### Post by someusernoob on 2006-06-15
Well, i made an extra account in my ubuntu install in VMware, and that starts with a clean alt+F2 entry menu, so the file must be somewhere in your own /home/user folder.

I will find it, i wont go to sleep before i do.

Hopefully i will find it. Otherwise i dont get much sleep. lol.

---

### Post by someusernoob on 2006-06-15
I am tired and im really mad about this thing, so i deleted everything in the home folder of the 2nd user and the entry field is empty again. But i went through all the files, but couldnt find any of the entries i putted in. So it is in your /home/ folder somewhere, but i do not know which specific file. AAARRGH. 

Why did they had to make this so friggin hard??

---

### Post by measure on 2006-06-15
Perhaps a hidden file/folder?

---

### Post by bruce89 on 2006-06-15
[QUOTE=measure]Perhaps a hidden file/folder?[/QUOTE]
Obviously, tried those.

---

### Post by someusernoob on 2006-06-15
One step closer to the solution :-$ 

(note: everytime i try something i have to log out and in for it to work, that takes a lot of time)

There are 2 hidden folders in the home/user/ dir that (as it seems) co-operate:
.gconf
.gconfd

When deleting one of the 2 the entrybox isn't clean.
When deleting both the entrybox is CLEAN!!

So im 100% sure it are those 2 folders that make me mad.

But! there are a lot of setting files (.xml) in there, and i will not break my own desktop down. So i have to spend more time to find the excact file and code that keeps those entries.

I also tried to remove those 2 folders, and copy-paste them back after i login, but that doesnt work, the entrybox contains the nasty entries again.

Anyone knows if there is a program that can compare files on the contents of the file? So it let me see what file has a different code from the other and what the difference is? Or something... :-({|=

Can do that myself but it could take a whole day...

NOTE:!! I did this in a Virtual Machine, with a clean Ubuntu install with a fresh user!, dont do this with your own account, there are a lot of important settings that can break your whole configuration down!!!

---

### Post by someusernoob on 2006-06-15
And i was thinking about installing Ubuntu again. I have my /home folder on another partition, so settings and data for programs like thunderbird and firefox are safely stored. But after i know this that wouldnt even help to get that entrybox clean. 

I really would've thrown my computer out of the window, when after a fresh install those entries were still there. lol

---

### Post by someusernoob on 2006-06-16
Got the solution

```

Clean gconf key /apps/gnome-settings/gnome-panel/history-gnome-run (use gconf-editor)

```


:rolleyes:

---

