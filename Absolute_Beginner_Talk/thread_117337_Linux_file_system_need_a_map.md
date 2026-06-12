---
title: "Linux file system: need a map"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by xylene2301 on 2006-01-14
I'm brand new and need a little help finding my way around through the linux file system.
Could anyone recommend a tutorial?

In the meanwhile, where would I find the firefox bookmarks?
I've been led to believe a folder named with a tilde:   ~/blah blah blah  but I don't see a ~ folder...

Thanks,
X

---

### Post by gravediggers on 2006-01-14
x

~ is the same thing as your user's home folder. Look there!

---

### Post by bscbrit on 2006-01-14
The ~ signifies your home directory.  Although there is no directory with this character in its name, using ~ on the command line is a shorthand which the computer understands.

Try this link

[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

### Post by ekarni on 2006-01-14
~ is a shortcut that stands for your home directory.  So
*~joe* is the same as
*/home/joe*.

Similarly, 
*~/mystuff*  is equivalent to
*/home/joe/mystuff*

For firefox bookmarks, you can also use Bookmarks -> Bookmarks manager -> Bookmarks manager File -> Import to get your bookmarks in.

I don't have a tutorial link handy for you but they are out there -- anyone got one?

EDIT:  man, I gotta type faster next time!

---

### Post by matthew on 2006-01-14
[quote=ekarni]I don't have a tutorial link handy for you but they are out there -- anyone got one?[/quote]There are others out there, but these will get you started.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by matthew on 2006-01-14
I thought of one more and thought I would add it as well as it's quite good.

[http://www.debian.org/doc/packaging-manuals/fhs/](http://www.debian.org/doc/packaging-manuals/fhs/)

---

### Post by xylene2301 on 2006-01-14
Thanks Everyone,

I found the Firefox bookmarks with your help.  They're in a file called
~/.mozilla/firefox/3187awlh.default/bookmarks.html

I guess I'll look for a way to import IE bookmarks (.url files) into this xml-ish looking firefox file.  Perhaps a perl script?  Any tips?
(This may no longer be a beginner problem?)

Thanks,
X

---

### Post by ekarni on 2006-01-14
IE bookmarks implies you've got windows running somewhere.  Pretty sure that  Firefox on the windows side will automagically import IE bookmarks -- you could get Firefox on windows and use that to convert your bookmarks.  I can confirm that Firefox bookmark files bounce back and forth between windows/linux just fine.

---

### Post by Greg2 on 2006-01-14
[QUOTE=xylene2301]
I guess I'll look for a way to import IE bookmarks (.url files) into this xml-ish looking firefox file.  Perhaps a perl script?  Any tips?[/QUOTE]
The easy way would be to install Firefox on the system with IE that you want to import from. Then import them to Firefox and copy to your Ubuntu install. This way you solve your problem and get a good browser on the other system at the same time.

---

### Post by Azion on 2006-01-14
Good links, cheers

---

