---
title: "Trouble Booting Ubuntu 11.10 with Intel iMac"
date: 2011-11-19
forum: Apple Hardware Users
---

### Post by tellis on 2011-11-19
I originally downloaded and installed 11.04 as the sole OS on my Intel iMac. Everything worked perfectly except for a few things like the iSight camera.

When I upgraded to 11.10, I started getting problems when I tried to boot. I first get to this screen:
[IMG]http://www.trumanellis.com/wp-content/uploads/2011/11/IMG_8120.jpg[/IMG]

If I select the default, after a few seconds it freezes on a blank screen with lines:
[IMG]http://www.trumanellis.com/wp-content/uploads/2011/11/IMG_8121.jpg[/IMG]

If I select Recovery Mode, I get this screen:
[IMG]http://www.trumanellis.com/wp-content/uploads/2011/11/IMG_8122.jpg[/IMG]

But as indicated by the "Read Only", I can't actually navigate within this screen or do anything - it's just frozen here.

The weird thing is that if I hard reset after either the line screen or the recovery screen and again choose the default option, everything loads normally. In fact, it looks like if the computer was recently powered up then powered down and restarted, things work fine. I only seem to get the bug when the computer has been off for an extended period of time. I did NOT get this bug under 11.04.

I figured that maybe something had gone wrong with the upgrade so I tried a clean install with the 64-bit version from [http://releases.ubuntu.com/11.10/]("http://releases.ubuntu.com/11.10/"), but that didn't change anything. I also tried installing the standard Ubuntu CD, but that wouldn't even install.

So I figured I should follow some of the Mactel guides and reinstall OSX then do a dual boot scheme with rEFIt. That is the configuration I am currently running, but I am getting the identical bug.

Considering that this was working under 11.04, it seems like the bug has to have been introduced with some package that was new to 11.10.

Any ideas?

---

