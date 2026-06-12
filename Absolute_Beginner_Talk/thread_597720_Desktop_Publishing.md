---
title: "Desktop Publishing"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-10-30
I'm suppose to create a brochure in the next 3 hours for a school assignment, I found a publisher-like program called scribus, but which one should I download?

[http://www.scribus.net/index.php?name=Downloads&req=viewdownload&cid=34](http://www.scribus.net/index.php?name=Downloads&req=viewdownload&cid=34)

I don't have a lot of time to figure out everything right now, I just want it to work.

Please help

Any answer would be thanked.

---

### Post by Happy_Man on 2007-10-30
Easy... just open System --> Administration --> Synaptic Package Manage, search for Scribus, and download it from there. That way, it's kept updated by the update manager. Plus less hassle for you. :p

---

### Post by llamakc on 2007-10-30
You should install from inside of Ubuntu by using Synaptic if you're using GNOME or Adept if you're using KDE.

Search for it and mark it for installation. If you're unfamiliar with Synaptic/Adept or installing packages from the terminal, let us know.

A simple:

```

sudo apt-get install scribus

```

Would also do the trick from within the terminal.

---

### Post by nest on 2007-10-30
you should download [this]("http://downloads.sourceforge.net/scribus/scribus-1.3.3.9.tar.bz2?modtime=1178753425&big_mirror=0").

you'll have to compile the source to make it work.

or you just can download it from synaptic (much more easily)

---

### Post by InsertNameHere on 2007-10-30
THANKS VERY VERY MUCH

for a moment I thought I had to compile everything from scratch... phew....

again THANKS =D

---

### Post by InsertNameHere on 2007-10-30
FREAKING GOD IT CRASHED THE 2ND TIME NOW I LOST ALL MY WORK TWICE AND MY FREAKING TIME IS RUNNING OUT....

Is that why KDE apps don't freaking work on gnome?

---

### Post by llamakc on 2007-10-30
Depends on the error or the reason it crashed. You would have to give more info.

---

### Post by InsertNameHere on 2007-10-30
It just says it has crashed singal 11..

---

### Post by BirdZerk on 2007-10-30
I use OO presentation, I found it easier to use, just set the settings to paper rather than screen.

---

### Post by llamakc on 2007-10-30
It just crashed on me too. Happened when I went to 'save' the work. Huhm.

[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=scribus&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=scribus&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

Several bugs over at bugs.launchpad.net already.

What is it you need to design? Perhaps somebody can recommend an alternative since you are on a time-crunch?

---

### Post by InsertNameHere on 2007-10-30
OK now it wont print...

GAHHHHHHHHHHHHHH!!!!!!!!!

I tried saving it to a .ps file and printing from there but the outcome showed a horizontal page with a big chunk of text in the center (I tried landscape.......)

scribus just wont print.

---

### Post by InsertNameHere on 2007-10-30
How do I output the .ps file to like 2 .gifs?

Maybe I can do it on another computer (thats windows that runs the printers native drivers)?

---

### Post by potentia on 2007-10-30
> **nest said:**
> you should download [this]("http://downloads.sourceforge.net/scribus/scribus-1.3.3.9.tar.bz2?modtime=1178753425&big_mirror=0").
you'll have to compile the source to make it work.
or you just can download it from synaptic (much more easily)

Don't suggest users to compile a program when it is available from Synaptic. Actually don't recommend compiling at all.

I am sorry, but although I like Scribus a lot, a lot, I find it hard to recommend it for serious use, yet. I crashes at lot when you work with it a lot, or when you throw some complex files at it. It simply is unstable and not yet ready for release.

See if you can't make the brochure using OpenOffice Draw or using frames in OpenOffice Writer.

---

### Post by InsertNameHere on 2007-10-30
The brochure is "sortta" complete I can't print using scribus because the printer wont move, I saved as a PS file and it can't print landscape (altough I ticked landscape) so I need to convert it to gif or png or jpg and print it from another computer..

---

### Post by InsertNameHere on 2007-10-30
OK I used the convert command but it only gives the first page?

How do I get the 2nd page?

---

### Post by InsertNameHere on 2007-10-30
OK, wasted a lot of paper and ink and so fourth but I finally got my first broshure made in Linux (woohoo)

---

### Post by potentia on 2007-10-30
If you cannot print directly to the printer, try exporting to PDF and then print it from Adobe Reader or whatever, on any computer.

Optimally, don't use Linux for that kind of serious work again.

---

### Post by InsertNameHere on 2007-10-31
Well in my views if linux can't do this kind of work, this bug will never be fixed
[https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)

Microsoft Publisher does this fine at my school (before it broke down...BY THE ACTIVATION THINGY (they think everyones a pirate)). So if Linux wants to surpass Microsoft it must be able to do work like that.

Also I saved it as 2 postscripts 1 for page 1 and same for page 2, then converted them to gif then printed from windoze.

---

### Post by llamakc on 2007-10-31
You could learn to use LaTeX.

---

### Post by potentia on 2007-11-01
Hahahaha [-X

---

### Post by Giradman on 2007-11-04
Just new to this forum, but also searching for a DTP program that will be of use to my wife - the program **Scribus** seemed to be a good recommendation, but from the responses here,  do not suggest an optimal choice?  First, is this a 'first choice' best DTP program to try w/ Ubuntu, or are there other choices?  Just starting to explore this OS, so completely new - any comments or suggestions would be appreciated - thanks.

---

### Post by potentia on 2007-11-05
I haven't heard about any other real DTP program. I think it is a very promising program, but stick to 1.3.3.x for now, and keep in mind that even that version it really is a beta or whatever you could call it

*Save* all the time and don't expect too much.

If serious DTP is your goal, go Windows or Mac for now. But whatever you do you should give Scribus a chance first.

---

