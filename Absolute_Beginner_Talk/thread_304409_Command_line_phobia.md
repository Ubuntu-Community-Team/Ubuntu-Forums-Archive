---
title: "Command line phobia?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by stream303 on 2006-11-21
Just some off-the-cuff suggestions that helped me when learning the command line long ago.  I'm no master, and what follows is just some tips that might get one over the psychological barrier.

How do you remember all those commands?
You don't - just learn what you need as you go.

Where do I start?
For me, learning how to traverse the filesystem and take a look around and peek at files was most important.  The four biggies were:

**ls**  (what's in this directory?)
**pwd**  (where am I now?)
**cd**  (cd Desktop - go to the Desktop directory)
**less**  (as in: less <filename>  [use q to quit viewing])

That was good enough to let me look around and see if I would just hate it.  The biggest breakthrough was disovering that issuing **cd** without any arguments took me straight back home no matter how far I got into the system.

If that doesn't throw you off, try some other simple ones:
**cal**
**date**
**clear**

Nice.  How about tidying this up a little and string them together with semicolons?

**clear ; cal ; echo ; date**

You get the idea.  Grab some online resources (man <command> is helpful but sometimes cryptic) or books and maybe learn how to make your own directories (**mkdir**), remove them (**rmdir**).  Move on to copying files (**cp**) and renaming them (**mv**) - be careful though - you don't want to be moving or renaming critical system files.  Find an editor to make some files of your own.  **Nano** is an easy start although I don't want to turn this into an editor thread - there are plenty of those elsewhere.

For me, actually writing these commands down in a notebook really helped - Not just as notes, but as if you were writing a book to help a friend learn.  Ah, a bit harder.  Try explaining what the command you learned does in your own language to someone else.  You may not have the full grasp, but writing it down and then trying to explain, or imagining your explanation can really force it to sink in. (if your friends and family can't take it anymore) :)

Don't just rewrite the book or other text verbatim.  Put it in your own words, that's the key.

If you do this, you'll laugh at your "book" a year from now, but it might become a cherished keepsake.  For some reason, doing it on paper seemed to make my brain cells retain it, rather than typing it into a text file on the computer.

Numbers and punctuation - I like to slash my zero's, and print my ones as upside-down t's.  For capitalization, such as writing down /etc/X11 , I would just underline the _X._

Take it easy!  The sheer simplicity of the command-line is its biggest secret - and unlike gui interfaces (which I love as well), what you learn now will easily stay with you for decades.  I don't foresee **ls** changing in the near future. :)

P.S. - the filesystem really threw me for a LONG time.  That whole tree-analogy with root, branches, twigs - I couldn't get it.  It wasn't until I used a Mac way back when it dawned on me that the whole thing is a file cabinet full of folders.  The file cabinet itself represented the root directory / .   Even then it took me awhile to see that the root directory had no name, just a forward slash.  Ah!  (although there is a directory titled root on your system - a point of confusion until you verbalize it. /root means "root root") :)

Have fun!

---

### Post by bodhi.zazen on 2006-11-21
[Welcome to the machine](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by ciscosurfer on 2006-11-21
Good write up.  I like the way you went about learning commands and even the methods you used.  I think this is a great way to begin learning the command line (as well as learning new non-Linux-related material).  This method reminds me of when I was in high-school and the teachers would make me write things down, even after receiving a handout.  The material just sinks in better when you can become a part of it.

Well done, Stream303!

---

### Post by po0f on 2006-11-21
> **stream303 said:**
> ...
Nice.  How about tidying this up a little and string them together with semicolons

clear ; cal ; echo ; date
...


I would recommend using two ampersands (&&).  If one command exits with an error, the rest of the commands won't execute, which is what you will want in most cases.  :)

But I wholeheartedly agree on writing stuff down.  I started using Linux full-time ~3.5 years ago, and still flip through my notes every now and then.  Ahh, the memories...  :)

---

### Post by ciscosurfer on 2006-11-21
CommandLineBeginners is also a nice site to view and learn on.

---

### Post by ciscosurfer on 2006-11-21
> **po0f said:**
> I would recommend using two ampersands (&&).  If one command exits with an error, the rest of the commands won't execute, which is what you will want in most cases.  :)

But I wholeheartedly agree on writing stuff down.  I started using Linux full-time ~3.5 years ago, and still flip through my notes every now and then.  Ahh, the memories...  :)I use logical ANDing as well and feel safer using it when I want to combine commands.  

If you know certain commands won't fail, though, using ; to separate commands is one less character you have to enter and I guess is quicker to input.

---

### Post by kinson on 2006-11-21
I Think stream303's idea is great :) its probably just laike going back to high school/college, cept this is more fun :) writing things down by hand always helps :)

I've just started to learn ubuntu, and I also wanna learn more about the command line(I'm a keyboard guy), so I'll go dig up an old exercise book and try this method, heehhe. Its probably better then typing "linux command ls" or something into Google when I need it :p

Cheers,
Kinson

---

### Post by stream303 on 2006-11-21
> **kinson said:**
>  writing things down by hand always helps :)


It's definitely a big drag.  Your fingers get cramped and you want to throw the whole thing out. Why do it if you are just going to laugh at it anyway in a year's time? :)

The other benefit of having it on paper (i'd also write my own "book" about how to install various distributions as I went through the process) was that early on I'd totally hose my systems and those precious ascii text-file notes would be gone!  Backup? yeah, right.

Thank goodness for my silly book!  Don't laugh, it'll happen. :)

---

