---
title: "Building Wine X from Source"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-24
This is the technology by Cedega. On this forum:

[http://www.linuxforums.org/forum/wine/10062-winex.html](http://www.linuxforums.org/forum/wine/10062-winex.html)

People were saying that it is possible to build Wine X from the source so that you don't have to pay for a US$5 month subscription. 

Here are the source files:

[http://www.transgaming.com/sources.php](http://www.transgaming.com/sources.php)

How do I begin to build this thing from source to run my games? I don't have a graphics card yet, I am looking at buying one but I want to know that this software will work before I spend the money on the graphics card. 

If I was able to build Wine X from source I think it would work better than Wine (which I already have)

---

### Post by Happy_Man on 2007-04-24
First you need the tools to compile: ```
sudo apt-get install build-essential checkinstall
```

Then you need to download the file with the source to your desktop. 

Right-click on the downloaded file and say "extract here."

After, change directories to your Desktop:```
cd Desktop
```

Then, change into the directory of the file of the unzipped folder: ```
cd name_of_folder
```

Then, run the following commands ONE AT A TIME:```
./configure
make
sudo checkinstall
```

If any of this doesn't work, post up with what happened, and we'll see how to fix it. ;)

---

### Post by Toxicity999 on 2007-04-24
Not directly on topic... but If you're going to use WineX you might as well just use wine, WineX has little over wine, and you can get wine in nice working Debs. The only thing that makes WineX appealing to users is the fact that Cedega five it the pretty (to some degree) Face. If You _really_ want to try it anyway, search for the WineX CVS script which will build it for you pretty much.

---

### Post by Wake Rider on 2007-04-24
I have successfully installed the compiling tools from the Feisty Disk

On this site:

[http://www.transgaming.com/sources.php](http://www.transgaming.com/sources.php) 

I click on the first 'here' that is a link.

It comes up with this

[http://cvs.transgaming.org/cgi-bin/viewcvs.cgi/](http://cvs.transgaming.org/cgi-bin/viewcvs.cgi/)

How do I download these files??

---

### Post by Happy_Man on 2007-04-24
Wow, not even a .tar.gz? That sucks for them... can't even roll a tar. Anyway, I really do have to agree with Toxicity, Wine is just as good as WineX, plus it's available in repos, or if you want to compile from source, it gives you excellent tarballs to use. Unlike these WineX people. Is there any special reason you want WineX?

---

### Post by Wake Rider on 2007-04-24
I found this script on the internet. 

[http://oktyabr.wordpress.com/2006/12/23/killer-script-to-install-winex-from-cvs/](http://oktyabr.wordpress.com/2006/12/23/killer-script-to-install-winex-from-cvs/)

Should I attempt this or is there something more I need to do to make WineX work?? I'm sorry I sound a little nervous, its just that I have already destroyed my system once when I accidentally modified /bin/sh.

---

### Post by Wake Rider on 2007-04-24
> **Happy_Man said:**
> Wow, not even a .tar.gz? That sucks for them... can't even roll a tar. Anyway, I really do have to agree with Toxicity, Wine is just as good as WineX, plus it's available in repos, or if you want to compile from source, it gives you excellent tarballs to use. Unlike these WineX people. Is there any special reason you want WineX?

It doesn't have to be WineX, I just wanted the best possible solution that would run games on Ubuntu with the least amount of problems, and I saw that Cedega appeared to be the most popular, but I don't want to commit to a subscription service and so I was trying their free version.

---

### Post by Wake Rider on 2007-04-24
> **Toxicity999 said:**
> Not directly on topic... but If you're going to use WineX you might as well just use wine, WineX has little over wine, and you can get wine in nice working Debs. The only thing that makes WineX appealing to users is the fact that Cedega five it the pretty (to some degree) Face. If You _really_ want to try it anyway, search for the WineX CVS script which will build it for you pretty much.

Is there really not that much difference? I already have the basic Wine installed, I did try to run Microsoft Home Publishing 2000 with it but it failed after activating the Windows installer. I'm just trying to see if something will run games reasonably well under Ubuntu before I fork out for a graphics card. 

Ubuntu has my tower case to itself. I use Windows on a laptop. This way I keep the systems separated until I am confident enough in using Ubuntu to attempt a dual-boot. Though I am trying to build a desktop on the tower case to try and do as much as possible without Windows.

---

### Post by Wake Rider on 2007-04-24
I have ordinary Wine, and I tried installing Roller Coaster Tycoon 2

[http://appdb.winehq.org/appview.php?iAppId=2594](http://appdb.winehq.org/appview.php?iAppId=2594)

It installed perfectly fine, but when I clicked on it to run it or activated the autorun in the terminal, it failed to launch the programme. It says it failed to initialize graphics. I have a strong hunch that it is because I need to buy a graphics card.

From the experience of other users, is this a problem with Wine or the absence of a Graphics card??

---

### Post by Old *ix Geek on 2007-06-14
> **Wake Rider said:**
> From the experience of other users, is this a problem with Wine or the absence of a Graphics card??Neither!  I posted [this thread](http://ubuntuforums.org/showthread.php?t=457496) describing the exact same problem, and when it got no response I continued trying on my own to make it work.  I don't know that I could recount everything I did, but RCT2 now plays beautifully--with the exception of a sound problem (explained in the thread I posted).  So, from my experience, the problem you're experiencing is neither a wine problem nor a problem with your graphics card.

EDIT: The sound problem appears to be solved now; see the other thread for details.

---

