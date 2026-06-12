---
title: "Tibook G4/550 screen display not right with livecd"
date: 2008-06-28
forum: Apple Hardware Users
---

### Post by nothing_is_not on 2008-06-28
Hey, 

My tibook boots the livecd of 6.06 fine, and loads into the desktop. But the powerbook display shows the desktop screen twice on top of eachother. 

How do I set up the video card such that the screen is normal? 

thanks a lot.

---

### Post by stream303 on 2008-06-28
Unless you have a special need for 6.06, you can obtain later community-supported versions here:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

That being said, be sure to see this faq which was recently updated which might help:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-d0d44212d7476e04bb184740b076bb01f839882d](https://wiki.ubuntu.com/PowerPCKnownIssues#head-d0d44212d7476e04bb184740b076bb01f839882d)

Although the reference is for an ibook, the yaboot boot prompt may need to be changed to take into account your different resolution:

```
live-nosplash-powerpc video=radeonfb:1152x768-24@60
```

This would be for 6.06 which I believe did not have the ide-core issues that later versions did (see the original reference to that line in the faq)

If you just want to install and have no desire for the live-cd, you may be better off doing a text-based install (full gui afterwards) with an "alternate" install image.

---

### Post by nothing_is_not on 2008-06-28
Thank you, 

Now,  the reason why Im using 6.06 is because it happened to be laying around at the moment. I also have a fedora 8 live cd which gives me the same problem. 

Your suggestion from the known ppc issues makes sense. 

I can't find the " : " on the keyboard though and hooking up an USB keyboard is no worky either...

so.... kinda stuck there I guess 


cheers,

---

### Post by stream303 on 2008-06-28
Hmm.. unless the key got remapped, or maybe the silkscreen got rubbed off, the key should be just to the right of the "L" key.  Hold down shift and hit that key to get the colon.

Assuming a standard keyboard layout - maybe yours is different or for a different locale...

---

### Post by nothing_is_not on 2008-06-30
I got the colon alright, awesome, it booted with the no-splash command you stated above. 
Only, though, did the powerbook boot off the livecd but with the same weird double screen.

Like this
[IMG]http://i43.photobucket.com/albums/e381/schoft/kubuntuscreen.jpg[/IMG]

---

### Post by stream303 on 2008-06-30
Sometimes the live-cd has problems configuring X, whereas the non-live "alternate" installer doesn't, so that is an option.

I suppose you could try reconfiguring X in this environment for Dapper with

```
sudo dpkg-reconfigure -phigh xserver-xorg
or
sudo dpkg-reconfigure xserver-xorg
```

and then logging out and logging back in to see the changes.  (Not rebooting - just logging out of your session)

---

### Post by nothing_is_not on 2008-07-08
Hey, 

Im sorry if I gave the impression I'm ignoring your advice to download a both more recent and alternate install. Here in Belgium we have a downloadlimit and im almost pushing it already

One thing I forgot to say is the sort of splitscreen already starts before the desktop gets loaded. Iow there's also the same type of screen right after I type "live" in yaboot. 
No I followed the commands steam stated and obviously it leads to or a screen where I select my resolution for my laptop ( in my case 1152 x 768 ). 

Now, what happens is that I have this orange rectangle that shows me where i'm toggling between several screen resolutions. It appears I can select a new screen resolution by filling in an asterisk between the brackets the preceed the screen resolution. 

The other sudo command you suggested, stream, is the one that leads me to a series of configuration screens in the same bleuish screen that enables me to choose the screen resolution. 
This series of screens also finally leads to the same screen resolution screen, the one that only appears in the first sudo command. 
When all these steps are done, I get a small yaboot screen in between the two screens, which doesn't really work.. 

Did all this with just logging out instead of rebooting/shutting down and then bootin up again.

Kindof confusing here...

---

### Post by stream303 on 2008-07-09
Did it show this problem with the previous os, or was this a recent acquistion?  I've never heard of the orange rectangle thing, so this is a real head-scratcher.  Almost sounds like there is some boot remnant of the previous os interfering.

---

### Post by nothing_is_not on 2008-07-15
hmmmzzz. 

OK im gonna wait till I can download a more suitable cd somewhere somehhow. 
Won't be before august though... that's when my hopefully limitless ISP is connected... 

ubuntu's supposed to be more simple than that, right?

---

### Post by stream303 on 2008-07-15
For the first time in history, a PPC version (Hardy 8.04 live-cd) has appeared in a book on the included dual-sided dvd:

[http://ubuntuforums.org/showthread.php?t=859751](http://ubuntuforums.org/showthread.php?t=859751)

This might help get you up and running without internet access - If you go this route, search out the issues/solutions about initially installing without any connectivity.

---

