---
title: "awn?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by spacebub on 2008-03-17
i saw this website showing how to use awn to get a cool desktop but found some problems.
this is the link:
[http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml](http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml)

one thing im not sure of how to do is all the downloading.  i skipped all of that but now that i'm up to it i'm stumped.  am i supposed to extract the files and then drag them in or what? and how do i save in "/usr/share/nautilus/patterns"??

maybe if someone can read the instructions and help me out or something, that would be great.


by the way, i dont have my panels (i followed the directions but prob'ly messed up) or anything so i don't think i can get to systems, etc (the stuff thats on it) am i screwed?

---

### Post by Doorslammer on 2008-03-17
I used this page 
you don't have to compile anything 
[http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html]("http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html")

wow just noticed your doing something else completely 

sorry can't help  the directions are a bit shy on info

---

### Post by tlink on 2008-03-17
You are never screwed (well, 99% of time anyway).   Ok, so you deleted both of your panels then?  Not the end of the world.  

I'm trying to figure out where you might be in this whole process.

If you deleted your panels before you added the software sources, you can still get to them this way

type Alt-F2, it will bring up a menu.  Then put in

gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

That will get you to your sources menu.  Then add what they said to add to it.
Now that you have told it where to get awn, you can install it.

Again, type alt-F2 and type in 

gnome-terminal

that will bring up a terminal window, then put in the code they show there (the apt-get install blah blah).  That will install awn for you and you can then run it by typing 

avant-window-navigator

Saving to "/usr/share/nautilus/patterns" means to just download the bg and then copy it to that directory.

Hope it help, not really sure where you are in the whole process, but I tried to hit the places where I would think you might get stuck.  If there's something that I missed, ask away :)

---

### Post by spacebub on 2008-03-17
hmmm thats wierd, my computer doesn't respond when i type alt-F2

---

### Post by tlink on 2008-03-18
It should.  alt-F2 is holding alt down while you hit F2.  Maybe that helps?

---

