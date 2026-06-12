---
title: "Why is Ubuntu changing my motherboard BIOS time??"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Lvcoyote on 2007-12-07
I set the time in BIOS and boot to Ubuntu, within Ubuntu I set the time using internet synchronization, and have UTC off.  When I reboot the system and enter BIOS somehow the bios time has been moved forward exactly 8 hours.  It does this with UTC on or off, I'm really confused why, or even how Ubuntu can change a BIOS setting.....

Any help or resolution??

---

### Post by PmDematagoda on 2007-12-07
Did you make sure that the proper time zone is selected?

And the issue could be something with the NTP server itself since I had this problem myself even though everything was allright, so the problem was fixed by choosing another NTP server.

---

### Post by Lvcoyote on 2007-12-07
> **PmDematagoda said:**
> Did you make sure that the proper time zone is selected?

And the issue could be something with the NTP server itself since I had this problem myself even though everything was allright, so the problem was fixed by choosing another NTP server.

Somehow my time zone got changed to some place in Africa.....LOL.  All seems to be good now.....
thanks!

---

### Post by Lvcoyote on 2007-12-07
Well, I guess I spoke too soon, its still resetting the time in my motherboard BIOS to 8 hours ahead of local time, with UTC on or off, it doesnt matter.  Time zone is set correctly...... this is driving me mad!!!!!!!!!

---

### Post by Bigbird999 on 2007-12-07
In the adjust time and date, are you set on manual or "keep synchronized with internet servers?  Try manual and then hit the sychronize now button and then leave it on manual.  That's what I had to do to get it to stop fighting with windoze on my dual boot laptop.  

YMMV

BB

---

### Post by Lvcoyote on 2007-12-07
Its the manual setting that gets it all screwed up.  I'm still messing with it, but it appears the only way it will not change the BIOS clock is if I have it set to "keep sync with internet servers, and have UTC on.  I had the time right, then changed to manual and hit sync now, and it instantly went to the wrong time again and changed the BIOS clock......

I now have it set to internet time with UTC on, let me reboot and see what happens.....

---

### Post by Lvcoyote on 2007-12-07
Ok, that works in my case.  The only way it appears to work correctly is with internet syncro and UTC on.  With these settings I do not get a BIOS change in time.  IT still baffles me how Ubuntu can change the clock setting in BIOS though...... a little invasive dont you think???....... LOL

---

### Post by Bigbird999 on 2007-12-07
It is the same in windows or Mac.  The clock displays the time that is set in the bios.  When you adjust the clock, it changes the bios clock and the bios "remembers" what it is set at even when powered off.  This keeps you from having to go into the BIOS to adjust the time.  Mac's don't have a BIOS persay, but they have a system clock that is displayed and can be adjusted from inside the OS.

BB

---

### Post by Lvcoyote on 2007-12-08
> **Bigbird999 said:**
> It is the same in windows or Mac.  The clock displays the time that is set in the bios.  When you adjust the clock, it changes the bios clock and the bios "remembers" what it is set at even when powered off.  This keeps you from having to go into the BIOS to adjust the time.  Mac's don't have a BIOS persay, but they have a system clock that is displayed and can be adjusted from inside the OS.

BB

Well, this issue is still not resolved.  Just when I think I have it working it keeps changing the BIOS time to 8 hours ahead.  Whats weird is that Ubuntu will show the correct time even though the BIOS time has been changed to 8 hours ahead.  This is a real issue when your using a machine to run Windows and Ubuntu.  I'm at my wits end with this problem, you would think something like system time wouldn't be so damn difficult.

I don't know if this is a bug in Ubuntu or what because several other Distro's I've tried never presented me with this issue.  If anyone has any ideas please let me know, I just cant have Ubuntu changing the BIOS time every time the computer is booted up.  I am loving Ubuntu other than this problem, but unfortunately if I can not get it resolved I'm going to have to use a different Distro, and that would suck.....LOL

---

### Post by NilsE on 2007-12-08
If turning off UTC does not work in the clock applet try to change it manually.

In a terminal:

gksudo gedit /etc/default/rcS

Look for  this line:  UTC=yes

Change it to: UTC=no

And save it: 

Then set the time if it is wrong in System/Administration/Time and Date 

Then either reboot or do this in a terminal: 

sudo /etc/init.d/hwclock.sh restart

---

### Post by Lvcoyote on 2007-12-08
Ahh, you beat me to the answer.  I did a little more searching and found the following:

> [b]So after my installation was completed, I had a system with UTC=yes in /etc/default/rcS.

In a dual-boot Windows-Ubuntu computer for the time to properly works in all the OSes an user must set UTC=no.[/b]

So I did just that and it appears to be working , lets cross our fingers....

---

### Post by Lvcoyote on 2007-12-08
Now, just to further my education..... why would they set that default to yes??  For the vast majority of users I would think it should be turned off by default.... or am I missing something here??

---

### Post by NilsE on 2007-12-09
> **Lvcoyote said:**
> Now, just to further my education..... why would they set that default to yes??  For the vast majority of users I would think it should be turned off by default.... or am I missing something here??
I don't know the answer for sure but from something I read elsewhere the default is supposed to be "no" in both the time GUI and of course the file.  However, if you select a European time zone by accident or for that matter intentionally it sets it to yes in the file but is not always picked up  in the GUI.  I think there is a bug open on this but have not looked recently.

One thing I noticed for sure is if you select US English and don't touch the timezone on install it seems to be right.

---

### Post by geekygreen on 2008-02-18
> **NilsE said:**
> If turning off UTC does not work in the clock applet try to change it manually.

In a terminal:

gksudo gedit /etc/default/rcS

Look for  this line:  UTC=yes

Change it to: UTC=no

And save it: 

Then set the time if it is wrong in System/Administration/Time and Date 

Then either reboot or do this in a terminal: 

sudo /etc/init.d/hwclock.sh restart


I would add my thanks for this post, but cant seem to find the right button!  Fixed me right up!

---

