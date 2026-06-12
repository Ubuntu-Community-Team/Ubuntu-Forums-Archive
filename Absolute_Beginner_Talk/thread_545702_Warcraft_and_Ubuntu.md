---
title: "Warcraft and Ubuntu"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2007-09-07
Ok,  some simple questions here I hope!

First, I found a "how to" guide right here on the forum, which is very VERY well done, but there are a few questions I have.

Here's the link to the how to I plan to use...

[http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)

So.... my questions.

First part of the how to tells us to uninstall wine if we already have it installed.  Question 1. here: is that really necessary with Fawn?  2.  what is the command to uninstall wine... for that matter any program?

> **Install the 'build-essential' package** if you haven't already that will install the compiling utilities you will need.
You will probably want to run the command 'sudo apt-get build-dep wine' which should install anything you will need to compile wine. Otherwise you may get messages during './configure' about missing libraries.

I highlighted the build-essential package for a reason... because I am not sure if he is talking about the sudo apt-get build-dep wine.  Is this in fact the same?  If not what is the command for the build-essentials package?

> Get the two patch files needed, and place them in the top directory of the source files

Ok, so I'm a real newb here with Ubuntu.... what ummm does that mean exactly?  The above quote I am talking about.

I think that's about it for now.  I pretty much have everything I need up and running on Ubuntu... Doom 3 and Warcraft are the last two items on my list... of course I suspect they'll be the most difficult too....

Thanks in advance...

---

### Post by tyggna1 on 2007-09-08
> **ExSuSEusr said:**
> Ok,  some simple questions here I hope!

Question 1. here: is that really necessary with Fawn? 
Question 2.  what is the command to uninstall wine... for that matter any program?



1:  It actually depends on the version of WINE you're using already.  If it's the same version as in the guide--then, no, it's not nessisary.

2:  ```
sudo apt-get remove wine
```

---

### Post by tyggna1 on 2007-09-08
About the build-dep -- I'll explain

Wine needs certain packages--or bundles of code--to run properly.  The build-dep command will determine exactly what is needed to compile the source code of WINE and put it in to an executable package.

I.E.  He's teaching you how to take the source code that the programmer wrote, and turn it into a program.  This isn't always nessisary.   Warcarft 3--I know from experience, will run amazingly in the WINE provided in the Ubuntu repositories.

If you wanted to try:
```
sudo apt-get install wine
```
Then you'd get the command-line version of wine.  But if you go to Add/remove, and select the WINE in there, then warcraft 3 will run on it immediately.

The difference is that sudo apt-get install wine is *pre packaged*
This means that it was compiled on a system that was different than your own.  Sometimes, this can cause problems--and other times, compiling (or transferring programming code into something your computer can understand) on your own machine is nessisary.

---

