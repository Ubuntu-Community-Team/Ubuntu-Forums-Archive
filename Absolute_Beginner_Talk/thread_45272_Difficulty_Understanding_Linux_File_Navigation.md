---
title: "Difficulty Understanding Linux File Navigation"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-06-29
I've spent about four hours out of the past twenty-four unsuccessfully trying to understand how to get around the Linux file system to locate files and directories.

Here's an example:  I'm trying to open an .AVI file I have in the directory:

/home/anonymous/.aMule/Incoming/

...and get that directory configured for A/V programs.  OK, so I go to the "Computer" pull down and navigate to: 

/home/anonymous/

But there's nothing further there conected with the rest of this stuff.  It's a dead end.

OK, so I do a search for the file, which I know is at least somewhere on the system, because I see it listed in my completed downloads in aMule.  No dice.  I do a search for any .AVI file.  No dice. 

Even given Linux's obscure and unintuitive file and directories structure, I don't understand how this can be so difficult.

Can someone explain this rat's nest to me or point me to a tutorial page?

What am I doing wrong?

As always, many thanks for any help!

---

### Post by gammyhand on 2005-06-29
[QUOTE=polo_step]I've spent about four hours out of the past twenty-four unsuccessfully trying to understand how to get around the Linux file system to locate files and directories.

Here's an example:  I'm trying to open an .AVI file I have in the directory:

/home/anonymous/.aMule/Incoming/

...and get that directory configured for A/V programs.  OK, so I go to the "Computer" pull down and navigate to: 

/home/anonymous/

But there's nothing further there conected with the rest of this stuff.  It's a dead end.

OK, so I do a search for the file, which I know is at least somewhere on the system, because I see it listed in my completed downloads in aMule.  No dice.  I do a search for any .AVI file.  No dice. 

Even given Linux's obscure and unintuitive file and directories structure, I don't understand how this can be so difficult.

Can someone explain this rat's nest to me or point me to a tutorial page?

What am I doing wrong?

As always, many thanks for any help![/QUOTE]
 I am a noob so I can't really help but this might be of use to you. Linux is case sensitive. file.avi and file.AVI are not the same. So if your file has a lowecase extension and you are searching in uppercase it won't find anything.

---

### Post by Leif on 2005-06-29
I'm not sure I follow you. Is the file under /home/anonymous/.aMule/Incoming/ or not ? Under nautilus, hidden directories (those starting with .) are not shown by default, but if you press ctrl+H you can see them. Is this what your problem is ?

---

### Post by jsimmons on 2005-06-29
.aMule is probably a hiddle folder.  Go to the View menu (in Nautilus) and click "Show Hidden Files".

---

### Post by polo_step on 2005-06-29
[QUOTE=Leif] hidden directories (those starting with .) are not shown by default, but if you press ctrl+H you can see them. Is this what your problem is ?[/QUOTE]
I'm sure it must be at least part of it. I didn't know that bit about the "." indicating it was hidden.  If it's hidden...well...that really works! :smile: 

What a dumb glitch for a program to make its download directory hidden!  That's crazy...

How do I turn off hidden files?

Thanks!

---

### Post by Sionide on 2005-06-29
like they said, it's Ctrl+H or View->Show Hidden Files...

In a terminal you could do it easily, just do cd ~/.aMule/Incoming (~ is the shortcut for /home/username/ ) and what's more, if you typed .a and pressed tab, it'd complete the rest for you :)

---

### Post by rmjokers on 2005-06-29
To make the directory non-hidden, all you have to do is rename it.  There is nothing special about hidden files / folders in linux.  Most applications just treat those with a '.' at the beginning of the name as such.  You probably also have to let Amule know that the incomming directory has moved somewhere else (this might be somewhere in the application preferences?)

---

### Post by polo_step on 2005-06-29
It's all cool now.

I see what I needed to find, though I didn't notice a global setting to show ALL hidden files on the system.

It'll turn up if it's there.

Thanks to all who helped!

---

### Post by Kvark on 2005-06-29
As everyone else has said. Ctrl+H shows all hidden files. you can also go to "View -> View hidden files" from the menu on top. This setting stays next time you open a folder. It stays until you turn it off.

---

### Post by jsimmons on 2005-06-29
[QUOTE=Kvark]you can also go to "View -> View hidden files" from the menu on top. This setting stays next time you open a folder. It stays until you turn it off.[/QUOTE]


Umm, I beg to differ. When you shut down nautilus and re-open it again, the hidden files/folders are once again hidden.

---

### Post by skirkpatrick on 2005-06-29
For a permanent solution to any of Nautilus' settings, go to System->Preferences->File Management.  In the View tab, you'll see a checkbox for "Show hidden and backup files".

---

### Post by Kvark on 2005-06-29
[QUOTE=jsimmons]Umm, I beg to differ. When you shut down nautilus and re-open it again, the hidden files/folders are once again hidden.[/QUOTE]

For me the setting stays.

---

