---
title: "Need help coding"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by IISpII on 2007-10-25
Hello, i have been using ubuntu 7.04 for a wile and have found it to be far superior to windows or mac.  But for a long time i have been wanting to start writeing programs and learning a coding language, but have found myself at a standstill.  I realy have no clue were to begin.  Back when i was using windows i used to write html, so i have a basic understanding, but would like advice on where to go from here.

IISPII


I am like realy new to this, just say for instance i wrote a simple code. i would have no clue how to even exicute it

---

### Post by PointyWombat on 2007-10-25
Coding with linux/unix should begin with shell scripting. Bash shell scripting or just plain Bourne shell. Start with the basics. Tons of resouces on the net.

---

### Post by macogw on 2007-10-25
Python.  It's executable pseudocode.  You know all that td (table data), tr (table row), a (anchor) stuff in html that doesn't really always look like what it means?  Python lacks that.  It's practically English.

And no, HTML does *not* mean you "know the basics."  It means you're used to semi-English terms and maybe proper indentation.  Programming is entirely different.  HTML is static.  Programs move from state to state and manipulate data.  If you've done Javascript, you might know the basics, but pure HTML won't teach you them.  HTML does not involve training your mind to think about a problem and dig through abstractions until you reach a very detailed algorithm.  I recommend [How To Think Like a Computer Scientist:  Learning With Python](http://www.ibiblio.org/obp/thinkCS/python/english/) by Jeff Elkner, an Ubuntu member who uses Ubuntu and Python to teach high school computer programming classes.

---

### Post by jon zendatta on 2007-10-25
jolly good macogw, but you sound Python biassed! surely the beginngs are 'C' language. i am attempting to learn that first, surely a good foundation.:KS

---

### Post by hyper_ch on 2007-10-25
if you want to give yourself a go in bash, the [http://www.linuxcommand.org](http://www.linuxcommand.org) has some nice tutorials to start with.

---

### Post by jon zendatta on 2007-10-25
yes or go to your local library & look for any books by John Muster! excellent work through's etc.i think there maybe a [www.muster.com](www.muster.com)

---

### Post by macogw on 2007-10-25
> **jon zendatta said:**
> jolly good macogw, but you sound Python biassed! surely the beginngs are 'C' language. i am attempting to learn that first, surely a good foundation.:KS

C's not good for beginners.  I started on Visual Basic (really, no more advanced than WYSIWYG HTML + Javascript) then learned Java.  Java's good for beginners, but it's slow and is heavily biased toward object orientation (though that didn't stop my school from teaching it procedural).  Python's nice because you can learn object oriented, procedural, functional, and scripting without learning a new language.  Anyway, I learned a bit of C at the beginning of this school year, and it is a pain.  I can do it, but I don't like it.  I'm learning C after having 3 years of programming experience, and I think it's rather hard.  There are way easier ways to do things if you use a language with more tools (and with proper strings and garbage collecting!  note: if you ever wondered why Firefox leaks like no other, it's C++ and NSCOM working together...sometimes people forget to free their memory or put multiple pointers to the same thing and only free one of them).  The thing about being a beginner, is that it's best if the language stays out of the way.  Getting so caught up with trying to figure out what the proper syntax is and whatnot can really get in the way of grasping basic concepts.  

The thing I dislike about high level languages for teaching is that you then have a learning curve for future lower-level languages.  I do feel like if I had learned C first everything else would feel incredibly easy.  However, I would probably have gone nuts and dropped out of CS after 1 semester.  If I had to learn pointers before I learned what variables really do or what types are or anything like that, I wouldn't have gotten it.  It's a trade-off.  At some point, you have to hit the learning curve for C.  You can either do it at the start and have smooth sailing after (but it'll take a lot of endurance), or you can work your way up to it by going from a high level language where you can learn concepts and how to form algorithms to a lower one with more gradual curves in between.

---

