---
title: "how to program"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by cpeckert on 2007-07-30
I have absolutly no programing knowledge but am interested in learing to program in Ubuntu. Does anyone know of a site ( free preferably ) where a total novice can start learning?

Thanks

---

### Post by jfinkels on 2007-07-31
> **cpeckert said:**
> I have absolutly no programing knowledge but am interested in learing to program in Ubuntu. Does anyone know of a site ( free preferably ) where a total novice can start learning?

Thanks
Install python:```
sudo aptitude install python
```
Then follow the instructions here: [http://docs.python.org/tut/](http://docs.python.org/tut/)

Type the following to start the interactive python interpreter:```
python
```

---

### Post by cpeckert on 2007-07-31
Thanks

Can I do this in Windows? I haven't  done much but install Ubuntu so far.  I am hoping that by learning some programing I can also learn how to use Ubuntu. I installed Ubuntu on a new desktop machine but haven;t had much time so I haven't even got the modem up & running. I do however have a little time at work I can use for learning via a Windows machine.

I really appreceate any helpful info.

---

### Post by MicronXD on 2007-07-31
java r ghey.... but it'll work on nearly every platform!

---

### Post by univremonster on 2007-07-31
This post made me curious because I am also looking to contribute to the Ubuntu project.  I have created a Launchpad account and tried with little success to find a mentor willing to take on somebody with no experience in Python or Perl.  This website looks like it will do a great job helping me to catch up.  I do have a question though.

In chapter 2 ([http://www.python.org/doc/tut/node4.html](http://www.python.org/doc/tut/node4.html)) the author says Python is typically in /usr/local/bin or /usr/local/python.  I don't have either of these, despite the fact that I do have Python installed (and running right now) and I haven't moved it or anything. How do I search for a file or folder?  I have the feeling there is a wonderfully simple command-line answer to this question that does not involve some dumb dog animation pretending to dig while using 98% of my CPU during the search and still not finding the file... not that any OS would do that...

---

### Post by jfinkels on 2007-07-31
> **univremonster said:**
> This post made me curious because I am also looking to contribute to the Ubuntu project.  I have created a Launchpad account and tried with little success to find a mentor willing to take on somebody with no experience in Python or Perl.  This website looks like it will do a great job helping me to catch up.  I do have a question though.

Try making a program for your own benefit; it is the best way for you to learn a new language. After you gain some understanding of the language, then spend some time in the IRC channel for the project you wish to work on, or hang out around the forums or bug tracker. Fixing bugs will be the greatest help/best tool to understand a program.
> 
In chapter 2 ([http://www.python.org/doc/tut/node4.html](http://www.python.org/doc/tut/node4.html)) the author says Python is typically in /usr/local/bin or /usr/local/python.  I don't have either of these, despite the fact that I do have Python installed (and running right now) and I haven't moved it or anything. How do I search for a file or folder?  I have the feeling there is a wonderfully simple command-line answer to this question that does not involve some dumb dog animation pretending to dig while using 98% of my CPU during the search and still not finding the file... not that any OS would do that...

Programs are mostly kept in the **/usr/bin/** directory. There are many ways to find a program. One is to type in the terminal ("Applications > Accessories > Terminal"): ```
which python
``` You can replace 'python' with the name of any program. You can also use the program 'locate':```
locate python
``` This will do a more traditional "search" for the term "python". As with any program, read more about it using the man pages:```
man locate
```

As for installing in Windows, follow the directions on Python's website for installing with Windows. As long as you install the python runtime environment/interpreter, you should have no problems with the tutorial to which I directed you. However, I highly recommend using a *nix computer for your programming needs: it has all the tools you need at your disposal, and it is simpler to use and install programs and languages.

---

### Post by Hopeless on 2007-08-01
Most programming in Linux is the C Language, it's a good language..
a beginner language for you would be Basic, in Microsoft you have Visual Basic, and the Linux version is called RealBasic, you can download through any p2p also look for c programming & Basic  languages in p2p apps... + tons of free tutorials online

Once you learn Basic its easy to go to C

BTW RealBasic makes apps in Windows and Linux...

HTH

---

### Post by aquavitae on 2007-08-01
> **cpeckert said:**
> Thanks

Can I do this in Windows? I haven't  done much but install Ubuntu so far.  I am hoping that by learning some programing I can also learn how to use Ubuntu. I installed Ubuntu on a new desktop machine but haven;t had much time so I haven't even got the modem up & running. I do however have a little time at work I can use for learning via a Windows machine.

I really appreceate any helpful info.

There is a common misconception that you have to know programming to use linux.  This is not true.  It sometimes helps when things go wrong to understand the mechanics behind it, but its certainly not necessary.  However, there's nothing wrong with learning programming just for the sake of learning progamming, and I'd agree that python would be a good place to start.  

Python will work in windows - you just have to download it for win.  I think large portions of the ubuntu-specific stuff are written in it.

Java is also an easy one to start on, and is used extensively in web-based apps.

C is an extremely powerful language and the linux kernel is build in it, but I wouldn't recommend it for a newbie as its quite complicated and a little too low-level to make it useful for desktop apps.

C++ is similar to C, but does a lot more.  Most of linux is written in C++.  As far as I know its about the most powerful language out there, but because it can do so much it is also a lot to learn.  It took me a year to teach myself C++ properly, compared with python which took me about 2 weeks.

Basic languages are not very commonly used, except for VBA in windows.  VBA is to my mind the most cumbercome and unfriendly languages there is.  I don't know a lot about the other basics, but I don't think they are object orientated - the most feature of most other programming languages.

To summarise - I'd suggest starting on either python or java, but of course it depends on what you plan to program.  Python is not great for web-based apps, java is.  Java is not the best for small and quick desktop apps - python is much better.  But remember - its not necessary to learn programming in order to use linux.

Hope this helps

---

### Post by jfinkels on 2007-08-02
> **Hopeless said:**
> Most programming in Linux is the C Language, it's a good language..
a beginner language for you would be Basic, in Microsoft you have Visual Basic, and the Linux version is called RealBasic, you can download through any p2p also look for c programming & Basic  languages in p2p apps... + tons of free tutorials online

Once you learn Basic its easy to go to C

BTW RealBasic makes apps in Windows and Linux...

HTH

I disagree: BASIC is an ancient language with irritating syntax rules and lack of functionality, and you will only find BASIC today in Microsoft's VIsual Basic for Applications, because Microsoft is way behind the times and makes terrible software.

I highly recommend Python as a beginner language because it is a "very high level" language (i.e. it resembles our natural language [English] more closely than C, Java, etc., which we might call "high level" languages).

---

### Post by lisati on 2007-08-02
> **cpeckert said:**
> Thanks

Can I do this in Windows? I haven't  done much but install Ubuntu so far.  I am hoping that by learning some programing I can also learn how to use Ubuntu. I installed Ubuntu on a new desktop machine but haven;t had much time so I haven't even got the modem up & running. I do however have a little time at work I can use for learning via a Windows machine.

I really appreceate any helpful info.

My desktop (XP Home preinstalled) came with a version of Python, also available for Ubuntu but I haven't tried programming in it yet.

There's a number of programming environments that come in cross-platform versions that work with Linux (incl. Ubuntu) and other OSes..... Python is one, C & C++ are another example, as is "Freebasic". There are probably more - which one you choose is up to you.

---

