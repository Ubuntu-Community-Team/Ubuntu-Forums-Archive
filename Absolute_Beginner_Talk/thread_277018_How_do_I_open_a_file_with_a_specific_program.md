---
title: "How do I open a file with a specific program?"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by dolphinsonar on 2006-10-13
I am trying to figure out how to open this bit torrent using my newly downloaded, Ktorrent.  When I go to open it, it asks me which program I want to open it with, I try to select Ktorrent from the menu but it is not there:
[IMG]http://static.flickr.com/91/268911159_2396148161_m.jpg[/IMG]
So I hunt around on the hard drive looking for the program, but I have no idea where it is located, since I used apt-get to download it.  I don't really have a conception of where things go after they are installed.  I tryed to hit "Ctrl H" to find the hidden files in my "home" directory, figuring the programs would be there, but they are nowhere to be found.  Any help is appreciated.
[IMG]http://static.flickr.com/87/268911160_23e568597a_m.jpg[/IMG]

---

### Post by meng on 2006-10-13
Look inside /usr/bin, a lot of programs are run from there. Otherwise, from command line type:
which ktorrent

---

