---
title: "Firefox broken, help please."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-03-09
Hi

Firefox running fine, just congratulated myself on getting video streaming working yesterday, then...

I received some upgrades about an hour ago and Firefox is misbehaving. On the Samsung.com site the top drop down menus have expanded so that a box appears in the top left corner of the home page (and all other pages) that obliterates most of the page with a white backgound, in which, at the top, the drop down menu boxes sit. The menu boxes function on mouseover. 

I have tried the site with Firefox 2.0.0.2 on XP and the site behaves as normal.

Any clues as to what has happened please?

Regards, Bob

---

### Post by bapoumba on 2007-03-09
Hello, which Fx version are you using ?
could you please run:
```
sudo aptitude update
sudo aptitude upgrade
```
run Fx again and post a screenshot ?

---

### Post by bwallum on 2007-03-09
Updated to Fx using your code (really quick!). Now acutely embarrassed because I do not know how to do a screen save in Ubuntu! Ahem...could you help with this please..

---

### Post by i.am.canadian on 2007-03-09
Hey there.  Just hit your 'print screen' key and it should give you a dialogue.

---

### Post by r4ik on 2007-03-09
> **bwallum said:**
> Updated to Fx using your code (really quick!). Now acutely embarrassed because I do not know how to do a screen save in Ubuntu! Ahem...could you help with this please..


[http://www.ubuntuforums.org/showthread.php?t=350526&highlight=place+screenshot](http://www.ubuntuforums.org/showthread.php?t=350526&highlight=place+screenshot)

Good luck !

---

### Post by bwallum on 2007-03-09
That was a great crack! thanks, be back soon with a screen shot

---

### Post by bwallum on 2007-03-09
Hole in one! Brilliant!

---

### Post by bwallum on 2007-03-09
Here is the screen shot attached (I think)

---

### Post by r4ik on 2007-03-09
Would you be so kind to post a screenshot from,

[http://www.planet.nl/](http://www.planet.nl/)

please ?

---

### Post by bwallum on 2007-03-09
I think it may have something to do with the Flash Player. When I right click on the Samsung white patch it gives a menu referencing Flash. (I can't screen save when this shows). In my system screenshot-2 shows possible confict??

Also attached screenshot-3 as requested.

---

### Post by r4ik on 2007-03-09
I do not think so flash on that site looks perfect.
to be sure ,

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Good luck !

---

### Post by bwallum on 2007-03-09
I meant flash on my system may be at fault. I followed all the instructions and installed Flash 9. Your link has helped a great deal, thanks. Most of the white space is now filled. 

There is still a top banner that appears to be behind the large flash image (if that is the right terminology??)

I am pretty convinced that the problem lies with my system and the way flash is installed.

Is there any way of completely purging flash and reinstalling?

Thanks again for moving me forward, I am over the hill and only wish the zimmer frame would keep up with me!

---

### Post by bwallum on 2007-03-09
...of course the image may help!

---

### Post by r4ik on 2007-03-09
The site looks exactly the same here.
So my guess is you're oke and the site is wrong.

try,

[http://www.jawwi.nl/](http://www.jawwi.nl/)

I think it will be the same story.

---

### Post by bwallum on 2007-03-09
The site looks fine with Firefox 2.0.0.2 running on Windows XP. Screenshot attached. If you have the same problem Ubuntu might have a bug somewhere. What do you think? I have never reported a bug before so a couple of pointers would be useful please (if you agree it could be a general bug).

Thanks a lot for moving me forward, I really appreciate your time and effort. It must get a bit off putting with all these newbies asking darn fool questions! Bet it gives you a few chuckles sometimes though!

---

### Post by bwallum on 2007-03-09
may have run up against file size limits....

---

### Post by bwallum on 2007-03-09
png image (hopefully) with Firefox 2.0.0.2 running on XP

---

### Post by r4ik on 2007-03-09
> **bwallum said:**
> The site looks fine with Firefox 2.0.0.2 running on Windows XP. Screenshot attached. If you have the same problem Ubuntu might have a bug somewhere. What do you think? I have never reported a bug before so a couple of pointers would be useful please (if you agree it could be a general bug).

Thanks a lot for moving me forward, I really appreciate your time and effort. It must get a bit off putting with all these newbies asking darn fool questions! Bet it gives you a few chuckles sometimes though!

I am runnin Debian at the moment so it hard for me to decide if you should fiie a bug or not.
It is up to you.
To answer the second part,
No it does not.  :popcorn:

---

### Post by bapoumba on 2007-03-10
Hello :)
So I've tried the samsung web page with both epiphany (2.16.1) and Firefox (2.0.0.2) and flashplugin-nonfree from edgy repositories.
```
~ $ aptitude show flashplugin-nonfree
Package: flashplugin-nonfree
State: installed
Automatically installed: no
Version: 9.0.21.78.2ubuntu1~edgy1
```
Screenshot attached (epiphany, same exact situation with firefox).
When getting the screenshot from XP, could you please put your mouse over "about Samsung" ?

---

### Post by bwallum on 2007-03-10
Hi and thanks for responding. This problem also sows on FOXNews and is definately something to do with the way Flash is displayed in Linux (possibly Debian). It is broader than just Ubuntu.

Attached screenshot with mouse over 'About ..'. This taken with Firefox 2.0.0.2 on XP.

Thanks again, I was wondering what to do, it is a problem I'm sure.

---

### Post by Zelator on 2007-03-11
I am having similar problems with Samsung registration pages, not just with Firefox 1.5.0.10 but also with Konqueror in Kubuntu 6.06, though the problems are different with each - on the Australian registration page in FF I can't enter data but can drop down list boxes, whereas with Konq I can enter data but the boxes won't drop! On another international page FF shows some of the navigation stuff as empty, and in Konq I get the "big rectangle" blocking out the map. Looks like bad HTML practice on the part of Samsung to me.

Moral - don't buy Samsung.

---

### Post by bwallum on 2007-03-12
The point is, it all works fine with Firefox 2.0.0.2 on Windows XP. It might well be a site that does some quirky MS specific stuff but we should still be able to read it in Ubuntu. Moving Ubuntu on is all about ease of use for users, most do not want to know about technology quirks. This problem clearly lies in the Flash plugin. Quite where I'm not sure.

There are other sites using Flash where similar problems occur using Firefox 2.0.0.2 in Ubuntu but which work perfectly well using Firefox 2.0.0.2 on Windows XP.

I have looked at the bug lists and Flash plugins seem to be a perpetual problem, I guess this is just the latest round.

Kind Regards, Bob

---

### Post by Derspankster on 2007-12-12
A little off topic but I've had so much flash related problems with Firefox the past six months that I've finally pretty much switched to Opera. I experience no flash related issues in Opera on Gutsy. I like the feel of Firefox but it's so buggy in Ubuntu now that I can't tolerate it.

---

