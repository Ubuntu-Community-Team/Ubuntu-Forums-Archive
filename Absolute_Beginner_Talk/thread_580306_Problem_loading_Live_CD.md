---
title: "Problem loading Live CD"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by sullitf on 2007-10-18
I am totally new to Linux and tired of Windows, so if this is a basic and very dumb question I apologize.  I am running a Dell Inspiron 1150 laptop with 2.6 Ghz Intel Processor, 256 ram, and 30 gb hard drive.  I want to remove Windows all together (this thing can barely handle XP) so I will not need to partition for Windows.  My problem, however, is getting the live CD to actually start in the first place.  I selected start Ubuntu with safe graphics settings (can't remember the exact wording but you know what i'm talking about hopefully) and it goes through the loading bar screen with "Ubuntu" on it, then gets to what I, being a former Windows user, would call dos (but I know its different in Linux).  it goes through starting everything, everything seemingly shows up okay, but it stops when it gets to " *Running local boot scripts (\ect\rc.local) ".     I have a feeling its because of the 256 ram my computer has, do I simply need to use the alternative file with the text loader instead of the live cd?  I was hoping to be able to test out Ubuntu on this machine before wiping Windows out completely just in case there are some problems.  Thanks for all of your help, can't wait to get Linux up and running!

---

### Post by ofb on 2007-10-18
I guess the first question is are you trying 7.04 or 7.10? 

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

> The minimum memory requirement for Ubuntu 7.10 is 384MB of memory for desktop CDs, and 256MB for other installation methods. (Note that some of your system's memory may be unavailable due to being used for the graphics card.) 

With only the minimum amount of memory available, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed. 

Perhaps your system is not stopped but just crawling? How long did you wait?

Also why are you using safe graphics mode? Did regular already not work?

Do take your time and get the LiveCD to boot normally before you install. You'll want to look around to test that all your hardware is supported before committing.

You might also look at Xubuntu for better performance on low RAM. My slowest box happy with Ubuntu is only a p3 450 but it has 512MB.
[http://www.xubuntu.org/get#requirements](http://www.xubuntu.org/get#requirements)

And welcome to Absolute Beginners. You are /not/ asking dumb questions.

---

### Post by sullitf on 2007-10-18
I'm going for 7.10 by the way, sorry I didn't mention that.  I've been eagerly awaiting the newest version for a week or so and didn't even think about it.

It seems to be stopped, it will get to the Running local boots script, the screen goes black as if it is going to open the GUI, but then it goes back to the previous screen with "Running local boots script" still showing as [OK].

I was trying safe graphics mode just because a video I had run into on youtube earlier this week was saying to, don't really know why.  I guess maybe that was helpful for older versions of Ubuntu that may not automatically detect your screen/resolution setup?

I really don't want to have to wipe the hard drive before testing the Live CD, but it is a second computer I was given for free from a family friend.  It can barely run Windows as it is and I hardly ever use it because I prefer my desktop (about the most use it gets at the moment is taking notes in class).

I'll try loading in the normal mode rather than safe graphics mode and let it sit for a while, maybe it will eventually figure it out and load up.  If not, the computer is growing older every day so I may just go ahead and try loading Ubuntu from the text loader and hope for the best, it won't be that big of a loss to me.

Thanks for your response and help, and if you or anyone else has any advice feel free to jump in!

---

### Post by ofb on 2007-10-18
Well, let us know how things work out.

Since you're below minimum requirements, you really should try the Xubuntu LiveCD for comparison.

And if you feel like experimenting, there's also a custom install that I mention in this thread
[http://ubuntuforums.org/showthread.php?p=3460976](http://ubuntuforums.org/showthread.php?p=3460976)

That could be fun to try, but I doubt it'll get around the RAM issue.

And of course there are other light weight alternatives,
[http://en.wikipedia.org/wiki/Puppy_linux](http://en.wikipedia.org/wiki/Puppy_linux)
[http://en.wikipedia.org/wiki/Damn_Small_Linux](http://en.wikipedia.org/wiki/Damn_Small_Linux)
[http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)
[http://en.wikipedia.org/wiki/Fluxbuntu](http://en.wikipedia.org/wiki/Fluxbuntu)

I'm looking forward to trying the new Fluxbuntu myself.

---

### Post by sullitf on 2007-10-19
Here's the latest on my Windows to Linux conversion.  I tried the live CD again hoping that it would figure it out after a while,  I left it trying to load for a good hour or two while I played Halo and hoped.  It didn't work, so I decided to go ahead and take the plunge.  I installed Ubuntu 7.10 from the alternate disk and it worked!  I'll admit its not the fastest, but it is definitely faster than XP was, and I'm already happy with the change.

On a side note, which I was actually fairly proud of seeing as I've been on Linux for all of 2 hours, I successfully installed the Windows drivers for my wireless card (Linksys WUSB300N) using ndsiwrapper and Terminal.  Granted, I did find a step by step video on YouTube, for which I had to install flash plug-ins, so I wasn't doing it blindly (I only vaguely understand what I did, but it worked!).  [Click here for the video]("http://youtube.com/watch?v=bjKbnk-Vh2I") I used, as well as part 3 and 4 from the same guy.  The real reason I am brining this up, yesterday when I was trying to figure out what I would have to do to get my wireless working I came across ndsiwrapper's list of drivers and my card wasn't listed.  I thought that it could mean I was screwed and for some reason the card could not be used, but it ended up working without any additional work!  What should I do to get these drivers to ndsiwrapper's list so that others with my card will be able to download them (I still had the cd for the card)?

---

