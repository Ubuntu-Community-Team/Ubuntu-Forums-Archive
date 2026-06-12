---
title: "how install vb.net 2003 on ubuntu 7.04"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by banga on 2007-10-08
hi friends

help me to install .net on ubuntu
i am new in ubuntu nd try to intall .net on it
but i don't know how to install
so plz help me to intall vb.net on ubuntu 7.04
thanks in advance

---

### Post by Beggar on 2007-10-09
.net is specific to windows.

There is a version for linux, mono, but it is a ways behind (still the equivalent to .net 2.0)

To install mono, run 

```
sudo apt-get install mono
```

---

### Post by banga on 2007-10-10
is  mono  is same as .net

is mono is user friendly?
and can mono give same funtion  like in .net
i want to install .net
i read about .net
and now how i work on mono?

---

### Post by Circus-Killer on 2007-10-10
judging by your question (installing .net on ubuntu), i assume that you are only a beginner programmer.

if i was you, and you desperately need to learn .net, then i would have to say, stick with windows for now. if you are wanting to learn any programming language that will teach you the concepts of programming, then i would suggest a language that does not tie you down to an os.

i would not recommend you look into mono if you are just beginning. and installing .net on ubuntu will never happen. as said, i would suggest a non-windows language, maybe c++ or maybe even java.

but as far as .net goes, if you really MUST learn it, then stick with windows, it will probably be your best option. 

(just my opinion, won't be suprised if others disagree)

---

### Post by banga on 2007-10-10
i am currently working  on ubuntu nd not on window

so plz sugest me what can i do  to start vb.net2003 on ubuntu
thanks in advance
plz give me solution of my major problem

---

### Post by Beggar on 2007-10-10
Unfortunately, .net is extremely windows specific, and there isn't much you can do about it. As I said earlier, the mono project provides some support, but I am still forced to use virtualbox in order to do  most of my .net programming, of course I need to use 2008 which doesnt even run in XP.

However, if you really want an alternative

```
 sudo apt-get install mono
```

Help can be found in the man pages, although I would recommend a text as well (Im partial to the Sams books)

If you want an IDE, then 

```
 sudo apt-get install monodevelop
```

Is good enough for a beginner. But as previously pointed out in this thread, VB is not a very good language to learn first, I would highly recommend java if your looking for somewhere to start.

---

