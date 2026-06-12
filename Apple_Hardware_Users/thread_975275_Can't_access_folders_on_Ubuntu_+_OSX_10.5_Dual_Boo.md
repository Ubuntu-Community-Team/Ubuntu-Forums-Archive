---
title: "Can't access folders on Ubuntu + OSX 10.5 Dual Boot"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by jbiggs12 on 2008-11-08
I have a Penryn MacBook Pro Dual-Booting OSX 10.5 and Ubuntu Intrepid. When I try to access my Macintosh HD volume, I can see all of the folders, but when I go into my user folder, my music, movies, documents, etc. folders all have a little "x" icon at the top, and when I try to access them it says I don't have permission to access the folder. I've changed the permissions in "everyone" to "read only", as I don't want people hacking my network and deleting my music, and booted back into ubuntu, but I still can't access the folders. Can anyone tell me what is going on?

---

### Post by Rutiio464 on 2008-11-08
self-trust is the first secret of success.Come and buy [age of conan gold](http://www.aocgoldweb.com), AoC Gold, AoC Power Leveling and AoC Accounts here, [aoc gold](http://www.aocgoldweb.com) the easiest and safest way to enjoy a wonderful Age of Conan life! [aoc power leveling](http://www.aocgoldweb.com/the-age-of-conan-power-leveling-aoc.asp),  [aoc power leveling](http://www.aocpowerleveling-gold.com), [age of conan power leveling](http://www.aocpowerleveling-gold.com/the-age-of-conan-power-leveling-aoc.asp)..

---

### Post by davertron on 2008-11-24
I'm having the exact same issue.  Most folders I can view no problem, but some seem to be off limits.  For example, I can get to my home directory on the hfs partition just fine, but I can't even ls the Downloads directory there.  I'm sure I'm just missing something simple here, anyone care to point out what?

Thanks in advance.

---

### Post by _mario_ on 2008-11-25
> **davertron said:**
> I'm having the exact same issue.  Most folders I can view no problem, but some seem to be off limits.  For example, I can get to my home directory on the hfs partition just fine, but I can't even ls the Downloads directory there.  I'm sure I'm just missing something simple here, anyone care to point out what?

Thanks in advance.

a short introduction to filesystem permissions is [here]("http://ubuntuforums.org/showthread.php?t=898132"). the bottom line is: you'll have to make your files accessible to 'others' (in contrast to user and group) in OSX. if you don't like that for everyday work, you'll have to use a dedicated shared data partition (not HFS+). there are threads ([1, [URL="http://ubuntuforums.org/showthread.php?t=970572&highlight=shared+partition"]2]("http://ubuntuforums.org/showthread.php?t=976751&highlight=shared+partition")[/URL]) out there talking about that.

ciao,
Mario

---

### Post by davertron on 2008-11-25
Ah, of course.  Makes sense.  Thanks Mario, I'll give that a shot.  Probably using a dedicated data partition would make life easier here.  However, in this case the data isn't sensitive, and even if it were this is my laptop, not a multi-user system, so it wouldn't matter anyway :)

Cheers :popcorn:

---

### Post by baycoo01 on 2008-11-26
Charge stun. This 1-second stun has been one of the most annoying mechanics in a warrior's arsenal to date.we provide wow gold,cheap wow gold,warcraft gold. Charge is almost mandatory for entering combat effectively and forcing yourself to begin your stun DR (which resets after 20 seconds) with a 1 second stun just so you can get in melee range and generate a little bit of rage off of it seems very counter-productive, especially with a Protection-oriented build with 2 other controlled stuns (concussion blow and shockwave) and for any warrior in general as it shares DR with intercept stun. we provide wow gold,cheap wow gold,warcraft gold.Would it be possible to change Charge into a 1-second immobilize and 2-second interrupt? This would effectively yield the same results even for snare-immune targets (via hand of freedom) but would not annoyingly start your stun DR worthlessly. [wow gold](http://www.baycoo.com)[wow power leveling](http://www.baycoo.com/powerleveling-wow.asp)[wow power leveling 80](http://www.baycoo.com/powerlevelingreport.asp)[wow gold paypal](http://www.baycoo.com/wow_gold_paypal.html)[wow gold reviews](http://www.baycoo.com/wow_gold_paypal.html)

---

