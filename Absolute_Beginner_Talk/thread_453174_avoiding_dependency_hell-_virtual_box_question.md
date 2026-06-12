---
title: "avoiding dependency hell- virtual box question"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-24
Here's another silly question from me. Forgive me- this is a new universe.

 I've seen a number of references to 'dependency hell' in various places, and I hope to avoid it. Now I come to install a package not in a repo (the package is virtual box). Though it has a package for Feisty, the site also says it needs some stuff, 

<quote>
You will need to install some additional libraries on your Linux system in order to run VirtualBox - in particular, you will need libxalan-c, libxerces-c and version 5 of libstdc++. How to install these will depend on the Linux distribution you are using.
</quote>

So, here are my questions:
a) how do I check if I already have something a sw depends upon, assuming I know?
b) do I just look for the extra files I need, and find them whereever they may be, even if that is outside of the repos? 
c) if I don't know something is needed, and a new sw won't work because some file is missing, is it OK to install the missing stuff AFTER installing the new sw? Or will that vary on a case by case basis?

thanks.

---

### Post by ruy_lopez on 2007-05-24
Search for the dependencies in Synaptic package manager. Usually the libraries that are required are the development libraries. So if "libstdc++" has a check box next to it in Synaptic, to be on the safe side, check the one that also says "libstdc++-dev" (development libs all end with -dev). Then apply those changes. Do that for each of the listed dependencies, then try and compile the sources for the package.

Dependency hell is an exaggeration, its more like a dependency treasure hunt.

---

### Post by Soybean on 2007-05-24
Another point: the term "dependency hell" comes from older linux systems... Synaptic can almost always find all your dependencies for you and install them automatically, all at once. People still use the term, but it's not really appropriate anymore. Compared to the way dependencies were handled by linux systems in the mid-90's, this is dependency heaven. ;)

In the case of VirtualBox, I think they have a .deb for Ubuntu, don't they? Just download that and install it. It knows what its dependencies are, and if you don't already have them, Ubuntu will find them for you. :)

And if there's no appropriate .deb or 3rd-party repository for something you want to install, then like ruy_lopez says, it's just a matter of figuring out what package(s) you need and installing them, usually from Synaptic.

---

### Post by Terl on 2007-05-24
Yes, Virtualbox has a .deb.  Just use that and you are set.  Soybean is right.

---

### Post by ginestre on 2007-05-24
Thanks for your comforting replies. However, when I downloaded virtual box deb for feisty, and clicked on it, the installer opened up with an error message "Couil,d not open. Maybe the package is corrupt, or maybe you don't have permission." 
In case it was corrupt I downloaded it again. Same story.

This is the first time I install a non-repos package. Am I missing some step?

---

### Post by Terl on 2007-05-24
> **ginestre said:**
> Thanks for your comforting replies. However, when I downloaded virtual box deb for feisty, and clicked on it, the installer opened up with an error message "Couil,d not open. Maybe the package is corrupt, or maybe you don't have permission." 
In case it was corrupt I downloaded it again. Same story.

This is the first time I install a non-repos package. Am I missing some step?

When you click the link do you get the option to open it with the installer (usually the first option)?  I use that and do not actually save the file locally.

If you are saving it locally how are you trying to use it?

---

### Post by ginestre on 2007-05-24
> **Terl said:**
> When you click the link do you get the option to open it with the installer (usually the first option)?  I use that and do not actually save the file locally.

If you are saving it locally how are you trying to use it?

1) Yes, that was the mistake: i saved it to my PC and then tried to open it with the package manager.

2( However, after your post, I a) reset the machine- you never know! and b) followed your instruction above. I got the option to open it with the installer, and after  afew seconds exactly the same error message as before- corrupt file/wrong permissions.

Have I possibly messed up the package manager by the foolish actions at (1) above?

---

### Post by Soybean on 2007-05-24
Hmm... downloading it should have worked fine too. 

Well, it's giving 2 possibilities, so we should consider both:
1) Corrupt file -- could be a weird problem with your network connection or maybe something with their web server. I'd open the file in a text editor and see if it looks like an HTTP error instead of a package file.

2) Wrong permissions -- have you been able to install other things? Can you use sudo? If you're running as a non-privileged user (perhaps on a computer someone else set up for you?), you might not be able to install things.

---

