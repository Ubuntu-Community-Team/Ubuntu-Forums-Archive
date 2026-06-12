---
title: "One Stop Shopping..."
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by rom66 on 2007-12-28
Is there are reference guide anyone would suggest. Making the leap to linux/ubuntu is bringing up 10 new questions for every problem that is tackled. Digging through the forums, while sometimes helpful, doesn't always payoff. Leaving one to wonder, am I forming my question in a common enough way that I can find the answer I am looking for or is my problem so unique that there isn't a thread out there pertaining to it. A good book sampling all that is known about the ubuntu world as it is now would be great! 

Things I have noticed so far...

The online help for making my HP Officejet Pro L7680 came up quickly on search results and made it a breeze to set up the printer to do all of it's functions.

Scanning options with the different software packages available through the normal channels of add/remove software aren't really ready for primetime. 

Changing a video driver before you're sure it's the right one, can result in a reinstallation of Ubuntu and a loss of everything on the hard drive. 

Office.org is a true alternative to Microsoft Office. Next to Ubuntu, this may be the best "free software" out there at this time. 

Imho Wine is a waste of programmers time and energy as it stands to date. This may be because the programs I need to work aren't supported but the list of the ones that do run correctly just makes you ask...why?

Good mapping software hasn't really hit the linux/ubuntu world yet. Living in a computer world without my Delome software is a scary scary thought...

There are thousand of people out there determined to make this idea take root. The number of ridiculous question fielded and answered is staggering. And the number of informative post is even more staggering. 

Thanks to all those making sure we newbs don't hurt ourselves too badly on all the new and shiney ideas out there.

---

### Post by mejy on 2007-12-28
This probably isn't going to be what you wanted to hear, but in my experience by far the best way to get to know linux is by tackling it as it comes.  When there's something you have trouble with, dig around until you find the answer and you'll learn a good deal in the process.  While at first it may seem that this just opens up more questions, you'll eventually reach a stage where you can figure most things out on your own.

When I was at a similar stage to yourself, I actually plunged right in at the deep end by installing, configuring and living with a Gentoo system - daunting at first, but a great educational experience with some first class official documentation (and a community that has been known to be elitist... but there you go).

That said, if you're hard set on a book, I've heard good things about [this]("http://www.amazon.co.uk/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942") one.  Unfortunately that may be too basic, and you have to consider that linux is such an incredibly deep, varied and customisable operating system that there's unlikely to be a book that covers all the aspects you're interested in the detail you're looking for.

In answer to some of your more specific points:

You're lucky with that printer - HP have been very helpful to the linux community with their printer support.  Actually, there's pretty good printing support and it's only improving, but a fair proportion of printers have some problems in their driver implementation.

Scanning support isn't all that great - it isn't a problem for me since I rarely need to scan anything, but it could obviously be a big problem if.  In the long run it may be worth buying a scanner with linux support in mind, and hoping that we seem improvements in the future.

Video driver settings: despite peoples hopes that Gutsy would end this, it's still necessary to drop to the command line to fix these things.  It's not particularly difficult, but not obvious either: generally, you'll have to use "sudo cp" to copy a backup file in /etc/X11 to overwrite the configuration file /etc/X11/xorg.conf.  Alternatively, "sudo dpkg-reconfigure xserver-xorg -p high" will get you back to a working GUI.

OpenOffice is definately a great piece of software.  It's GUI isn't perfect and it does lack some high end office features, but it's a fantastic drop-in replacement for most users.

I'm not sure what applications you're struggling with in wine, but it's actually a very useful and complex piece of software.  It allows web developers to see how they're pages will look in IE, gamers to play a pretty decent selection of Windows games and graphics designers to use pretty recent Photoshop versions (CS 2's working, and I believe CS 3 is too).  Sometimes it's necessary to tweak and configure things a bit to get them working, but it makes using Linux as a primary OS possible for many who otherwise couldn't.

Mapping software I've never used, so I can't really comment.

Hope that was of some use, and good luck with linux.

---

### Post by blueridgedog on 2007-12-28
> **rom66 said:**
> Thanks to all those making sure we newbs don't hurt ourselves too badly on all the new and shiney ideas out there.

I ran Linux as a desktop OS for a year in 1998.

In the ensuing period, I have ran Linux servers constantly, but generally kept a windows desktop.  I think I have a good understanding of "how Linux works", having run Linux servers since 1994, but the new gnome desktop and the advances in the gui are amazing.

Last month, I decided to try the Linux desktop again and to help out here so that I can be a part of making this great.

Wow.  Yes there are some rough edges here and there, and you sometimes hit a deadend that makes no sense, but then you do have a working, functioning system. My daughter uses it (she is 9). 

I honestly think that the transition from XP to Ubuntu will be seen as easier to many than the transition from XP to Vista. My wife has asked me if it will run on her system (a new Sony laptop) because she REALLY hates Vista.  Nothing is where she expects it to be and worse, you find the things where they make little sense.

I am going to go another year with a Linux desktop (no dual boot) and who knows, I may never look back.

Don't look at what won't run or what won't work, look at what will.  Be flexible.  I have a few "must have" applications.  Most run in wine.  Regarding the few that don't, I have contacted the vendors and advised them that I am running Linux now and that I expect them to provide a version for me or to realize that my business is moving on.

Be part of it getting better.  Don't expect it to be "the same" and judge it on it's "sameness".  It is "free as in speech" and liberating.

---

### Post by AndyCooll on 2007-12-28
The nearest one-stop shop you'll get are the general distro guides. Ubuntu's is [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy")

:cool:

---

### Post by kinkdxm on 2008-01-13
> **rom66 said:**
> Imho Wine is a waste of programmers time and energy as it stands to date. This may be because the programs I need to work aren't supported but the list of the ones that do run correctly just makes you ask...why?
I was able to purchase and install halflife and frag to my hearts content via steam under wine!

---

