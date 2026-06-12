---
title: "Before I do this..."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by damooster on 2008-02-28
I have some questions.  I read the FAQ and didn't see the answers there.  I apologize if these questions have previously been answered, but I'm at work and trying to get this post in before the boss catches me goofing off!

Here are my questions:

1.  I have a 20" iMac with the 2.0 Core 2 Duo Intel.  I'm tired of OS X and Windows, so I'm wondering if I can install Ubuntu and use it as my sole OS on this machine?

2.  I'm a University of Phoenix student and just wondering if anyone here is also, and if so, do you use Ubuntu to do all of your class work.  Technically Linux is not supported by UoP.  They have a MathLab that requires Windows and IE, but I installed the Firefox plugin User Agent Switch and this seems to work.  Just wondering if it will work on Linux too.

3.  I found this book at Barnes and Noble: [http://search.barnesandnoble.com/booksearch/isbninquiry.asp?ean=9780132360395&itm=2]("http://search.barnesandnoble.com/booksearch/isbninquiry.asp?ean=9780132360395&itm=2").  Seeing as how I know next to nothing about Linux, do you think this will help or hurt?  Please keep in mind that I'm not very computer savvy.  

Thanks in advance for any help.

---

### Post by neurostu on 2008-02-28
So i have a couple pieces of advise:

First yes you can completely replace Mac OS X with linux. I recently made the switch to purely linux about a month ago and i'm loving it ( I have however been using linux for about 4 months now).

How critical is it that your machine just works?  Can you tolerate having things break or be not working for a few days/weeks?  Unless you can answer yes to this question i would advise against moving to completely to linux.  Linux is  very stable and it works great, but it generally takes a few weeks to months to really get accustomed to the linux way of doing things. It can also take a while (in special cases) to get all your hardware recognized and working, but if you head over to the MacIntel section of the ubuntu forums you should get a good idea of how hard it will be to configure your hardware.

I'm not sure if the IE plugin in firefox will work in linux. I believe it works by using the IE rendering engine within firefox. As linux doesn't have IE there won't be a rendering engine for the plug-in to use. (But i'm not 100% sure as I haven't tried it)

The fact that UoP doesn't support linux is okay. You can install Wine and run IE on it if you need to, also you can dual boot with mac os x if you can't get Wine working.

As far as the book you mentioned, I haven't read it, but I have read a lot of the O'Reilly books and they are really good, You might check out :[http://www.oreilly.com/catalog/9781593271527/?CMP=AFC-ak_book&ATT=Ubuntu+for+Non-Geeks](http://www.oreilly.com/catalog/9781593271527/?CMP=AFC-ak_book&ATT=Ubuntu+for+Non-Geeks)

But again as a word of advise I would recommend against single booting linux your first time. Keep your Mac OS X install just in case, and until you are fully confident with your linux skills.

Hope this helps!

---

### Post by TheDilettante on 2008-02-28
Just a quick addition - stu's right about a complete switch, don't do it until you can afford to not have a computer for a few days, but I thought I'd throw in some links I used to teach myself some Linux

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/) - very basic intro, with exercises at the end of each section.  very short, can be done in a week or two

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)  somewhat more advanced, useful once you've got ubuntu's gui down and some small knowledge of linux/unix, like what you got from the first link.

[http://www.ubuntu-unleashed.com/](http://www.ubuntu-unleashed.com/) for ubuntu-oriented fun.

also, [http://www.tldp.org/](http://www.tldp.org/) the linux documentation project has many _longer_ manuals you can read and download.

---

### Post by radiocognition on 2008-02-28
Im also a mac user, and though I dont run Ubuntu on my Mac Book Pro, I can say that Ubuntu almost as user friendly (if you know a *little* about computers) and has the full power of the debian repositories built right in.  Also I use MatLab 2007.a (or are you using some other software) without a problem in Ubuntu,  The only thing I would caution you is this: Mac OS X is designed to run precicely on your hardware.  Moving to linux might mean that you will lose some of the functionality of your machine.  You might have a hell of a time makeing your built in camera to work ect...

---

### Post by radiocognition on 2008-02-28
Also, I trust that you realise that Mac OS X is very closely related to Linux and Ubuntu.  OS X uses the BSD kernel instead of the Linux kernel (The BSD is another 'free' kernel) but still has much of the same tools and programs that you find on a Linux machine.  Open up your terminal Applications --> Utilities --> Terminal.app and you will be able to run most of the commands that make your system go.  I would recommend that you have a basic familiarity with how the terminal works before you go charging off into linux land.  On the Ubuntu side of things, you will be using the terminal alot more

---

### Post by neurostu on 2008-02-28
I totally agree with radiocognition, try messing around with the mac terminal and see how you like it.  You don't have to use the terminal in linux but most people do, and infact it is one of my favorite features of linux.

---

### Post by Oldsoldier2003 on 2008-02-28
> **neurostu said:**
> I totally agree with radiocognition, try messing around with the mac terminal and see how you like it.  You don't have to use the terminal in linux but most people do, and infact it is one of my favorite features of linux.

Some people look at the terminal as a Throwback to the old unix days... when in fact the terminal is really the "poweruser" tool of choice. The Gui is great for getting started, and in fact many people never get past that stage, especially those that are a bit intimidated by computers. What can I say I guess i'm with you... I love my terminal.

---

### Post by neurostu on 2008-02-28
The terminal is great.   I guess the greatness of the terminal is really a function of all the applications that are available.  I have to say that I am having a love affair with APT. It is amazing. The ability to just simply search and then install software with one or two commands is AMAZING!  In windows I used to spend 20-30 minutes searching for then installing the software I was looking for but with APT i just type apt-get search <program name> then sudo apt-get install <program name> and BAM!!! its installed. i love it!, the process is reduced to seconds!!!

---

### Post by Scut_Farkus on 2008-02-28
I have to second neurostu's recommendation for Ubuntu for Non-Geeks, Second Edition A Pain-Free, Project-Based, Get-Things-Done Guidebook by Rickford Grant.  I bought this book and I have to say that it's excellent.  

I bought mine from Amazon.com and I have to say I was a little irritated because I wasn't paying attention and I got the first edition which is geared towards the Dapper Drake version of Ubuntu.  Make sure you get the 2nd edition which has updated to Feisty Fawn.  

Book will come with a disk ready to go.  Even if you're using Gutsy, you can still probably figure out how to do the excercises, and if you can't just ask a question here and people will fill you in.

Enjoy!

---

### Post by damooster on 2008-02-28
Thanks for the info and advice everyone.  I think I'm going Boot Camp it and practice with it before I do anything drastic.  

I've heard that you can run Linux from the CD  itself without having to install it...is this true?

---

### Post by neurostu on 2008-02-28
Yes, ubuntu 7.1 is shipped on a LiveCD which means that it will boot into a working os, without an install. There is also an alternate cd which does not boot into a working machine, it only boots into the install program.

---

### Post by Scut_Farkus on 2008-02-28
Yep!

It's on what's called a "Live CD".  Just put the CD in your CD-ROM drive and make sure your system boots to the CD-ROM (instead of your hard drive).  The system will boot from the CD and you can play with Ubuntu to your heart's content without screwing around with your current OS.  

A couple caveats:
1.)  Things might be a little slower because everything is running off the CD.
2.)  If you make changes to things (install a game, change your time zone, etc.) They won't be saved because you're on the CD.

Here's something interesting I've been meaning to try myself (but I've been lazy about it).  You could try installing to a flash drive.  Go here if that interests you at all:  [www.pendrivelinux.com](www.pendrivelinux.com)

Good luck and have fun with it!

---

