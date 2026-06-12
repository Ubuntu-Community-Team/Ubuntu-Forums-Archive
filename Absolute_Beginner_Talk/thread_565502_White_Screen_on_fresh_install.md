---
title: "White Screen on fresh install"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by beejaycee on 2007-10-02
I found the solution to my problem but am trying to figure out what happened.  My computer is an e-machine 3000XP, 512MB, with on-board video and an added NVidia GeForce2 w/64MB (which I use in place of the on-board video.  I had previously installed 7.04 and successfully used it.  To prepare for the upcoming 7.10, I did a fresh re-installation, formatting the drives when I did it.  Upon starting up, everything went fine until I logged in.  Then I got the white screen.  Searching this forum I found a post about commenting out the "Load "glx"" line in xorg.conf and it solved the problem.

My question is why was this not a problem on my previous install and it became a problem on a subsequent installations? I tried reinstalling several time and download a new iso but still could not get past the white screen until I did the edit.  There were no hardware changes.  What happened?

Thanks, Bryan

---

### Post by sirgogo on 2007-10-03
Well, there are several possibilities to your problem.

I'm thinking it had to do with recompiling your kernel. Every time you reinstall, Ubuntu recompiles your kernel. As a result, the drivers for your graphics card may have been edited or something, causing Ubuntu not to choose it as the default driver, thus causing you to see a blank white screen.

I think this was the problem that was fixed by you installing the correct drivers, and letting it thus recompile the kernel. To those who disagree, please educate me on what the problem might actually be.

Take it easy. ;)

---

