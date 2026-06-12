---
title: "[SOLVED] Simplish questions from seminoob"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by WFGeppetto on 2008-03-16
Alright, this is now my forth install of Ubuntu.  I used a wubi installer with Fiesty, first, then did a proper install of Gutsy from a live CD, and set up dual boot properly.  Then, after installing lots of junk, and finally figuring out what apps I wanted, I reinstalled Gutsy, to have a fresh start.  

I was using the 64 bit version, and I had gotten advice enough times telling me that the 32 bit is just much easier to get going, and running properly (especially with codecs, and internet plugins), that I did a fresh 32 bit install.

So, here I am, in 32 bit Gutsy, on an AMD 64 laptop.  It was much easier to get everything working, and I have yet to run into a problem on the internet, so I am happy I went with the 32 bit.  AWN works, and the applets work properly, my compiz is great, plugins and all, and the internet rocks again.

Here is my question.  I tried to install AWN curves, and [winff](http://www.winff.org/).  I just really want AWN curves, and I wanted winff to have a GUI for ffmpeg, and convert .oggs.  I had the exact same problem with installation with them both.  Here is the code from the AWN curves installation, starting with the erroneous command.

> wfgeppetto@GPTO:~/awn-curves$ sudo gdebi *.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Wrong architecture 'i386'wfgeppetto@GPTO:~/awn-curves$ 


The exact same error ("Wrong architecture 'i386') was shown during the latter portion of the winff install.

Is this something to do with 32bit vs 64bit?  I would assume that's what is meant by architecture, but I know better than to assume.  Also, neither set of instructions seemed to favor one over the other.  In fact, the AWN curves instructions list debs for both 64bit, and 32bit.  

What am I missing, what is wrong, and what exactly does it mean by "Wrong architecture"?  Does it have something to do with trying to install 32 bit apps on a 64 bit machine?  Is there a workaround?  I do not want to go back to 64 bit, at least until there is more support (namely with java, flash, and vids), but I'd really like to know if that's the problem.

---

### Post by bsharp on 2008-03-16
you might be trying to install a x_64 .deb on an i386 install of ubuntu, if so, go download the 32-bit version and try again.

Installing 32-bit apps on a 64-bit machine doesnt matter if the OS is 32-bit.

---

### Post by WFGeppetto on 2008-03-16
Thank you very much.  That clarifies quite a bit, and is pretty much what I suspected.  It doesn't really solve my problem, as the AWN instructions have a deb specific to 32 bit, and that was the set of commands that I was using, and apparently, there is only one version of winff available currently (aside from the development build) from the download site.

I would like to think that there is more to the problem I am having than simply using the wrong deb, but I will double check to make sure, and I appreciate your answer, as it does help me feel a little bit more confident of my assumptions.

Btw, great quote.

---

### Post by bsharp on 2008-03-16
lol thx, i just got the quote tonight helping someone in another thread :P

---

### Post by WFGeppetto on 2008-03-17
I figured it out.  

Please take the following statements with a grain of salt, as I am stating what I believe is the case (not what I **know**), and what I did that worked for me.  I have little understanding of these commands, and barely understand why they work.

Ubuntu knows this is an AMD64 machine, and even though I'm running the 32 bit Gutsy, it doesn't always want to install i386 .debs.

I used this code:

```
sudo dpkg -i --force-architecture <mydebfile>.deb
```

Where mydebfile is the name of the .deb package to be installed.

That worked perfectly for winff, and for AWN curves, I had to use the following:

Instead of ```
sudo gdebi *.deb
```

I used ```
sudo dpkg -i --force-architecture *.deb
```

Thanks for trying to help.  I am marking this thread "solved".

---

