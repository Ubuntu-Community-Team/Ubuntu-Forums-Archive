---
title: "[SOLVED] Inkscape development versions"
date: 2007-10-22
forum: Art &amp; Design
---

### Post by potentia on 2007-10-22
Hi

From [http://www.inkscape.org/download/](http://www.inkscape.org/download/)

you can download Inkscape development versions. I can still get development versions for Windows that are only a few days old, but the latest autopackages for Linux is from 06-Sep-2007 12:02.

Why? I'd like to test it on Linux. Can I get it easily from somewhere else without compiling and all that sh*t?

---

### Post by YetAnotherNoob on 2007-10-22
You're right that seems to be the latest package...maybe autopackages are broken?

I noticed the 0.46 version has "path along path", a feature I wanted last night.  (they have it in illustrator, etc)

This site has the feature available as an py extension:
[http://math.univ-lille1.fr/~barraud/Inkscape/pathdeform/](http://math.univ-lille1.fr/~barraud/Inkscape/pathdeform/)

Maybe contact inkscape for info on the packages.
:confused:

---

### Post by potentia on 2007-10-23
0.46 looks very interesting. I have the latest developer version on my Windows partition. It includes several nice new features!

I don't have time to contact them, however, right now. There is no central e-mailaddress, only subscribing to developer mailinglists and what not. Too much trouble. Perhaps I will find the time later, but for now I will play around with it in Windows.

---

### Post by Paul820 on 2007-10-23
Why don't you build it? I have just done it and it works great in Gutsy Amd64bit. All the dependencies are in the repos and it's just a case ./configure make and make install. Took about half-an-hour to build.

---

### Post by YetAnotherNoob on 2007-10-23
I am not really sure how to go about build the packages.  I am relatively new to linux and do not know what is required.  I think I will wait.  tanks.

---

### Post by potentia on 2007-10-24
> **Paul820 said:**
> Why don't you build it?

** I am an end user.** All I want to do is to install using the autopackages and start testing the features. That I could do on a daily basis when testing the stuff they are currently working on.

But, it runs in Windows, where I am most of the time anyway. Just annoying to have two different versions.

---

### Post by sloggerkhan on 2007-10-24
I tried to compile it from svn, but couldn't seem to get all the dependancies satisfied. I think some of them are probably included in available packages, I just haven't been able to figure out which ones.

---

### Post by potentia on 2007-10-24
From inkscape-devel lists

"New packages are not available because I need to resolve a problem with
packaging Inkscape which makes use of the stack protection features in
modern gcc. I have been rather short on time to research and work
through this. I would welcome help from anyone who wants to learn how to
build autopackages.

Aaron Spike"

So the ubergeeks have to build it :)

---

### Post by Paul820 on 2007-10-24
>  I am an end user.And?
> I'd like to test it on Linux. Can I get it easily from somewhere else without compiling and all that sh*t?
If you would like to test it then build it. No-one is going to sit back and do everything for you. The source-code is there, **use it**. Or quit your complaining and just use the windows version.

---

### Post by potentia on 2007-10-24
I repeat, I am an end user, the type of user some of you guys knows zero, absolutely zero about. 

Don't tell me to USE IT!!! YOU are the kind of user, and a male, probably, that compile programs. Try to understand how many that don't and never will

* I will decide myself when I will complain and when I won't, and I will absolutely never, ever compile anything!!!*

Anyway, for the normal audience out there, the autopackages will return some day, according the the developers I was in contact with. It is actually in their interest that as many as possible can easily install and test the software. They wouldn't like to scare normal users away by demanding that they compiled the software they should test.

And you should probably get out of the closed Linux circles some more. The biggest marketing disaster in human history is the Linux ubergeeks trying to attract a broader audience to Linux with more demands than offers.

Compile it...  [-X   #-o [-( :roll:

---

### Post by UI-Freak on 2007-10-24
> **Paul820 said:**
> And?

If you would like to test it then build it. No-one is going to sit back and do everything for you. The source-code is there, **use it**. Or quit your complaining and just use the windows version.

These autopackages are probably built by an automated process and as he/she points out, he/she IS actually also helping the DEVELOPERS with their software. It is in THEIR interest that as many as possible help them with testing Inkscape. Thats why the autopackages were MADE!

Compiling, you HAVE to be kidding us. Compiling is for developers and developers only. If you ask end users to compile anything, you effectively scare them away. I can see that you assume that everybody is like yourself, Paul, and that is indeed the cardinal mistake made by so many Linux followers. I honestly think that this assumption is the biggest threat to Linux. 

And where did you learn to talk and behave like that, Paul?

---

### Post by potentia on 2007-10-27
**New autopackage available here:**

[http://inkscape.modevia.com/ap/?M=D](http://inkscape.modevia.com/ap/?M=D)

To play with the new 3D toolbox feature, press** Shift-F4**

Happy testing :)

---

### Post by gruvsyco on 2007-10-28
> **potentia said:**
> To play with the new 3D toolbox feature, press** Shift-F4**
woah... thanks for that!  I built it the other day and while I like all the improvements so far, couldn't find any signs of the 3D on the interface... I just assumed I needed a GSoC patch or something but it's there!

---

### Post by sloggerkhan on 2007-10-28
```
Failed to import the numpy or numpy.linalg modules. These modules are required by this extension. Please install them and try again.
```

I get this whenever I try to use the perspective effects plugin. What the heck is numpy and where do you get it?

---

### Post by CAD-MAN on 2007-10-28
> **potentia said:**
> **New autopackage available here:**

[http://inkscape.modevia.com/ap/?M=D](http://inkscape.modevia.com/ap/?M=D)

To play with the new 3D toolbox feature, press** Shift-F4**

Happy testing :)

Fantastic - Thanks for the heads up :D

---

### Post by CAD-MAN on 2007-10-28
Downloaded *inkscape200710270316.package*, and double clicked iot to start the installer. I click install, enter the root password, and then it starts installing, but the progress bar just goes on and on - I left it for 10 minutes before getting annoyed and quitting.

Inkscape usually only takes about 30 seconds to install, so I don't know why Im having this problem. Maybe its a bad package? Has anyone else had similar trouble?

---

### Post by sloggerkhan on 2007-10-28
whichever one I used installed fine.
No idea if it's the same number as yours, but it was posted oct 27th, I think.

---

### Post by CAD-MAN on 2007-10-28
Hmm, I'll download it again tomorrow and give it another go - maybe its just a broken package.

---

### Post by potentia on 2007-10-28
If the package from the 27th is not updated, try this from the terminal:

package install inkscape200710270316.package

(CD to where ever you saved it)

It will install it using the GUI, but will provide you with some output in the terminal. Perhaps it will give you a clue, perhaps not.

---

### Post by potentia on 2007-10-28
> **sloggerkhan said:**
> ```
Failed to import the numpy or numpy.linalg modules. These modules are required by this extension. Please install them and try again.
```I get this whenever I try to use the perspective effects plugin. What the heck is numpy and where do you get it?

Is this relevant? 
[http://screencasters.wordpress.com/2007/08/31/inkscape-perspective-hell/](http://screencasters.wordpress.com/2007/08/31/inkscape-perspective-hell/)

It mentions the **python-numpy** and **python-numeric** packages. Perhaps installing them from Synaptic helps? I wouldn't know. Just an idea.

---

### Post by sloggerkhan on 2007-10-29
[http://inkscapetips.wordpress.com/2007/09/19/get-the-perspective-effect-work-under-ubuntu-linux/](http://inkscapetips.wordpress.com/2007/09/19/get-the-perspective-effect-work-under-ubuntu-linux/)

But thanks for the direction. Thanks! The more I use Ubuntu, the more I feel stupid when I discover simple solutions.

---

### Post by potentia on 2007-10-29
This is what I get when I try to use the perspective plugin/script:

> The fantabulous lxml wrapper for libxml2 is required by inkex_lxml.py and therefore this extension. Please download the latest version from <http://cheeseshop.python.org/pypi/lxml/>I get this error with or without the **python-numpy** installed.

Can I install this wrapper from Synaptic?

:confused:

---

### Post by m_gasior on 2007-10-29
sudo apt-get install python-lxml

---

### Post by wirah on 2007-10-29
> **potentia said:**
> I repeat, I am an end user, the type of user some of you guys knows zero, absolutely zero about. 

Don't tell me to USE IT!!! YOU are the kind of user, and a male, probably, that compile programs. Try to understand how many that don't and never will

* I will decide myself when I will complain and when I won't, and I will absolutely never, ever compile anything!!!*



I agree with everything you say. End users don't need smarmy comments from Linux geeks (of which I probably class as one :> ). However if you want to be the sort of user who tests development snapshots, you have to be the sort of user who 'tar xzvf package.tar.gz && ./configure && make && make install'

It's the way of the world :( I'd skip the 'make install' bit and just run it from the compile directory - for testing.

> 

And you should probably get out of the closed Linux circles some more. The biggest marketing disaster in human history is the Linux ubergeeks trying to attract a broader audience to Linux with more demands than offers.

Compile it...  [-X   #-o [-( :roll:



closed linux circle! don't tell the FSS about that. It's all open here ;)

Loving the excessive use of smilies by the way.

---

### Post by potentia on 2007-10-29
> **wirah said:**
> I agree with everything you say. End users don't need smarmy comments from Linux geeks (of which I probably class as one :> ). However if you want to be the sort of user who tests development snapshots, you have to be the sort of user who 'tar xzvf package.tar.gz && ./configure && make && make install'


Thanks! :)

Hehe, I actually am the sort of user who tests developer snapshots. Did that with several Windows programs, but they were provided with an installer. Inkscape was too for a long time. It is just a great way to ensure that as many as possible can participate in the testing. If not the developers are at least sure that the testers are hardcore enthusiasts that are usually not the greatest testers of usability.

As I see it I don't loose the chance to test the software, but the developers loose yet another potential tester. The easiest thing for me to do would be to just wait for the final release, and then participate in the following bug report avalanche that can ruin the reputation of otherwise excellent software.

But as I understand that the busy developer Aaron is struggling with the autopackages I will patiently wait.

---

### Post by potentia on 2007-10-29
> **m_gasior said:**
> sudo apt-get install python-lxml

That did it! Thanks! :popcorn:

---

