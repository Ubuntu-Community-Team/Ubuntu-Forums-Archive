---
title: "Ubuntu installed find, but now the windows install isnt working."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by StuffGuy on 2007-11-13
Just installed Ubuntu on a 3-4 year old dell with XP pro.  It has two 80 gig hard drives, with space on the secondary one without the XP OS, so I figured Id defragment that, then resize it so Id have about 20 gigs for Ubuntu.  Installed and booted okay, and I could originally see the Dell Utility (very small partition on the XP drive with dell stuff on it), Main (The XP Install), and the Storage (which I shrunk to make room for the Linux install) on the Ubuntu desktop.     

Everything seemed to be working in Ubuntu, so I figured Id switch over to windows real quick to make sure it was working right too, which it wasn't.  It booted, let me log in, my background showed up, but then it sat there not loading the shell until I figured it was time to reset the computer and see if I could figure out what was wrong in Ubuntu.  Logged back into Ubuntu, and the Main drive with the XP OS was no longer visible.  Checked the ubuntu file system folders, and the media/sda2 folder, which I'm 99.99% sure should be the XP OS partition, now shows up as empty.   

Annoying thing is I took care to make sure I wasn't touching that drive when partitioning for the install, while the drive I did mess with is working fine, including all the old data from the windows install on that drive under Storage.  So I basically don't know enough about ubuntu and partitions to figure out what I screwed up with that partition, which is obviously still there since windows will still boot from it.  

I suppose I should point out that the shell which should be booting inst the standard, but is BB4lean, a minimal version of Blackbox for windows.  All the files for that are on the windows OS partition that is no longer visible in Ubuntu.  

Btw, I wasn't sure what the proper forum for this was, so I put it here since I'm new to Ubuntu, have minimal linux experience, and only a tad more unix experience.  

Help please?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
you said you resized the windows partition?
This is always risky bissness ... i have done it a few times now like 3
I killed windows 1 time 
So any way its not ubuntu thats mest up its something in windows or something with your hard drive like a bad sector
what does it do now when you try to boot xp

---

### Post by StuffGuy on 2007-11-13
Not the windows OS partition, I resized the partition on the second hard drive, which just had a bunch of data files.  I intentionally avoided touching the first hard drive with the OS partition.  

I also just realized I've typo'd the thead title.  That find was supposed to be fine obviously.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
lol i just reread your post
you said you didnt resize xp just the part with storage right?
then your xp died for a reason unrelated to linux 
it probly would have died anyway

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
> **StuffGuy said:**
> Not the windows OS partition, I resized the partition on the second hard drive, which just had a bunch of data files.  I intentionally avoided touching the first hard drive with the OS partition.  

I also just realized I've typo'd the thead title.  That find was supposed to be fine obviously.

dont worry i didnt see that

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
now for fixing the problem ... hopefully
you are running blackbox on your windws so your far more into windows then i ever got
perhaps reinstall blackbox?
becuase you said the shell stoped loading
can you switch back to explorer to see if that loads

oh and as for ubuntu not seeing the files thats not good ... sugjest hardware failure thats why i said that before

and thats about all i know about it
so best of luck and hope some one else sees your post
tell us how it goes :)

---

### Post by StuffGuy on 2007-11-13
It seems extremely unlikely the XP installed hard drive would choose to die at the exact same time I was installing Ubuntu.  I suppose its possible, but it seems like that would be terrible luck.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
> **StuffGuy said:**
> It seems extremely unlikely the XP installed hard drive would choose to die at the exact same time I was installing Ubuntu.  I suppose its possible, but it seems like that would be terrible luck.

yes it would seem like terrible luck
but this is my best gess
i really can't think of anything else 
after ubuntu stoped seeing the files in the xp part does it still try to boot at all?

---

### Post by StuffGuy on 2007-11-13
:confused::confused::confused:

Ive got the option to run harddrive diagnostics from my boot menu, which I did just to make sure the drive wasnt failing like you suggested it might be.  Came back with both drives passing.  

Then I decided to try booting windows again.  Booted, and this time blackbox loaded, but not all of my startup programs started up, and I couldnt start any of them, or Opera, which is the web browser I use most of the time in windows.  

I did get a look at My Computer, which showed the Main drive with the windows install, but not the Storage drive where i shrunk the patition and installed linux.  At about this point blackbox locked up on me again so I reset the computer figuring Id uninstall blackbox and deal with explorer while I tried to figure out why I couldnt see the Storage drive.  Rebooted, except this time blackbox loaded, as well as all the startup programs.  Everything is working fine, and I can see the Storage drive, which has all the files on it it should.  

So Im typing this from opera in windows with a working blackbox shell now.  I guess ill reboot into windows again and see if its randomly decided to fix itself, in which case Ill let the crazy randomness slide, or wether its going to screw with me and go haywire again.  If that works Ill switch back to ubuntu and then back to windows and then back to ubuntu again a couple times to see if its going to keep working or randomly break on me again.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
ya i have no idea whats wrong with it :) good luck

---

### Post by StuffGuy on 2007-11-13
So everything is now working fine, in both OS's.  Apparently I should have stuck with the troubleshooting procedure I used to use when I was six.  "Keep restarting the computer and praying it fixes itself."  Thanks for trying to help though.

---

