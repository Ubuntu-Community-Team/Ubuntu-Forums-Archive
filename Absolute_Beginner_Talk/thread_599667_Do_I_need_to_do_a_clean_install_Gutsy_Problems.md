---
title: "Do I need to do a clean install? Gutsy Problems"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-11-01
Everything in Feisty was working perfectly, and since I've upgraded to Gutsy, I've had all sorts of problems (without any significant benefits :'(). Here's a quick summation:

-My webcam no longer works (it was installed via repo). Not only did it break, but it prevented my computer from even booting (even in recovery mode). I finally go back into my desktop, but the webcam is still broken. Reinstalling it does no good.

-Amarok is completely messed up. Half of the time it won't load up, and then it goes into "Uninterruptible" status and I can't even kill it. The other half of the time, it loads and freezes. I got it to run once, and it was going insanely slow and froze within a few songs. Running from the terminal produces no helpful output.

-Network manager randomly breaks. I have to occasionally switch between two wireless networks. I click on the bars, choose the other network, and it does nothing. If I open System > Admin. > Network, it freezes and fails to load, but the Network window pops up still (it just doesn't have any widgets on it), and that will usually force the network manager applet on the panel to switch to the network I selected earlier. Again, nothing from the terminal / logs help.

-Nautilus will randomly break. All my desktop icons disappear and I can't open nautilus. Running it from the terminal freezes and produces no output. The log files show nothing.

-My wirelessly networked printer used to work perfectly, and now it's broken. I removed the printer completely (and everything I downloaded along with it), followed a Gutsy guide, and it still doesn't work, and gives no error messages.

-In Eclipse, I changed absolutely nothing. When I open Eclipse, it tries to open the files I had open when I closed it last (like it used to), but it always throws some generic error with no further details. When running something, it tells me that it doesn't know what workspace_loc is. I found a few other people having problems online, but no one (that I found) had a working solution. It also freezes up after a few minutes.

And those are only the ones I can think of right now.

I don't say this to whine about Gutsy or Ubuntu in general. Instead, my question is: Since I have so many problems (many fundamental) that all occurred immediately after upgrading to Gutsy, and they don't seem to be common problems that a lot of other people have, is my best solution probably going to be to just do a clean install? I really don't want to, since backing up my /home will be a huge pain, but I'd rather have a working system. I upgraded from Dapper-> Edgy -> Feisty with no problems, so I don't see why there'd be a situation with Gutsy. Everything was installed from apt with default repos. I have proprietary graphics drivers, but Compiz is turned off.

Any tips?

---

### Post by clancymf on 2007-11-01
I am not an expert by any means but I read this forum alot and it seems that most of the gusty problems have come when people upgrade.  

I did a clean install and everything worked wonderfully.  If that is an option for you I think I would do the full install than pulling your hair out trying to fix each of these problems and other ones that you have yet to identify.

Good luck.

---

### Post by Pumalite on 2007-11-01
What are you waiting for?

---

### Post by jayaramk on 2007-11-01
rather than fioxing each of these errors and fixing i would rather suggest you to again have a clean install of the ubuntu!!!!

---

### Post by ofb on 2007-11-01
It's hard to say what's the best way forward. Certainly there's other threads with similar problems. I haven't noticed a pattern yet to indicate upgrade would be different than fresh. On my two machines I've had one bad upgrade and one no-problem fresh, but I wouldn't want to generalize from that.

Just for information, you /can/ do a fresh install without formatting the drive.
[http://ubuntuforums.org/showthread.php?t=596932](http://ubuntuforums.org/showthread.php?t=596932)

But you really should be backed up before any major operation. Or just in general. I've even had two drives fail at the same time. Probably you know that, but it bears repeating.

---

### Post by Maestro23 on 2007-11-01
You're good to go if you have a /home.  Just don't let Ubuntu touch that during the Install.

---

### Post by scrooge_74 on 2007-11-01
Either do a fresh Gutsy install or go downgrade back.

Sometimes is better to stick with what is working, if it ain't broken just tweak it

---

### Post by tonyr1988 on 2007-11-01
How do you downgrade? That would be awesome.

My hesitation for a clean install is:

1) I would need to download and burn a new CD (and my Internet isn't the fastest and has been cutting out quite frequently lately).
2) My ~ is not on a separate partition, so I would need to back up all of that.
3) I would have to reinstall all of my programs.
4) There were several things needed to get everything on my laptop working correctly - I would have to: a) find all of that again, and b) do it, which may be easier said than done.

Plus, I really don't want to format every 6 months. :P

---

### Post by akiratheoni on 2007-11-01
Well, you could get AptOnCd then burn your installed packages to a CD then when you reformat, you just pop in the CD and then download all of your packages again. 

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by scrooge_74 on 2007-11-01
To start what ever you do make a separate /home partition, [here]("http://www.psychocats.net/ubuntu/separatehome") is a good guide I have used before.

---

### Post by tonyr1988 on 2007-11-01
> **scrooge_74 said:**
> To start what ever you do make a separate /home partition, [here]("http://www.psychocats.net/ubuntu/separatehome") is a good guide I have used before.
I used to have a separate ~ partition, but I could never figure out the right size. It was definitely easier to just have it integrated into root, and I didn't figure I'd have to do a lot of clean installs, since I install software the "right" way. :P

---

