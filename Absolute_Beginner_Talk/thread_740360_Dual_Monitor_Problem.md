---
title: "Dual Monitor Problem"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by lifeinoleg on 2008-03-30
I know this is generally frowned upon, but I'm reposting this thread. The first iteration of it was [here]("http://ubuntuforums.org/showthread.php?t=737837"). But I didn't get any help in Multimedia and Video; my upping was to no avail. Perhaps there are more eyes in this part of the forum. To save time, here is a copy of the post:
-----------------------------------------

Hi, just recently bought a new monitor(LG L226WTQ-BF) to use with my Dell Inspiron 6400/E1505 laptop. After some twiddling around with "Screens and Graphics" I got the resolutions set correctly which took care of the pixelated-mouse problem that initially affected my second monitor.

Currently, everything seems to be working okay except that the cursor doesn't change on my second monitor. On the laptop the pointer changes when I want to resize a window, when I hover over a link, when I'm in a text-area etc. None of that happens on the new monitor, it simply remains a pointer. Actually, when I try to resize windows it skips over the area where it would usually become the sizing graphic.

fyi: I'm using Gutsy Gibbon 7.10, the laptop has a ATI Radeon Mobility X1400 (I've looked a the documentation re: Binary Driver found in other posts, and my fglrx is enabled.). The second monitor is connected straight to the laptop using a VGA cable. Would be glad to post any other information that's necessary.

Thanks in advance for the help.

---
cooldude replied: "Was it a large square looking cursor on the second monitor??"

---
I replied:

 "Sorry, I wasn't being clear in my post. By "pixelated-mouse" problem I meant the the large square thing.

After I got my resolutions all figured out, that problem was replaced by the issue described in my post; the cursor is a regular pointer, but it doesn't change, it stays a pointer all the time. (really annoying when doing programming, word processing, internet browsing since it doesn't change to the hand to show me when something's a link, or to the serif "I" to show me I'm in a text area..."


---

If this act of reposting is too egregious, than this thread should get deleted, and I'll just keep upping the original thread. Just hoping I can get this problem figured out.

Thanks.

---

### Post by smurphy_it on 2008-03-30
Could you attach a screenshot so we can see what it is you are talking about ?

---

### Post by lifeinoleg on 2008-03-30
I'm having trouble creating a screenshot from the second monitor. When I press Print Screen, the program pops up, but it only take a shot of the laptop screen. How can I make it capture the second screen? (the cursor changes normally on the laptop screen)

(perhaps I can give describing it another try: imagine moving your pointer over a link, the little hand appears, that doesn't happen on my second screen. The regular pointer stays as it was. Same with any place the pointer is supposed to change, it just doesn't. It does function correctly i.e. I can still click on the links. Just graphically it doesn't change.)

---

### Post by smurphy_it on 2008-03-31
You could try backing up your xorg.conf file and then upgrading to the latest ATI video driver.

---

### Post by J1m on 2008-03-31
Hi there,

You might try downloading and installing Envy for Ubuntu.  It automates the installation of ATI's propriatary graphics drivers.  I use it for my nVidia card - I use dual monitors and I've never had a problem.

All credit to Alberto Milone for writing an awsome application:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Hope this helps,

---

### Post by lifeinoleg on 2008-03-31
Hi, thanks for the replies.

I used Envy to update my ATI driver and this solved the pointer problem, so thank you for that.

However, it changed something in the configuration of the second monitor, so now it's back to twiddling around in "Screens and Graphics" for me. So far, I've been unsuccessful (i.e. having to scroll around the screen on the laptop and having a line of the screen black on the 2nd screen.) 

Is it me, or is the Screens and Graphics somewhat buggy. Is there any spiffy program to replace it? Which makes it easier to configure resolutions?

---

