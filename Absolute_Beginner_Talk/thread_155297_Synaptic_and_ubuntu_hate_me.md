---
title: "Synaptic and ubuntu hate me"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Zieb on 2006-04-04
I was finally getting the hang of this whole linux thing and saw a package I really needed if my fiancee was going to let me keep linux and not Windows on the computer (I'm not partitioning, she's going to fill way too much of our little 20 GB harddrive with MP3s and movies for two operating systems to be an option).  Anyway, for some reason synaptic closes itself imediately after opening now.  I don't even have time to get a good look at it before it's gone.  The same thing happens when I try to open pretty much anything besides the time and date in the administration menu.  Anyway, any help would be appriciated, because I'm about three seconds away from just breaking down and putting XP on here (getting acclimated to linux has not been easy thus far, and this is just about the last problem I can handle before admitting that I'm just not linux material).

---

### Post by dcstar on 2006-04-04
[QUOTE=Zieb]I was finally getting the hang of this whole linux thing and saw a package I really needed if my fiancee was going to let me keep linux and not Windows on the computer (I'm not partitioning, she's going to fill way too much of our little 20 GB harddrive with MP3s and movies for two operating systems to be an option).  Anyway, for some reason synaptic closes itself imediately after opening now.  I don't even have time to get a good look at it before it's gone.  The same thing happens when I try to open pretty much anything besides the time and date in the administration menu.  Anyway, any help would be appriciated, because I'm about three seconds away from just breaking down and putting XP on here (getting acclimated to linux has not been easy thus far, and this is just about the last problem I can handle before admitting that I'm just not linux material).[/QUOTE]
Open a terminal, type:
```
sudo synaptic
```
and report back what is displayed in the terminal.

---

### Post by Zieb on 2006-04-04
It says:
(synaptic:8693): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Segmentation fault

---

### Post by Mustard on 2006-04-04
[QUOTE=Zieb]It says:
(synaptic:8693): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Segmentation fault[/QUOTE]

Hmm..well segmentation fault is not good.  The first part of the error about GTK stuff is probably pretty normal with opening a graphical app via command line, but the segmentation fault is a fatal crash of the application.

I'm not sure how to proceed from there, other than perhaps completely removing synaptic and reinstalling via the command line.

-edit-

Actually looking at your description of the problem and other issues you are having I'm curious about something.  

Did you install using the 'expert' install option?

What does this command output?

```
sudo whoami
```

Also, what do you get if you try to start synaptic with this command from terminal..

```
gksudo nautilus
```

---

### Post by Zieb on 2006-04-04
Well, it told me I'm "root".

When I typed the second thing it gave me an error message and then my computer blacked out.  I'll try to get the message up but I figured I'd write the first part now just in case it resets again.

EDIT:
Okay, it said:
(nautilus:7060): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Also, it opened a "root" window.

---

### Post by Jason_25 on 2006-04-04
You may have a hardware problem.  Try running a few passes of memtest86 from the boot screen.

---

### Post by Zieb on 2006-04-04
I'm beginning to think that's what it is.  Windows 98 was giving me a lot of trouble on the old harddrive (i.e. not starting up everytime), then we put XP on the old harddrive and it refused to start at all (it didn't even get to any point where it was actually loading Windows).  Then I put this new harddrive in and put Ubuntu on and things were alright for a few days and now this.  What kind of hardware problem could cause three different problems on three different operating systems and two different harddrives?

---

### Post by cx2610 on 2006-04-04
Like he said, do the memtest many times. I had a similar problem back in the day. I open up the computer and unloaded the RAM, loaded it back in and haven't had a problem since. Also, if you choose the unload the RAM, look at the RAM to make sure there aren't any burn mark or anything.

At this moment, I can't think of anything else that would be bothering your computer.

Reehan

---

### Post by halitech on 2006-04-04
reading the problems you are having Zieb, I'd have to agree with cx2610. It looks like you probably have a memory problem. Only other thing I can think of would be a heat issue.

---

### Post by Mustard on 2006-04-04
The memtest from the Grub boot menu should help you diagnose a RAM problem.  If you get errors on the memtest then that could well be the culprit.

---

### Post by Zieb on 2006-04-05
Thanks guys.  I couldn't even read these last few responses last night because firefox stopped working.  I'm almost sure that the message that came up before the computer reset said something about a segmentation fault.  
I'll try the memtest thing after work today and I'll check the RAM.
By the way, now that you mention it, I doubled my RAM over a month ago by adding a new stick.  Everything was working great for the first three or four weeks after, so I didn't think that was likely the culpret. Maybe the new one had a problem afterall.
By the way, this experience actually makes me want to keep linux on the computer.  I really didn't think it'd be this easy to get tech support on free software (well software that came with a $10 magazine).  Thanks a lot; I'll let you know how this works out later today if I get it working enough to open firefox.

---

### Post by Mustard on 2006-04-05
Good luck with working it out.

---

### Post by Zieb on 2006-04-06
Well, I did the memtest thing and didn't see anything telling me I had any errors (but to be honest, I really didn't know what it was saying anyway :) )
Anyway, I took both sticks of Ram out, blew compressed air into the slots, and put them back in.  There weren't any burn marks or anything.  The computer was working again before I did all of this (it has been working off and on since I started having this problem) and after I did this it still didn't show any errors.  I booted it up this morning before work and got 30 minutes out of it where it was working fine before I left the house.  Of course, seeing as how the problem has been coming and going, I really can't tell if it's been fixed or has just entered the "going" phase for awhile.  I'm just going to wait now and see if the problem stays solved or if I get problems again later today.  If I get anymore problems I'll try removing the new Ram stick entirely.

---

### Post by Mustard on 2006-04-06
Intermittent faults are a pain in the butt.

I booted my machine this morning and I get kernel panic first boot, freezing at 'loading modules' on second boot attempt, and then success on third boot.  Some days it works fine, others it doesnt.  I figure that my issue is something to do with the hard drives spinning up/warming up in time.  That's my uneducated guess anyway.

---

### Post by Zieb on 2006-04-06
So far so good-- a whole day of using anything I needed and having a bunch of stuff open at once where nothing bad happened.  It might have been the memory afterall.  Once again, thanks for the help guys.

---

### Post by cx2610 on 2006-04-07
Well, computers can be like that at times. Problems coming and going. ZIEB, I would suggest you try it as it is right now. When the problem arises again, take out the new mem stick and continue with like that. If that doesn't work, put back the new one and take out the old one and try. This way, you can start eliminating problems. If this doesn't work, post here again to let us know what is up.

Reehan

---

