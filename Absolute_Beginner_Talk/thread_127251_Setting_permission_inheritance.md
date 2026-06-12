---
title: "Setting permission inheritance"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by pinkfloyd65 on 2006-02-08
I'm sorry if I sound too Windows-ish, but that's because I am new to Ubuntu. I want to start introducing Ubuntu into our non-profit Agency and I recently downloaded a trial version of Crossover Office (Standard Ed.). I created some users and a "Documents" folder in their respective /home directory. In there, I dumped a few Word and Excel documents and started to "play" with them. 

_[COLOR="Black"]**My problem:**[/COLOR]_

As root, I made sure that the permissions for that "Documents" folder are set to 777, however, when I check individual permissions on files inside the folder, all show 555. Obviously, in this case, if I atempt to save any changes on a file, Word will complain that it cannot save because of a permission restriction.

[COLOR="Magenta"]**_[COLOR="RoyalBlue"]My Question[/COLOR]_**[/COLOR]

How do I make sure that assigned permissions at the folder level will be inherited by *all *files and sub-folders within that "mother" folder. I'm sure that there must be a better way to have permissions replicated than to just change them for each file individually, but all I tried just doesn't seem to accomplish that.

Thank you in advance for your help.

---

### Post by Bicko on 2006-02-08
Hi PinkFloyd65,

Sorry, I don't have the answer to your problem, but I DO have the exact same issue and am eagerly waiting for somebody to post the solution;) 

I have a whole directory structure to change, just the 'group' name will suffice (but I'd like to chmod 0770 it all really as well), and I have perhaps hundreds of subfolders each containing many files.

I was hoping nautilus would have a 'tick box' to enable the new 'group' setting to cascade down through the sub-directories.  Perhaps there's a command-line approach?

Regards,
Bicko.

---

### Post by aysiu on 2006-02-08
```
sudo chmod -R 777 /home
```

---

### Post by pinkfloyd65 on 2006-02-08
That did it for me!

Thanks:KS

---

### Post by Bicko on 2006-02-08
... and me!

sudo chmod -R 777 /home
   and
sudo chown -R :newgroup /home

Thanks.

---

### Post by David Corrales on 2006-02-08
I think 777 is way too open unless you're the only user on the machine... but still.
Remember permissions go as following:
```

**Owner - Group - Others**
*XXX- XXX - XXX*

```
So, by making them 777 everyone can read/write/execute any file. That's not what you ideally want. For directories, you'll usually want to allow "execution" or else you won't be able to access them :) but for regular documents, set execution to 0 and let yourself and the group r/w while others just read for example. That'd be 640 :)

---

### Post by pinkfloyd65 on 2006-02-09
Thanks for the advice. I restrict permissions on Windows shared folders and know how to allow/remove inheritance but in this case, I am testing the functionality of Crossover Office and was trying to change files using MS Word. Word kept giving a permissions-error message and that's why I started looking into this and decied to "go all the way" in order to see that it's actually a file permission issue rather than a Crossover issue. 

I wonder if command line is t**_he only way_** to change permissions on a folder and have those permissions inherited by all the files included within....In Windows one has pretty specific choices when it comes to setting permissions on a folder on an NTFS partition and all is GUI. Is there some thing like that in Ubuntu?

---

### Post by matthinckley on 2006-02-13
chmod -R 777 only changes existing files and all subfolders and files contained that currently exist.. any new files created will not have the 777 permissions

I also have the same problem..

me and my wife use the same computer and I would like to be able to have a folder that we could both dump documents or pictures into and both have read/write permissions, but I can't figure out how to do this... I can have a folder we can both dump into but if she puts pictures in it, I can't do anything with them and vice versa..

---

### Post by aysiu on 2006-02-13
[QUOTE=pinkfloyd65]
I wonder if command line is t**_he only way_** to change permissions on a folder and have those permissions inherited by all the files included within....In Windows one has pretty specific choices when it comes to setting permissions on a folder on an NTFS partition and all is GUI. Is there some thing like that in Ubuntu?[/QUOTE] There's a GUI option for this in Konqueror, just not in Nautilus.

---

### Post by aysiu on 2006-02-13
[QUOTE=matthinckley]
me and my wife use the same computer and I would like to be able to have a folder that we could both dump documents or pictures into and both have read/write permissions, but I can't figure out how to do this... I can have a folder we can both dump into but if she puts pictures in it, I can't do anything with them and vice versa..[/QUOTE] I think what you're looking for is *chown*, not *chmod*. *chown* **ch**anges **own**ership of the folders/files.

There are two owners--the owner and the owner's group. Maybe you could make you and your wife the same group (say, *users*)--this can be done in System > Administration > Users and Groups or KUser, depending on whether you're using Gnome or KDE.

Then, let's say you share a folder called /home/pictures
You can try ```
sudo chown -R matt:users /home/pictures
``` See if that makes a difference.

---

### Post by matthinckley on 2006-02-13
Thanks Aysiu.. i think my problem is different  than i thought.. posted new thread..

[http://www.ubuntuforums.org/showthread.php?t=129132]("http://www.ubuntuforums.org/showthread.php?t=129132")

thanks 

Matt

---

