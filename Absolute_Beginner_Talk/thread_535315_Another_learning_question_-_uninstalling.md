---
title: "Another learning question - uninstalling"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-26
Using Synaptics I see, and have performed, installing and removing apps.

I managed to install Adobe reader this morning from Adobe's website, and got it running with a hint from this site, and it works fine now. What I don't get yet is how to remove these kinds of apps under linux. I don't see an "uninstall" script or program and it didn't come with the instructions for removing it (why?). So, how does one remove these types of apps? I guess there is no common analogy for us moving from windoze, where there is an Add/Remove section in control panel. Where are all the files at? Do you simply delete the directories or files? I see no instructions on Adobe's web site. It was a tar.gz file to begin with. I feel like I have come a long way, but this is still one hurdle I am not getting over yet.

:icon_frown:

---

### Post by adityakavoor on 2007-08-26
I have the same doubt too :(

---

### Post by jfinkels on 2007-08-26
> **mikex said:**
> Using Synaptics I see, and have performed, installing and removing apps.

I managed to install Adobe reader this morning from Adobe's website, and got it running with a hint from this site, and it works fine now. What I don't get yet is how to remove these kinds of apps under linux. I don't see an "uninstall" script or program and it didn't come with the instructions for removing it (why?). So, how does one remove these types of apps? I guess there is no common analogy for us moving from windoze, where there is an Add/Remove section in control panel. Where are all the files at? Do you simply delete the directories or files? I see no instructions on Adobe's web site. It was a tar.gz file to begin with. I feel like I have come a long way, but this is still one hurdle I am not getting over yet.

:icon_frown:

First things first: read the first link in my signature about installing software.

Second: we have a free and open source application for reading PDFs (and more!). It comes with Ubuntu, and it's called 'evince'. Press Alt+F2 to open the "Run Application..." dialog, then type "evince".

As for uninstalling, if you compiled from source (i.e. you used './configure && make && make install') there may be a 'make rule' to uninstall the files that have been installed. You can try:```
make uninstall
``` after changing to the directory containing the source files from which you compiled the application.

For the most part, you will never have to compile from source! There will (almost) always be an open source equivalent to the program you are accustomed to using on Windows! Check Synaptic, ask the forums, or search using Google or [www.getdeb.net](www.getdeb.net) !

---

### Post by mgmiller on 2007-08-26
I prefer to stay within the apt/synaptic/.deb system for exactly this reason.  Uninstall becomes a very simple matter of unchecking a box.  You would have to look at the install script to see where it put every thing and then erase all of them.  

I am curious.  Why did you install adobe reader from their web site when there is native pdf support already in Ubuntu along with evince, xpdf and probably others?

---

### Post by david_e on 2007-08-26
If something is installed via-synaptic or apt-get you should not remove it "by hand" as apt-get keeps trace of installed files and removing them will confuse it, but you should use synaptic or apt-get.

But if you installed software without the use of synaptic (apt-get) or [checkinstall]("https://help.ubuntu.com/community/CheckInstall?highlight=%28checkinstall%29") your system is not "aware" of it so you can uninstall these things by deleting files: *nixes don't have any "system register" so installing and uninstalling of 3rd part software as it  is just a metter copy/remove of files.  

In this case you can remove acroread by removing all the files it installed. It will be a long work as files are scattered among the system directories...

---

### Post by mikex on 2007-08-26
> **mgmiller said:**
> 

I am curious.  Why did you install adobe reader from their web site when there is native pdf support already in Ubuntu along with evince, xpdf and probably others?

Simple - because I wanted to try it.

 I don't understand some of you people, you want us new users to learn Linux, dive in, and ask questions on the one hand, yet when I try to learn and try something on my own, I get chastised.

:confused:

---

### Post by HappyGuy938 on 2007-08-26
I think, perhaps, it was just an honest question, and not meant in any way as a reprimand.  One of the key things about open source software is freedom of choice, so you certaintly can do as you like.

---

### Post by jfinkels on 2007-08-26
> **mikex said:**
> Simple - because I wanted to try it.

 I don't understand some of you people, you want us new users to learn Linux, dive in, and ask questions on the one hand, yet when I try to learn and try something on my own, I get chastised.

:confused:

No offense was intended, friend.

---

### Post by r4ik on 2007-08-26
Maybe this,

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Helps.

Good luck !

---

### Post by mysticmatrix on 2007-08-26
Ok you can always learn from your own side and then come asking. We accept that :)

Now as for uninstalling program, there are several ways(corresponding to several ways of installing)

1) If you used Add/Remove, uncheck the box to related application.
2) If you used Synaptic, uncheck the box related to related package.
3) If you compiled from source, i.e. did something like 'sudo make install'; go to source code folder and type

```
sudo make uninstall
```

By the way, you can see that 1 and 2 provide ease and hence are called preferred methods.

Also, you can always(99.9% of times) find a binary package that would help you save headaches. For example, Acrobat Reader can be found at the [Medibuntu's repositories.]("http://www.medibuntu.org/index.php")

---

### Post by dgaf on 2007-08-26
easy there im more a noob then you ..he was asking thats all.i know  its hard  to learn a new os system.
i only started using a pc 4yrs ago and now  i have taken a dell cpx p3 600mhz 512ram 6gig hard drive
8mb video card and brought to life when it had a blue  screen of death ..it on wireless and i can down at 
8600kbs upload is 1200kbs all buy reading and asking for help ...sometime some simple question to someone else is a big problem to you . so if the people on here seem up tite  to you there not ..AND IM NOT JUMPING ON YOU AT ALL ..so just chill and if someone get out of line theres alot of peole in here
to set them right \\:D/\\:D/\\:D/

---

