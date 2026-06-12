---
title: "Anyone tried Gambas, Anjuta, Eclipse ?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-03-16
[COLOR="Purple"]I have used Visual basic, not alien to programming in other languages including Fortran. Can anyone give me some information on the various tools like Gambas, Anjuta or Eclipse. Any info
on software development for cross platform operation (maybe using Java) ?
Any other programming tools ?[/COLOR]
:guitar:

---

### Post by Ryba on 2007-03-16
> **dptxp said:**
> [COLOR=Purple]I have used Visual basic, not alien to programming in other languages including Fortran. Can anyone give me some information on the various tools like Gambas, Anjuta or Eclipse. Any info
on software development for cross platform operation (maybe using Java) ?
Any other programming tools ?[/COLOR]

Not sure what you are wanting to know actually. Eclipse is fantastic for java development. Anjuta is pretty decent for a c/c++ development. I've never used gambas so I can't say anything about it.

As for cross platform development, I'd suggest java as it is definately a heck of a lot easier, faster, and more portable then trying to write crossplatform c/c++ and making sure you have all the special crossplatform api libraries included and setting up the automake to do the crossplatform checks for all the strange apis you might work with and trying to compile it for various different platforms so that it is easier for people to use your work without having to compile it themselves and such.

But if you need native look/feel/speed/efficiency, I'd suggest c++ (or c) though with Java 6 out now I might have to question just how much better c/c++ is for complex applications. Most of the newer complex applications I've seen done in both actually suggest that Java 6 is better for even desktop applications. Aside from the initial startup time (and only the 1st time not subsequent times at that) it has run smoother and faster then the c++ equivalent.

C#/.net/mono is not bad either. Well mono sucks but I'm sure it'll quickly get better. c#/.net are almost as good as java in performance (and .net 3.0 claims to be better) but the api are much cleaner so working with it might be easier. Mono is well .... not quite even close to being on par with java or .net but as with all things open source, they'll get better whenever they get around to caring about performance. Right now just getting api compatibility seems to be their highest priority.

My recommended choice if you are looking to learn something new though, stick with Java, there is a lot more useful references and external libraries and well developed tools and toolkits out there for it.

---

### Post by dptxp on 2007-03-16
Thanks Ryba.

Ubuntu 6.10 is my first Linux OS, and one reason for going for Linux is programming. I am currently trying to understand  Linux. Netbeans is one I have checked, I want the 64-bit. Gambas is similar to Visual Basic, uses Basic, and I want to use it for small test programs for Rapid Development.
Do you like Elipse ?

---

