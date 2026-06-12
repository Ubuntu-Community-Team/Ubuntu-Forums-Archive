---
title: "everything works fine--&gt;restart computer--&gt;doesn't work.....need some help please."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by davidwarren on 2007-06-09
OK, so I think I know just enough about this to be dangerous.......
I am running Feisty with compiz, last night I had everything humming along, compiz, cube, avant dock, ect......

I restart my computer, and everything goes to crap. 
some of the issues I ran into upon restart:
my splash screen would come up, then go away as it should, then come up again and be on the desktop.
   that would go away after a while, but it was my first clue that something was amiss
I no longer was running compiz. desktop effects were not enabled, I did not have cube working, avant did not show up
my wireless connection usually starts right up, and prompts me for a password, that didn't happen.
strange things like my weather report in the toolbar forgot where I am, it reverted to default location....
my desktop icons did not show up
I could enable desktop effects, and wobbly windows would work, but still no cube.
I checked the configuration editor, and all my settings were no longer there.
so I change the hsize to 4, still nothing.

eventually, the avant dock would popup (it was not set to autohide) and my icons would show up, but some of the launchers I had in my avant dock were no longer there, some were...

if I started firefox a couple times, the keypass prompt to access my wireless network would come up and I can get on the internet.

There were a couple other things, like I can't move my windows, they stick to the top left corner, and I can't see the top bar ( I don't know what it is called, the one with the minimize/max/close buttons), I am sure there are other things, but I can't think of them right now.

-----------------------
OK, so I tried to search for a solution to this, but I can't find anything, probably because I don't really know what to look for. Any help here would be appreciated. BTW, I did all this once, and then restarted again to see if it would work, but it didn't--everything stopped working again.....

---

### Post by ggaaron on 2007-06-09
If you can't see the top bar with minimalize and so on - alt+f2 and run metacity (for gnome) or kwin (for kde) - probably you have no window manager running, but why? I don't know.

---

### Post by davidwarren on 2007-06-09
is there something like the equivalent of system restore available?

I might just reinstall ubunto, but that would be my third time of reinstalling because I messed something up that I didn't know how to fix...

---

### Post by ggaaron on 2007-06-09
Delete all files in your home directory that are hidden - start with "." <- this should delete most of configuration files (but sometimes along with something that you wanted to keep - be careful) - it may help, but I don't know of a way to revert /etc configs to original form.

---

### Post by davidwarren on 2007-06-09
well I just reinstalled and am going to start fresh....
it seems each time I do that I get a bit better at working with linux, but also a bit better at screwing it up!

---

