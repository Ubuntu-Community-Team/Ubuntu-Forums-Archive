---
title: "Big Fonts on Gutsy"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-10-23
Hi All

I just did a clean install on two laptops to Xubuntu Gutsy. It seems I'm having the same issues as this bug report:
[https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745](https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745)

On my computer running Nvidia the fonts are way too small but I'm living with it because I like to fit as much on the screen as possible.

I just used the exact same alternate cd to install the same os on my girlfriends laptop and the fonts are way too big. When I type in the user name one letter takes up the entire line and you can only see part of the letter. Then when I do log in the entire screen is taken up with the panels.

Does anyone have a solution for this, keeping in mind that the fonts are so big I can't navigate around to modify files?

Help is greatly appreciated,

---

### Post by High Camp on 2007-10-23
Anyone have any thoughts on this? My girlfriends computer is essentially useless with Gutsy on it.
I tried the solutions found here:
[http://ubuntuforums.org/showthread.php?t=235214&highlight=dpi](http://ubuntuforums.org/showthread.php?t=235214&highlight=dpi)
and here:
[http://ubuntuforums.org/showthread.php?p=3609621](http://ubuntuforums.org/showthread.php?p=3609621)
with no luck.

I have also read the entire bug report (link in first post) and have not found a solution.

Thanks,

---

### Post by keith11 on 2007-10-24
I haven't read through the links you provided but have you tried changing the fonts to 96 dpi? It changes everything completely, to a mush nicer look. You can use either 96 dpi or 120 dpi from the advanced settings for the fonts (I don't remember the exact settings and I am in Vista right now, so I can browse to the exact setting but you should be able to find it). Hope this helps.

Keith.

---

### Post by High Camp on 2007-10-24
Hi Keith

Thanks for the reply. I can't change the DPI directly because the fonts are so big I can't navigate around the computer. The two links I posted suggested changing things in xorg.conf and gdm.conf. I tried both of those together and seperately (logged in via Live CD) and that didn't work. I thought maybe the Xubuntu download hadn't been updated with the latest and greatest so I downloaded a fresh Ubuntu Alternate CD and still no go. 

I guess what I'm looking for is:
1. Confirmation that this is a DPI issue.
2. A reliable way to change the DPI.

Thanks much,

P.S. Vista???

---

### Post by keith11 on 2007-10-25
I am sorry I couldn't be of much help. I don't understand either what could be the problem then if you can't even navigate properly. Have you tried looking through the launchpad bugs? Hope you find the solution soon.

Keith.

---

### Post by High Camp on 2007-10-27
Hi Keith

I have found this bug:
[https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745](https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745). 

So I think I can fix the problem if I can go in and change the DPI assuming that's the problem. I need to know were to edit it though. What I will have to do is install the program and then boot the livecd again and edit from there or boot in command line but that just frustrates me. I tried editing it in the two places the posters in the bug report say (can't remember were at this time) and that didn't fix the issue. The only other thing I can think of is the wrong driver (it has an ATI card) so I would also like to know how to check what packages are installed from the livecd or for that one I might have to boot to the command line.

Thanks for trying,

P.S. I know it's not called the command line (that's a M$ term) but old habits die hard and at least I'm not calling it Dos prompt.

---

