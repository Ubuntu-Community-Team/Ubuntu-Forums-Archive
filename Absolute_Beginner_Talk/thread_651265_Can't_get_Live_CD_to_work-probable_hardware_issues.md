---
title: "Can't get Live CD to work-probable hardware issues"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by despidey on 2007-12-27
I have successfully installed Ubuntu on 3 older computers already, but they are at my office.  Now I want to set up a dual boot for my Vista (UGH!) home computer to play with the different distros of Ubuntu until I decide which one is for me so I can blow away all traces of windows. I know the install disc works because I've already successfully used it.  I see from perusing the forums that I cleverly own a machine that is going to have issues: ATI graphics, wireless USB keyboard/mouse and don't have a clue about what to do to get the Live Disc to work.  

Dell XPS 410
Core 2 Duo 2.1 Ghz
2 Gb RAM
ATI Radeon X1300 Pro 
Logitech MX 3200 cordless keyboard and laser mouse
Viewsonic VG700b Monitor

When I start up the computer, it boots from the live disc and I get the opening screen.  At that point, the keyboard doesn't work so I just let it time thru until the install starts.  
Then my monitor goes black and says: "out of range" but eventually starts working again
Then it starts running the scripts and hangs up at the place it says "running local boot scripts"

Sure would like to get things running.  Thanks

---

### Post by spiderbatdad on 2007-12-27
have you looked into boot options on the grub screen? F1 you could try f6 then delete rw quiet splash --  and input noapic nolapic    but those options may not be correct for this machine. you can try other options found in F1 F6

---

### Post by despidey on 2007-12-27
> **spiderbatdad said:**
> have you looked into boot options on the grub screen? F1 you could try f6 then delete rw quiet splash --  and input noapic nolapic    but those options may not be correct for this machine. you can try other options found in F1 F6

What's a grub screen?  Is it something I can get to before the live disc starts to load?

---

### Post by LowSky on 2007-12-27
nevermind grub suff, thats for installed ubuntu... Is the disc a 64bit version, its a known issue. the 32bit doent have that problem. dont worry about that

check your bios to make sure you have enabled usb for keyboard control, if that doesn't work  you may need a wired keyboard for install (pick one up on newegg.com for under $10), but i pretty sure my logitch keyboard worked during the install.

---

### Post by despidey on 2007-12-27
Thanks LowSky.  I'll check the bios first and if it doesn't work, I'll grab one of the extra wired keyboards I have lying around.  I'll report back

---

### Post by despidey on 2007-12-27
> **LowSky said:**
> nevermind grub suff, thats for installed ubuntu... Is the disc a 64bit version, its a known issue. the 32bit doent have that problem. dont worry about that

check your bios to make sure you have enabled usb for keyboard control, if that doesn't work  you may need a wired keyboard for install (pick one up on newegg.com for under $10), but i pretty sure my logitch keyboard worked during the install.

Checked the BIOS and installed a wired keyboard and mouse.  That took care of the keyboard not working problem but I still get the same hang up in what I assume is the GRUB screen.  So I grabbed a different cd to see if maybe something had happened since my last install, but the same thing happened except I got a new message that said: "Display server has been shut down about 6 times in the last 90 seconds.  _Something bad is going on_."  Now, how can you not love linux - if this error came up in MS Whatever it would be some cryptic thing referring to some knowledge base crappola but in reality still means "Something bad is going on."  :lolflag:

Having moved beyond my amusement and delight back to puzzlement, I'm guessing that there is a problem with my display (drivers) that linux doesn't like.  In addition to the ATI card, I also have a Happaugue 1600 TV card intalled - don't know if that matters It probably would be easier to deal with if I actually had Ubuntu running, but I'm still mired in Windows.  Is there some work around to do get the install to work?

---

### Post by azimuth on 2008-01-01
The liveCD will load it's own generic driver (similar to what runs your bios splash screen). Most likely it doesn't understand your monitors specs and is setting to an unusable refresh rate. You might try another monitor just to get it to boot.

Also: my wireless Logitech mouse's xcver  works dandy in the ps/2 mouse port with a usb to ps/2 adaptor.

---

