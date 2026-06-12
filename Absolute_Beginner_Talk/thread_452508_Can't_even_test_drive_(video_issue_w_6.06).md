---
title: "Can't even test drive? (video issue w/ 6.06)"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Paul Sherman on 2007-05-23
Hi all;

I've been pretty happy with a fairly old Ubuntu distro on my machine at home.
Last week, I was given a copy of 6.06 to try out.

Today, I decided to try it on my system at work...

It boots fine, but I can't see anything after it does.  The monitor just shows
a video 'out of range', even when I try to use the safe graphical mode.
I actually had to remove power to the workstation to get the system to
restart, the power button didn't work.

1.  Is there a command I can enter at the 'boot' prompt to tell it what video
resolution and frequencies to use?

2.  What keystrokes can I use 'blind' to get out of Ubuntu and reboot the PC?

Please hold all the 'you should download/get' this newer distro comments.  If this
old of a distro is too much for my system, what will a newer one improve?

---

### Post by srt4play on 2007-05-23
At the livecd menu, hit F6.  Append "vga=771" to the end of the boot line.

---

### Post by Paul Sherman on 2007-05-23
Hmmm....

Tried that, didn't work.
(Is the 771 code 800x600 at 256 colors?)

System has Intel 82865G video controller and Viewsonics VG2000 LCD monitor.

Currently capable of up to 32 bit color at 1600X1200 resolution.

Posted refresh raes are 60, 70 and 72 Hz

I have a chart with the 'VGA=' codes on it, maybe I'll try some more of
those.

Is there a way to force refresh and scan rates at boot?

---

### Post by srt4play on 2007-05-23
Since 771 didn't work try 791.

I have no idea what modes they define.  I do however know that I've seen them fix countless problems with the boot splash screen not showing on certain LCDs.

You can blindly reboot the computer by hitting ALT-F1, if you see a command prompt please let us know that here.  If you don't see anything after alt-F1, you can blindly put in your username, enter key, password, enter key.  Then "sudo shutdown -r now" followed by your password and hitting enter .

---

### Post by Paul Sherman on 2007-05-23
Regarding the shutdown command...

Since this is happening in the 'live cd' mode without any user name
or password, I should be able to type in 'shutdown -r' by itself,
correct?

Well, one way to find out...

---

### Post by Paul Sherman on 2007-05-23
> **Paul Sherman said:**
> Regarding the shutdown command...

Since this is happening in the 'live cd' mode without any user name
or password, I should be able to type in 'shutdown -r' by itself,
correct?

Well, one way to find out...

Rats!  None of those suggestions worked...

The displayed refresh rates with the message are 
Horizontal 81.4 KHz and Vertical 65 Hz

The vertical seems to be a rate that the hardware doesn't like
(In XP, only 60, 70 and 72 are listed)

---

