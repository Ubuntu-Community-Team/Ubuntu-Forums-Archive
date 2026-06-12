---
title: "Want to Revert Back to My Original ATI Drivers..."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Pyrotechnic on 2007-12-08
When I started Ubuntu for the first time the other day, an update popped up saying there were some Restricted ATI Drivers available.  I installed them and everything worked great.  Recently I've been trying to get Valve's Steam program to run properly.  Someone suggested installing Envy to get the new ATI drivers.  I did.  Everything was fine until I went to watch a video.  Videos work find in a small window, but if I make them full-screen or even if I resize the window to be fairly large, the videos get choppier and choppier.  I've also noticed that when I move my Firefox scrollbar now, it's very choppy, whereas it was quite smooth before.  

I tried reverting back to the Open Source ATI drivers, but I don't think those were what I had installed, because kiba-dock and my compiz fusion things would barely run with those drivers installed.  I'm basically stuck, I have no idea what to do to get everything to work properly again (either by finding those other drivers, or fixing whatever is wrong with these FGLRX drivers).  Any help would be greatly appreciated.

---

### Post by pHreaksYcle on 2007-12-08
Well, to go back to your proprietary drivers, the old ones, all you have to do is reinstall them in the restricted drivers manager again.
System->Administration->Restricted Drivers Manager and click the graphics driver.
Check out this link too! Maybe it will help you with the new ATI driver.
[http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html]("http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html")
Make sure to read carefully though. I didn't and I messed it up the first time!

---

### Post by Pyrotechnic on 2007-12-08
Yeah, I tried that and it didn't work.  Also, Envy was how I got the driver in the first place, so that didn't work.

I did figure it out, however (some of this might be obvious to more experienced users, but I'm a noob).  When you install the new drivers, instead of making a new section entry in the config file, it edits the old driver section (which I knew, but didn't think about).  So, when I'd try to re-enable my old drivers in Restricted Drive Manager, nothing would happen because the settings for the new driver were edited in to those old driver settings in the config file.  So, I removed FGLRX with apt-get remove, went to Restricted Drive Manager, uninstalled those drivers, then reinstalled them, restarted my computer, and it worked.

At least, that's why I'm guessing re-enabling the old drivers didn't work.  Like I said, I'm new to Linux.

---

### Post by pHreaksYcle on 2007-12-11
I'm pretty sure you said problem solved, right?

---

