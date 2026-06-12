---
title: "Feisty Fawn flash problem."
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by kga5 on 2008-03-20
I know there is a lot of these problems but i have not found a good solution. I cant install flash trough firefox... it says "no suitable plugin available" or something like that. in synaptic i did not find anything that worked... I am not so experienced with installing manually (for example from macromedias own homepage) so if it is the only way please explain well, thanks!

---

### Post by celticbhoy on 2008-03-20
Give this a look :-

[http://ubuntuforums.org/showthread.php?t=729362&highlight=install+flash](http://ubuntuforums.org/showthread.php?t=729362&highlight=install+flash)

---

### Post by wolfen69 on 2008-03-20
first, go to system>admin>software sources and check off all boxes except cd. it will ask to reload. do so. then in terminal:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by stchman on 2008-03-20
> **kga5 said:**
> I know there is a lot of these problems but i have not found a good solution. I cant install flash trough firefox... it says "no suitable plugin available" or something like that. in synaptic i did not find anything that worked... I am not so experienced with installing manually (for example from macromedias own homepage) so if it is the only way please explain well, thanks!

There was a flash update on Ubuntu's site that was removed quickly.  It works very well.  I have it archived on my site.

[http://www.stchman.com/tools/flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.3_i386.deb](http://www.stchman.com/tools/flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.3_i386.deb)

Hope this helps.

---

### Post by kga5 on 2008-03-20
Wolfen:
I did what you told me to do, but i get an error like this (when typing the installation command for flash-nonfree):"...This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate"

stchman: I get an error when i follow your instructions too, like this: Error: wrong architecture i386

---

### Post by stchman on 2008-03-20
> **kga5 said:**
> Wolfen:
I did what you told me to do, but i get an error like this (when typing the installation command for flash-nonfree):"...This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate"

stchman: I get an error when i follow your instructions too, like this: Error: wrong architecture i386

Are you running 64 bit Gutsy?  If yes then this will not work.  You have to do a few special things to get Flash to work in 64 bit OS.

---

### Post by kga5 on 2008-03-20
yes, i am using 64...

---

### Post by Sef on 2008-03-20
Here's a [Howto on Flash on 64-bit systems]("http://ubuntuforums.org/showthread.php?t=476924").

---

### Post by stchman on 2008-03-20
> **kga5 said:**
> yes, i am using 64...

I believe this is the procedure you will need to do.

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

I have an Athlon 64 and a Core 2 Quad but I have yet hesitated to use the 64 bit version of the OS.  I have been reading on the forums and it seems that there is still too many incompatibility issues with 64 bit to get the 10-15% speed improvement.

Maybe in the next year I will upgrade to 64 bit OS.

---

### Post by kga5 on 2008-03-20
well, i am starting to have regrets... but when i get the basic things working ill make it :D

Thanks for all your help! im probably not writing on this topic today anymore. i will try out your solutions
EDIT: thanks both of you! it worked, im glad.

---

