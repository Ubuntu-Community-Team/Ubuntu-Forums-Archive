---
title: "Google Desktop Search can't open text files with Gedit"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by amac777 on 2007-07-03
I installed Google Desktop search today without hassle. It's indexing now. One thing I've already noticed is that if I search for a text file, google's search tool finds it and shows the results in a nice webpage but I can't open the text file directly by clicking the link of it's name on that web based results page. If I click the link, Gedit opens Unsaved Document 1 not the text file I clicked....

Then I tried clicking the "Open folder" link from Google's result page and nautilus opens with the right directory where the text file is. So then I double click the file from within nautilus and Gedit opens Unsaved Document 1 again. ????

But yet if I open nautilus myself by going to Places --> Home folder, I can open all text files by double clicking them  - including the one that doesn't work if I find it via google desktop search. And of course opening the text file from the command prompt using 'gedit filename.txt' works too.

Is anyone else experiencing this?

EDIT: I have found that this only happens if the text file is stored in a directory with spaces in the name. Other files in other directories work, but if there is a space in the directory name then I cannot open it by clicking on it. Looks like a bug to me.

---

### Post by cleverselfreferentialname on 2007-07-05
I tend to believe that cross-platform stuff that hasn't been cross platform very long is not very interested in serving the interests of the Linux community. That is, they only care about people saying "Oh, they support Desktop Linux," not about actually supporting any of the ideological backings of Linux, or supporting it itself.

What I really want is for there to be some really good desktop search method that does indexing properly and can look only in specific dirs (good for all the etexts many of us have accumulated) and return them in a google-esque manner, being searched with a google-esque syntax. Something open source too.

---

### Post by amac777 on 2007-07-05
Well, I use google desktop at work and it seems to basically do what I need. Although it is kind of a security risk if you store all your passwords in a text file hidden in some directory and then find them top of the list after doing a google search. haha At least that's easy to fix - sort of.


But not being able to open text files with spaces in their filenames or in the directory file names seems like a big bug. If others can confirm this I'd like to know. I did a google search and a search on the google desktop group but didn't see anyone else reporting this....

Anyone else install it and find they can't open text files that have spaces in their names somewhere?

---

