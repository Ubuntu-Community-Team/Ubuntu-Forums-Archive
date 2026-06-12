---
title: "I need to download and install Firefox2 directly from the Mozilla website"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-03-29
For reasons  I don't really understand, since I started playing around with the new FF beta I cannot revert back to FF2.  I tried seeking help figuring that out here [http://ubuntuforums.org/showthread.php?t=735122](http://ubuntuforums.org/showthread.php?t=735122)

Anyway, I have given up figuring out what I did wrong there and now I just want to install FF2 fresh from the website. I downoaded it and "extracted" it to my desktop but now I don't know what to do next.

And please, I know the easiest way to install is from synaptic but as I explain in the other thread I can  get that to work.

Also, once  I get it installed I will need to know how to start it from the command line.

---

### Post by philinux on 2008-03-29
Once you've used FF3 Beta your profile cant be used with FF2. Go into your profile and make sure you make a copy of your bookmarks.html file. 

You'll then have to delete the profile folder and restart FF2.

My advice would be stick with FF3 beta4 as it's much quicker and many improvements.

---

### Post by boriquajake on 2008-03-29
> **philinux said:**
> Once you've used FF3 Beta your profile cant be used with FF2. Go into your profile and make sure you make a copy of your bookmarks.html file. 

You'll then have to delete the profile folder and restart FF2.

My advice would be stick with FF3 beta4 as it's much quicker and many improvements.

OK, it sounds like you might have the advice I need. Is this "profile" perhaps the reason that I can't seem to get FF2 to even start up? The truth is that at this point I don't even care if I import my favorites or any settings or anything I just want to see my good pal FF2 with its ability to work with the google toolbar and run all the flash and java crap you need to use the web. I am not smart enough to work with a beta I need to wait until it is a little farther along.

---

### Post by boriquajake on 2008-03-29
> **philinux said:**
> Once you've used FF3 Beta your profile cant be used with FF2. Go into your profile and make sure you make a copy of your bookmarks.html file. 

You'll then have to delete the profile folder and restart FF2.

My advice would be stick with FF3 beta4 as it's much quicker and many improvements.

Uhm, where is my profile?   :)

---

### Post by forrestcupp on 2008-03-29
Open up Nautilus in your home directory.  Go to the View menu and check the 'Show hidden files' box.  Your profile directory is in **.mozilla**.

But I'm pretty sure that if you were to install a newer version of FF3 than what you have, Flash and Java would just work for you.  I'm running Swiftweasel 3.0b4.5 and it just worked without any tweaking from me.  (Swiftweasel is just Firefox that has been compiled in an optimized way).

---

### Post by boriquajake on 2008-03-29
> **forrestcupp said:**
> Open up Nautilus in your home directory.  Go to the View menu and check the 'Show hidden files' box.  Your profile directory is in **.mozilla**.

But I'm pretty sure that if you were to install a newer version of FF3 than what you have, Flash and Java would just work for you.  I'm running Swiftweasel 3.0b4.5 and it just worked without any tweaking from me.  (Swiftweasel is just Firefox that has been compiled in an optimized way).

Cool, that sounds good. How do I aquire this "swiftweasel" you speak of? Or, in view of my lack of technical prowess should I not push my luck?

---

### Post by louieb on 2008-03-29
Wanted to do the same thing in Hardy beta. What works in Hardy may work for you. This thread shows what work for me and several others. 
[[SOLVED] How do I revert to Firefox 2.12 in Hardy?]("http://ubuntuforums.org/showthread.php?t=733048")

---

### Post by forrestcupp on 2008-03-29
If you still want to try Swiftweasel, go [here](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=231607) to download the latest beta version.  The thing about Swiftweasel is that it has been compiled to be optimized to run on certain processors, so you'll have to pick the one that is for your kind of processor.  I have an Athlon64, but I'm running 32-bit, so I chose the one for Athlon XP.

Just download and install the deb.

---

