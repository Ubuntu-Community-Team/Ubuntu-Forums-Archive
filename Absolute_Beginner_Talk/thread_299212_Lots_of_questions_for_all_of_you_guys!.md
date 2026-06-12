---
title: "Lots of questions for all of you guys!"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Bllizzd on 2006-11-13
Ok, Well here are here some of questions for youguys.

Which one is better, Kubuntu or Ubuntu?

If you install a program for gnome, would it work on KDE?

Why does everyone make it so hard to install programs?

Why isn't there a installer like the windows one?

Wouldnt that make it more user friendly?


And my prior languages that i programmed in are Visual Basic, Visual Basic.NET, and C#.

Which languages should i try and learn in ubuntu, I don't want to learn C/C++ because they are a little to hard for a 13 year old.

Is python a decent language to learn?

Srry for all the questions, but this is the beginners section.

---

### Post by digby on 2006-11-13
The Kubuntu vs Ubuntu question is completely a matter of preference.  Both have their various merits.  Ubuntu is probably a little more supported around here simply because more people use it.

If you have both Gnome and KDE installed, you can use programs for either one in either desktop.

Hard to install programs?  Have you tried using Synaptic / apt-get / aptitude yet?

Some programs have installers like you'd find in windows, but using a package manager is generally easier, and it lets the system keep better track of what is installed.

User friendly is, again, a matter of opinion.  I find the command line to be friendly because it does exactly what I tell it - no more and no less.  But a lot of people prefer to have a more visually oriented idea w/ mouse clicking, etc.  Same with software / package management.

As for your languages, you can use C# in linux - look into the mono project.

Python is also quite excellent for a lot of tasks.  I believe that Mark Shuttleworth and some of the other higher-ups are fans of python.

---

### Post by BarfBag on 2006-11-13
Welcome to the world of free software!  Don't be afraid to ask questions.  That's what some of us are here for.  :)

1.  It depends on what you think.  Ubuntu is a little easier to use, but Kubuntu gives you more control over your system.  Personally, I prefer Ubuntu.

2.  Absolutely!  Just make sure it's in the repositories.  Makes it a lot easier as it grabs the required KDE/GNOME packages and other dependencies.

3.  Installing programs isn't hard, it's just different then Windows.  There's a quite few ways to do it.  You can compile it from the source code (not recommended for the beginner), install it with a package manager such as Synaptic (KDE has a different one, can't remember the name), or use apt-get (which is as easy as Synaptic, just command line based).

4.  That's just the Windows way of doing things.

5.  Maybe at first.  However - once you learn how to do it via the things listed above, I can almost guarantee you that you'll like them better.

6.  Can't help you there, bud.

7.  Can't help you there either.

---

### Post by CatKiller on 2006-11-13
> **Bllizzd said:**
> Wouldnt that make it more user friendly?

No. What if the software gets updated? The Windows way, you'd have to know that it had been updated, find the site you downloaded it from again and update it yourself. How do you know what's available, the Windows way? You have to trawl around the Internet looking for software that may or may not work. How do you know if it conflicts with software you've already got installed, or depends on software you don't have installed? You don't, and have to just pray to the Redmond gods that it will work.

Doesn't sound very friendly to me.

---

### Post by Bllizzd on 2006-11-13
Ok Guys,
Thanks for all the information, About the installing and the complaining about using the command line (Or Terminal in Linux), i just came from windows and visual is pretty much all i know since windows trys to hide the command lines from the user to make it easier on new computer users.

Im not saying im new at computers (Definitaly NOT), i have lots of experience. Just in a different computer environment.

---

### Post by aysiu on 2006-11-13
> **Bllizzd said:**
> Ok Guys,
Thanks for all the information, About the installing and the complaining about using the command line (Or Terminal in Linux), i just came from windows and visual is pretty much all i know since windows trys to hide the command lines from the user to make it easier on new computer users.

Im not saying im new at computers (Definitaly NOT), i have lots of experience. Just in a different computer environment.
You don't need the command-line to install programs.

Read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by digby on 2006-11-13
> **Bllizzd said:**
> Ok Guys,
Thanks for all the information, About the installing and the complaining about using the command line (Or Terminal in Linux), i just came from windows and visual is pretty much all i know since windows trys to hide the command lines from the user to make it easier on new computer users.

Im not saying im new at computers (Definitaly NOT), i have lots of experience. Just in a different computer environment.
There's nothing wrong with that - I would bet that the vast majority of us have come from windows in the not too distant past.  

Just try to keep an open mind and remember that things are done a little differently here.  And ask questions!  We like to help people.  That's why we join forums ;)

---

### Post by d3v1ant_0n3 on 2006-11-13
You may find over time that using the terminal to install programs is actually much faster than using Synaptic (or Apept in Kubuntu). PErsonally, I prefer using terminal when i know the complete name of a package. But the GUI tools are there as well, so you have the choice either way.

Everything will seem very foreign and odd at first (ESPECIALLY if you have a lot of experience in Windows) but it will feel second nature in no time at all.

Just repeat quietly to yourself 10 times a day...

"Linux is not windows. Windows is not Linux";)

---

### Post by Velotix on 2006-11-13
Fwee. To answer thy questions:

> Which one is better, Kubuntu or Ubuntu?

Translation: which is better: KDE or GNOME? The answer: depends on what you want. If you want a very, very fast system that doesn't waste huge amounts of RAM getting the desktop to look nice, the answer is neither - you'll be looking in the Xubuntu area. My system is K/Xubuntu-powered, and I prefer KDE personally as Xfce is just too light for my liking.

You're not limited to just one, as my setup demonstrates. If you want to try them all out, though, definitely start with Ubuntu - I've had trouble downloading *ubuntu-desktop* through command line and no-one seems to know what to do to solve my problem. Starting with Ubuntu eliminates this issue.

Also, bear in mind you're not limited to the official Ubuntu desktops either. Have a look around when you're ready.

> If you install a program for gnome, would it work on KDE?

If you run something outside of its native environment, it's never guaranteed to work. However, GNOME and KDE both have development teams committed to a very high interoperability between the two desktop managers, so for the most part you should encounter no problems. Unless you use Xubuntu, then KDE apps need a bit of tweaking (i.e. you need to enable KDE support manually even though it's included as standard).

> Why does everyone make it so hard to install programs?

It isn't hard. You get used to it extremely quickly. I've only been using Linux for a week, and I'm already right at home... though my sound still isn't working. Check for hardware compatibility before you install Ubuntu - that's what the LiveCD's for. :/

> Why isn't there a installer like the windows one?

Because the Windows installers are inefficient. Try running aptitude (the best download manager) from command line and you'll see what I mean: everything is auto-configured and works instantly the moment the install is complete, without rebooting. In fact, Linux is designed in such a way that it is possible to leave the PC on for weeks or even months before rebooting.

> Wouldnt that make it more user friendly?

Again, no. BTW, my preferred download method is the following:

1) Load Synaptic/Adept and search for the package I'm after in the repositories.
2) Copy the package name to a text editor (GEdit/Kate/Mousepad)
3) Open the terminal and run:

```
sudo aptitude update && sudo aptitude install [package-name]
```

And one download later, my new program Just Works.

> Which languages should i try and learn in ubuntu, I don't want to learn C/C++ because they are a little to hard for a 13 year old.

That's no excuse - if you can do programming at all, you're far superior in skill to most people your age. Because of that, I would not hesitate to recommend that you learn C/C++. Above all else, Linux was programmed in C, and C++ remains the most powerful (though certainly not the most intuitive) programming language to date. You have plenty of time, so take it slow. :)

> Is python a decent language to learn.

**Yes.** Learn C/C++ and Python simultaneously and you're set for the vast majority of programming tasks. Python is considerably easier to get to grips with and is a very powerful language, but like all languages it has its limits, so don't narrow yourself to just one language. An alternative I hear of in these parts is Ruby. Head on over to the Programming Talk section of this forum to get more info on that.

Co-incidentally, avoid OS-specific programming languages because they're inherently less useful than platform-independent languages. I have significant experience with VB6 myself, and I can honestly say you'll never look back. **Man** VB6 is awful. Except the GUI. The GUI's OK.

---

### Post by IYY on 2006-11-13
> Which one is better, Kubuntu or Ubuntu?

I prefer Ubuntu, but it doesn't really matter. Look at the screenshots on shots.osdir.com and pick the one that looks best.
> 
If you install a program for gnome, would it work on KDE?

Yes.

> Why does everyone make it so hard to install programs?

It's not harder, it's just different. For me, installing a program in Ubuntu is far easier than in any other OS: I just use aptitude, apt-get, the add/remove programs or Synaptic. I don't have to download any files, run an installer or anything else.

If the program is not in the repositories (very rare), I can often get a deb and install it with a simple double click.

Installing from source is something that's nearly impossible in Windows, so there's no reason to compare. However, it's also not that difficult: just run a few terminal commands according to the readme file.

> Why isn't there a installer like the windows one?

Wouldnt that make it more user friendly?

For what, Ubuntu or the programs? The Ubuntu installer is more graphical and simpler than the Windows one (which is actually text based and has far more technical questions). Program installation I described above, and I believe it's friendlier than a "wizard" based installer.

> 
And my prior languages that i programmed in are Visual Basic, Visual Basic.NET, and C#.


You can use your C# knowledge with Mono, but it's really better to learn something more native.

> Which languages should i try and learn in ubuntu, I don't want to learn C/C++ because they are a little to hard for a 13 year old.


Python is a very good choice.

---

### Post by harrisony on 2006-11-26
i know i am a bit late but as another 13 year old whos moved to linux and 
To answer some of your questions from a teens perspective
> Which one is better, Kubuntu or Ubuntu?
Personally GNOME (ubuntu) (who says it dosent have themes if orange aint for you) the ubuntu counter says gnome as well
> If you install a program for gnome, would it work on KDE?
sure will i installed a program and it required a few KDE Libaries (not the full kde though just required for programs) and works wonderfully
Another example is edubuntu which has the kde educational suite installed out of the box
> Why does everyone make it so hard to install programs?
i think you mean compiling from source yes that is difficult and scary but still not hard, ```
sudo apt-get install program1
``` isnt hard although terminal is scary at first you get use to it you can use synaptic (package manager) i use synaptic normally (because it shows descriptions) but if i am telling someone to install something or someone is telling me to install somethng terminal is the better way to go
> Why isn't there a installer like the windows one?
because we have repositries which track everything and makes it easier for updates, although some programs use configuration wizards which would be normally be done in a installer
> Wouldnt that make it more user friendly?
repositries cant be easier it tracks everything knows what programs are installed manages what needs to be installed and saves you from having 10 copys of java installed meaning programs are smaller and did i mension updates of programs (with reps. a dream. win nitemare)
> And my prior languages that i programmed in are Visual Basic, Visual Basic.NET, and C#.

Which languages should i try and learn in ubuntu, I don't want to learn C/C++ because they are a little to hard for a 13 year old.
mono for the .net based and try them in wine as well i had some small suscess with VB
I reccomend Python and c/c++ as someone else said i mainly program in PHP but thats scripting also check out [http://ubuntuforums.org/showthread.php?t=233405](http://ubuntuforums.org/showthread.php?t=233405) i know it says beginners but some of the posts may help you make a decision to go in
--
Overall ubuntu may be scary at first but now im loving it and have ubuntu stickers all over my locker. the forums are good for when you stuff your pc up as well. I single boot but have a copy of vmware workstation for photoshop (need for school) and wlm (as Messenger Plus Live is a tank)

If you need any help/advice from a teens perspective just give us a yell
remeber ubuntuforums.org and [http://doc.gwos.org](http://doc.gwos.org) are your friends

---

### Post by Foxen on 2006-11-26
Welcome to something much better than Windows(much better it must be since you decided to try it out:)!

I can't say anything more than the other guys haven't already told you, I emigrated from the Redmond controlled world about a month and a half ago, not so very easily tho because of my laptop and I tried almost every thinkable distro except Arch and Slack(I didn't quite like the idea of having to compile nearly everthing from scratch, but ended up there with Gentoo, duh) and found out after three weeks of struggle with my Radeon X1600 that Edgy Eft had the neccessary X.org 7.1.x ;)

Since then I've been running Kubuntu, trying all the wahooplas out and nuking it totally(user fault, not os fault) and at the moment I'm waiting for the Ubuntu installer to complete, I am switching to Gnome.

It's like they say, more support(Gnome) or more control(KDE), the choice is yours but like someone earlier said, if you wish to choose between both desktops do begin with installing Ubuntu and then just install "kubuntu-desktop" with Adept, Synaptics or aptitude, I've also found out that gdm is far superior to kdm as a Display Manager(in my case anyway) as kdm keeps hardlocking on logout with this laptop, it didn't happen in the beta but with the released version it does... *shrug*

Oh, I am not ever going to be heading back to the Redmond path, I might install Playground XP in VmWare but not as my preferred os anymore, it took me about ten years of abuse from Windows to make a decision and figure that whatever I left behind was not worth the pain that Windows tends to inflict on it's users ;)

All it takes is a bit of determination, knowing how to read and write good english(I'm swedish) and you're all set.

If you want to play games it should be pretty easy as well, either there are binaries for lots of games and if not you could always see if it will run through Cedega or Wine.

Sure, linux might seem a lot more complicated in the beginning but eventually you'll see what so many others have before you, a more efficient, powerful, flexible and reliable OS than Windows will ever become.(I've tried Windows Vista public beta, it's the biggest waste of resources I've ever seen so far and everything it can do, Beryl can do nicer;)

Sorry for ranting, just giving my view on things.

---

