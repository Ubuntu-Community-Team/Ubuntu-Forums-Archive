---
title: "Programming"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Arrhenius on 2006-06-05
I would like to start learning programming. I would do it in my ubuntu. What would you recommend me reading and downloading?

Thank you.

---

### Post by nanotube on 2006-06-05
[QUOTE=Arrhenius]I would like to start learning programming. I would do it in my ubuntu. What would you recommend me reading and downloading?

Thank you.[/QUOTE]
what languages do you want to learn? what is the goal you want to accomplish with your programming? the answers depend on what it is you want to do :)

in general though, for a beginner trying to learn to code, i'd recommend jumping into python. it is pretty easy to pick up, has easy syntax, and gives you a lot of good ideas. then, later, if you want to learn lower level stuff, you could try your hand in C.

python is installed by default on the system. and if you go over to [http://www.python.org](http://www.python.org), they have an extensive documentation section, with tutorials and everything.

---

### Post by slimb on 2006-06-05
[QUOTE=nanotube]what languages do you want to learn? what is the goal you want to accomplish with your programming? the answers depend on what it is you want to do :)

in general though, for a beginner trying to learn to code, i'd recommend jumping into python. it is pretty easy to pick up, has easy syntax, and gives you a lot of good ideas. then, later, if you want to learn lower level stuff, you could try your hand in C.

python is installed by default on the system. and if you go over to [http://www.python.org](http://www.python.org), they have an extensive documentation section, with tutorials and everything.[/QUOTE]

yep the first big thing you want to decide is what you want to accomplish.  do you want to be able to contribute to a project like ubuntu, or do you want to build your own apps, or ... etc.

once you decide what you really want to do is when you can decide which language to learn first.  python isn't a bad thought

---

### Post by tylerjames on 2006-06-05
I find that Java is always a good place to start too. You can get used to the whole Object-Oriented paradigm pretty quickly. And Eclipse is an excellent IDE to use for it. Not to mention that Java is pretty easy to read since you won't be using a lot of ambiguous special characters and things.

Might wanna check it out.

---

### Post by Arrhenius on 2006-06-05
I would like to learn programming. I want to be a physicist and I think notions of programming could be useful. For starting I would like to create like errr... a programm that gives me, for exemple, the 1000th number of the Fibonacci sequence. 
Did I help?

---

### Post by meng on 2006-06-05
It helps, but do you have any more ambitious projects in mind too? You could find the 1000th Fibonacci number with a bash shell script, and so programming in Java would be overkill (IMHO, even though it wouldn't be that difficult). But if you were interested in developing multi-platform user-friendly applications, then you'd want to look beyond shell-scripting. That said, there are some basic programming principles that you would pick up even with simple languages, and you can always migrate to something else later.

---

### Post by sherlock-holmes on 2006-06-05
[QUOTE=Arrhenius]I would like to start learning programming. I would do it in my ubuntu. What would you recommend me reading and downloading?

Thank you.[/QUOTE]


[How did you learn to program]("http://www.ubuntuforums.org/showthread.php?t=8682")

this thread has a LOT of information....

hope this helps..

---

### Post by Pavilion on 2006-06-05
[QUOTE=Arrhenius]I would like to start learning programming. I would do it in my ubuntu. What would you recommend me reading and downloading?

Thank you.[/QUOTE]

It appears your interest may lie with Mathematics, therefore, you should consider a languuage specifically designed for that purpose. FORTRAN will do mathematics.  Google:  FORTRAN LINUX.  FORTRAN does have a rather steep learning curve and you may want to consider an instructed course.   

Pavilion

---

### Post by enyaw on 2006-06-05
[QUOTE=Pavilion]It appears your interest may lie with Mathematics, therefore, you should consider a languuage specifically designed for that purpose. FORTRAN will do mathematics.  Google:  FORTRAN LINUX.  FORTRAN does have a rather steep learning curve and you may want to consider an instructed course.   

Pavilion[/QUOTE]

When I'm bored sometimes I retreat to my old Packard Bell running MS Dos.  FORTRAN 77 lives there, and I enjoy creating and running small programs that cause me to use some of the mathematics I learned of Physics.   Newer versions of FORTRAN are available for LINUX.  FORTRAN will do mathematics if that's your goal.  =D>

---

### Post by nanotube on 2006-06-05
[QUOTE=Arrhenius]I would like to learn programming. I want to be a physicist and I think notions of programming could be useful. For starting I would like to create like errr... a programm that gives me, for exemple, the 1000th number of the Fibonacci sequence. 
Did I help?[/QUOTE]
hmm, well, i'd stick with my original recommendation of python. the initial learning curve is not hard (the x'th number of fibonacci, eg, is just a few lines of code), and for more "advanced" things that you may want to do later on, there are libraries specifically for science/math usage that you could use (scipy, numpy).

---

### Post by Arrhenius on 2006-06-05
Yes, I am interested in Mathematics/Physics, because as I said I would like to be a physicist. Nevertheless, I am just an 11 grade student, who wants to learn something already. Should I follow this FORTRAN?

---

### Post by mostwanted on 2006-06-05
Fortran, FSM no!

Learn Ruby, it's the most makes-sense language and does everything these days.

[http://poignantguide.net/ruby/](http://poignantguide.net/ruby/) <- Coolest programming book ever
[http://www.rubycentral.com/book/](http://www.rubycentral.com/book/) <- Good tutorial/reference

```
sudo apt-get install ruby irb
``` will install Ruby and the Interactive Ruby Interpreter.

---

### Post by tribaal on 2006-06-05
I highly suggest Python, it has several nice advantages you might want to consider:

* It uses an easy to figure out syntax.
* Yet it's very powerful: you can code something really small, but also a multi-threaded distributed computing application. :)
* It comes with it's famous "batteries included" library: most of the functions you will need to call are already included in python, that means you'll hardly ever have to download additional modules.
* It can be used as a procedural languages (you'll start with this), but will allow you to do Object-Oriented programming too. Actually, it's even designed for that!
* It's portable: you applications will run on Linux, Windows, and Mac OS.

And I saved the best for last:

* It comes with ubuntu :) You already have it installed on your system :)

Just my 2cents, but I really think Python is a nice programming language... ;)

- trib'

**EDIT:** I didn't write fast enough, mostwanted's suggestion of ruby is a good one too. Python or Ruby, way to go :)

---

### Post by xtacocorex on 2006-06-05
Hey, what's wrong with FORTRAN?

I'm an Aerospace Engineer and have done quite a bit of numerical methods programming in FORTRAN. If you're going to do anything math related, I would learn it. It can do all that object-oriented stuff, but not easily, at least that's how I see it. It's gotten to the point that I can think in FORTRAN syntax.

There are some other people on the forums that I know personally who can attest to how cool FORTRAN is, at least I hope they would. (chickenmonger and aerowrestlerisu)

I will say, that most scientists still use FORTRAN, and this comes from working in a laboratory with physicists and chemists. 

I've taken two classes in C++ and know it decently, but not all the object-oriented stuff. I'm teaching myself Python now to get a better grasp of that. It's quite a handy little language.

I would say FORTRAN and Python.

---

### Post by zvezdogled on 2006-06-05
Hi. I am a student of physicst. I am dooing a lot of computer simulations and modeling. I was first confronted with programming in my first year of college...  
I started with java , but in second year i changed to c because in c you have a library called gsl that has many rutines (numerical integration, fft, differential equations...)  already written and that is essential  when you want to save time and focus on a "real" problemm. 
I advise you to learn c if you want to do simulations like three body problem, n-body problem and numerical orbit computations, and stuff like that.
And also i think that if you learn one of those languages any one will be fine because in my opinion it is realy easy to swich between them once you know the basics.

---

### Post by bigkahoona on 2006-06-05
You are saddling the horse from the wrong end...
The issue shouldn't be "I want to be a programmer, now, what do I want to program..."
but
"Ok, this is the problem I want to solve and how can it be solved logically."
Then start coding.
You want to have an algorithm that gives you the 1000th number of the Fibonacci sequence? Well, how would you go about getting the result on a sheet of paper? Then try translating your solution into code.
The language you use is not important at all. It's all applied logic.

---

### Post by Arrhenius on 2006-06-05
zvezdogled, are you enjoying physics? It must me beautiful. Where are you from?

I have to start with one. Maybe Python, I like the name (great reason!) and it appears to be the most recomended followed by FORTRAN. But meanwhile I will read some information about the other ones. Thank you everyone for your kindly help.

---

### Post by Bloch on 2006-06-05
Once you learn one programming language, you'll find that it's easy to learn a second and third. Basically, they are all the same, with the exception of languages like LISP.

I always wanted to learn programming without having a special reason to do so. I learned the basics of Python. I was able to help out my girlfriend do some text processing on a few hundred files. The kind of thing other people use perl for, but python is much clearer. Python is more friendly to beginners. 
Here is my favourite book for learning python - it is much better than the two books I bought for about €40 each!!

How to think like a computer scientist
[http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)

---

### Post by Arrhenius on 2006-06-05
bigkahoona,
> how would you go about getting the result on a sheet of paper?
The Fibonacci Sequence is 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ... a[SIZE="1"]n+1[/SIZE] = a[SIZE="1"]n[/SIZE] + a[SIZE="1"]n-1[/SIZE].

I would calculate until reach the 1000th term.

Bloch, thank you very much for the book and your suggestion.

---

### Post by bigkahoona on 2006-06-05
Yes, I do know the Fibonacci sequence.
My point was a different one.
No matter whether you want to calculate how many crates you are able to fit into a truck or what is the shortest way to get from A to Q, you will have to apply some logical thinking.
There is no way you can simply say "I want to be a coder and a physicist, what do I need to do?".
The answer lies within...:wink: 
Think. Find a logical solution for the problem. Put it into your preferred languages syntax.
That's it. No more and no less.
I might be wrong here, but I think you are rather young. Am I right?

---

### Post by nanotube on 2006-06-05
[QUOTE=Arrhenius]bigkahoona,

The Fibonacci Sequence is 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ... a[SIZE="1"]n+1[/SIZE] = a[SIZE="1"]n[/SIZE] + a[SIZE="1"]n-1[/SIZE].

I would calculate until reach the 1000th term.
[/QUOTE]
so, now, basically, read the python tutorial (if you do indeed choose python), to learn about the basic techniques available in the language, and think about which ones would be appropriate for your situation. (hint: a loop might be handy here)

---

### Post by Arrhenius on 2006-06-05
bigkahoona, 17 years is young?

---

### Post by highslime on 2006-06-05
A friend of mine who introduced me to the wonders of Linux suggested that I learn to program as well, because apparently it'd help me understand wtf I was doing a little better.  My problem lies with the fact that the only programming language I know(or vaguely remember, haha) is Pascal, which I took in high school(10 years ago :-k ).  I've yet to check out Python, but I've heard of it before, so I might look into that tonight.

---

### Post by Pavilion on 2006-06-08
[QUOTE=Arrhenius]I would like to start learning programming. I would do it in my ubuntu. What would you recommend me reading and downloading?

Thank you.[/QUOTE]

My major is chemical engineering.  Fortran is the language needed and taught for this major at the university.  Your present grade level should give you great access to high school as well as college level instructors.  If your goal is physics at the university level you should invistigate what langusge your major expects of you.  Learn and completly understand that language first this will put you in  good position with your peers when you move onto university.  University physics professors or the many  TA working for the professors are a resource to help you decide on what lanuguage works best in Physics.

---

