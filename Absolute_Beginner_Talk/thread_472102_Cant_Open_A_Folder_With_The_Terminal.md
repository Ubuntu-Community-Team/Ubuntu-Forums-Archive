---
title: "Cant Open A Folder With The Terminal"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-06-12
Yeah, with a while invested in Ubuntu, this is still a very 'beginner' question... 

Im trying to put a shortcut to my Windows desktop on my top panel. 

If I go to a terminal and type:

nautilus /home/user/pictures

for example, everything works fine. Nautilus opens up to that directory. Good so far...

If I type:

nautilus /media/Windows/shared

It once again works just fine opening nautilus to that directory.

BUT, if I type:

nautilus /media/Windows/Documents and Settings

It pops up 3 error messages, saying it cant open /../../Documents, /../../and, etc. Does nautilus support opening a file directory containing spaces? Ive tried using Documents_and_Settings, etc, but Ive had no success. How do I open these kinds of directories from the command line?

---

### Post by PgR on 2007-06-12
Try putting a \ before the spaces in "documents and settings"

nautilus /media/Windows/Documents\ and\ Settings

---

### Post by GSF1200S on 2007-06-12
> **PgR said:**
> Try putting a \ before the spaces in "documents and settings"

nautilus /media/Windows/Documents\ and\ Settings

That did it! Thanks alot for the help :)

I would have NEVER thought of that.. :)

---

### Post by yabbadabbadont on 2007-06-12
Just as an FYI, you would have to do the same thing in Windows if you were to create the link manually instead of using Explorer.  You could also have quoted the path "/media/Windows/Documents and Settings" and it would have worked.  (both in Linux and Windows)

---

### Post by Papi-KB7VGW on 2007-06-12
I did it without using the terminal.

Open >Places>sda1 (which I think is the default name for a non Linux partition like windows)
navigate to your documents and Bookmark it.  Then the next time you want to go there it will be in Places.  Hope this helps.

---

### Post by GSF1200S on 2007-06-12
> **yabbadabbadont said:**
> Just as an FYI, you would have to do the same thing in Windows if you were to create the link manually instead of using Explorer.  You could also have quoted the path "/media/Windows/Documents and Settings" and it would have worked.  (both in Linux and Windows)

Hmm.. I didnt know that about Windows..

I tried the link you suggested and I got an error message (3 actually). I must be missing something... The post below my initial one worked flawlessly though.

---

### Post by GSF1200S on 2007-06-12
> **Papi-KB7VGW said:**
> I did it without using the terminal.

Open >Places>sda1 (which I think is the default name for a non Linux partition like windows)
navigate to your documents and Bookmark it.  Then the next time you want to go there it will be in Places.  Hope this helps.

WOW! I never even tried the bookmark option.. of course Ive been using KDE a while. Im currently setting up Ubuntu on my Moms computer, and let me tell you- with what Ive learned trying to make it nice, Im falling in love with Gnome all over again. It lacks a FEW features of KDE, but the speed, stability and simplicity of it more than makes up for its shortcomings. I find I can make Gnome complicated where I want it, but keep it simple otherwise. Not trying to start a flame war.. im just saying I initially VASTLY underestimated Gnome.

---

### Post by Papi-KB7VGW on 2007-06-12
Yes, I prefer the simplicity of Gnome to KDE mostly because KDE seems more like MS while Gnome reminds me of Apple.  My brother is ecstatic about KDE, while my son is an Apple fan.  It make for some lively conversations.

---

