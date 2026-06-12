---
title: "glxinfo"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-07-22
How do I reinstall it? Like, totally rip out everything related and start a fresh?

It used to work, now since I've been messing around with ATI drivers which **still** don't bloody work (another story, check my other posts) it just crashes X.

I've tried reconfiguring X, undoing all changes I can see that the ATI drivers might have made, reinstalling my kernels. 

Now just reinstalling anything *xorg* - *fingers crossed*

Any suggestions?

*prepares to see yet another cry for help sink and become ignored*

---

### Post by brent113 on 2007-07-22
Have you tried anything yet?  Is this a fresh fesity install aside from the ati drivers?  And are you using the default open source ati drivers?

---

### Post by Old Pink on 2007-07-22
I've tried reinstalling the kernels, everything with xorg in the name, anything that seems remotely related, and tried reconfiguring the xorg-server.

Feisty is a few days old, was working fine (glxinfo was) until today when I followed a guide like I said in another of my posts (keep them separate, check there) that ****** glxinfo, tried undoing everything there to a certain extent with no luck.

---

### Post by Old Pink on 2007-07-22
This is the guide that caused the destruction: [http://ubuntuforums.org/showthread.php?t=406389](http://ubuntuforums.org/showthread.php?t=406389)

Mostly the second post.

---

### Post by brent113 on 2007-07-22
Hmm, I know you don't want to hear this, but I'd probably go for a complete reinstall of feisty, and here's why:

It sounds like you have made a lot of significant system changes on top of each other, perhaps without remembering some you did, and even if you did manage to get it to work, chances are down the line something will happen as a result of this.

First, you could try doing a complete remove of every related package and then reinstalling, that might work too.

---

### Post by Old Pink on 2007-07-22
What's the point in reinstalling? It's just a damn waste of time. The only current problem is glxinfo doesn't tell me that my system doesn't work, I know that already. There is a way to change this back without reinstalling, there has to be.

---

### Post by brent113 on 2007-07-22
Yes there is, you'll have to find exactly what caused the problem and restore that, which may take much more time than reinstalling.

I'm just trying to help out.  Based on your join date, it looks like you've been using Ubuntu for quite a bit longer than I have.  I've got to go for a few hours, hope this helps this thread stay fresh.

---

### Post by sad_iq on 2007-07-22
Well I would have to back **brent113** on what he said for a few reasons...the packages you installed probably left your system full of dependencies that could conflict with the packages you need to make direct rendering work. Also the guide that broke your config has done some changes to the kernel modules and maybe they'll conflict with your install attempts(probably that's why dpkg-reconfigure xserver-xorg fails...who knows). Also reinstalling the kernel and xorg and all that won't do anything significant unless you used **--purge** when you removed them and made sure they have been completely removed and all theyr dependencies :( . Cleaning a system is not allways the easyest option!!!

---

### Post by Old Pink on 2007-07-23
Well, it wasn't pretty, but I fixed glxinfo without reinstalling. 

Still haven't got direct rendering working, but it's a work in progress. :) 

And yeah, I guessed you were newer than me lol, but no worry, it's sorted now. ;) 

Reinstalling everything is very much the Windows way to fix things, we're past that now.

---

