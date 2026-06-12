---
title: "Root priveleges"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Badger3k on 2007-05-12
I installed the 7.0.4 build on my PS3, and am trying to modify my kboot.conf file.  Unfortunately, even though my own account has administration priveleges, I can't modify anything, since apparently only the root can do that.  Also undortunately, I can't seem to switch to the root user, especially since the windows seem to extend beyond the bottom of the screen and there is no way to shrink them to fit the screen.  The "password" section of the user window is below the bottom of my screen.  

For background, when I start in linux, I get the kboot prompt and have to type in a long list for it to start.  Supposedly I can stop this by changing one letter (an sde1 to an sda1) in my kboot.conf file, but as I (the only operator on the system) can't make any changes, this is pretty much impossible.  So, is there any way I can get permissions to make the changes I need to make, or do I need to scrap the whole thing?

For the other part - is there any way to make the stupid windows actually fit the screen?  :confused:

---

### Post by Happy_Man on 2007-05-12
Hmmm.... people messing up  PS3s for the greater good. I would suggest running
```
sudo dpkg-reconfigure xserver-xorg
``` to fix your resolution problems....

and also, forgive me if I seem ignorant, but I don't have a PS3, and so I must ask....
can't you simply move the window?

---

### Post by st33med on 2007-05-12
> **Happy_Man said:**
> Hmmm.... people messing up  PS3s for the greater good. 

True, I think I'm hearing more hackers than gamers using the PS3 as a computer. Odd, really, but you get a cheap supercomputer with Blu-Ray!

---

### Post by Badger3k on 2007-05-12
> **Happy_Man said:**
> Hmmm.... people messing up  PS3s for the greater good. I would suggest running
```
sudo dpkg-reconfigure xserver-xorg
``` to fix your resolution problems....

and also, forgive me if I seem ignorant, but I don't have a PS3, and so I must ask....
can't you simply move the window?

I'll try that, thanks.  No, the window can be moved right, left, or down, but not up.  In windows without a scroll bar, that means anything below the edge of the screen can't be accessed.  

As for using the ps3 as a computer, my main reason for this is to play the overabundance of avi files I have on my tv instead of my computer.  VLC works great, and I don't have to try to convery my files to a format the ps3 can understand.  Other than that, I mostly use it for games.

Edit - is there some kind of list for what code I need to use for my screen?  It's a standard tv screen (an hd is on my list, assuming my company settles down and gets our hours back up).

---

