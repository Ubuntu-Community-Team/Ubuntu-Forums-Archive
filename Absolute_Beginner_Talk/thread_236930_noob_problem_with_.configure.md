---
title: "noob problem with ./configure"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by drtpw on 2006-08-15
I'm still a noob.  I have Ubuntu up and doing everything I ask of my PC.  I love it.  I even downloaded and installed Xsane 0.991 for scanning to PDF's.  Downloaded build-essential and worked through the errors in ./configure by getting the proper packages, etc.  I'm feeling good so I decide to get an FPS for a little fun.  But after I extract the files and change to the directory, when I run ./configure, I get "./configure: No such file or directory".  What am I doing wrong?  I have searched the web and the forums, as well as a couple of books looking for answers and can't find it.  Hope someone can help me.  Thanks in advance.

---

### Post by Kobalt on 2006-08-15
There must be an "Install" file in the FPS directory you downloaded, with instructions on dependencies and HowTo install the application. 
If not, can you tell us a bit more about that FPS : what's that ? What's your graphic card ?

---

### Post by Perfect Storm on 2006-08-15
Can you point to the thing you want to compile. Sometimes it's a bit diffrent depending how the maker(/s) made it.

---

### Post by stricevics on 2006-08-15
> **drtpw said:**
> But after I extract the files and change to the directory, when I run ./configure, I get "./configure: No such file or directory".

See if the file actually exists (sometimes there's no configure file) and check if it is set as an executable. If not: ```
chmod +x configure
```

If I am not mistaken with syntax, that should enable its execution.

Hope it helps,

St.

---

### Post by aysiu on 2006-08-15
Is XSane 0.97 not good enough? That's a lot easier to install.

---

### Post by drtpw on 2006-08-15
Thanks for the quick replies.  Let's see if I can answer some questions.  I'm trying to install the game, Cube.  My graphics card is an Nvidia 5700 Ultra.  I do have the drivers loaded and the xorg.conf file corrected so the card is running 3D nicely.  As far as pointing to the thing I want to compile, I have no idea.  I'm a noob.  I'm just following the directions given all over the place on installing tar.gx files (./configure, make, make install).  And I've done it before.  Btw, Xsane 0.97 does not have PDF as a save option and I do that a lot.  That's why I went through the bother of getting 0.991 installed.  Plus, I learned a lot.  I've been all through the Cube files and can't find a configure file.  And I've been to the web site.  Any ideas?  Thanks.

---

### Post by Perfect Storm on 2006-08-15
I guess it's cube 1 you are trying.

Yuo need both the binary and the source in this case to compile. But you can just use the binary to play the game.

Dynamic binary: cube_2005_08_29_unix.tar.gz
Source:  	cube_2005_08_29_src.zip

---

### Post by drtpw on 2006-08-15
AI, thanks for replying.  I'm chuckling here because I must be a super noob.  Now I have both the source and the binary on my desktop and extracted and am at a loss on my next step.

---

### Post by Perfect Storm on 2006-08-15
It's a bit tricky because you have to write your own make file to compile.

But you have the binary, you can run the game now, by:
```
cd /to/the/extracted/folder
sh cube_unix.sh

```

---

### Post by drtpw on 2006-08-15
AI,
Thanks, but no matter which extraction I go to, when I type in sh cube_unix.sh I get a no such file or directory message again.  At work now, but I'll do a little digging on this later tonight.  Thanks for pointing me in the right direction.

---

