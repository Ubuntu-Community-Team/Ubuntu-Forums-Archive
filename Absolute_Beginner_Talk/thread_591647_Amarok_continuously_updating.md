---
title: "Amarok continuously updating"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-10-25
[FONT="Comic Sans MS"]Hi, a small problem. Amarok updates the collection every few seconds. No real bother except it uses a fair bit of cpu doing it. I've searched and haven't seen anything related to this but maybe my search terms are crap. I can't see an option in amarok related to this.
Any ideas?[/FONT]

---

### Post by FighterOfTheNightMan on 2007-10-26
Try changing Applications<Add/Remove Software<Preferences<Updates to weekly instead of daily.  I tried some googling myself and didn't find anything.  Never heard of this before.

Regards,

Brandon

---

### Post by forestpixie on 2007-10-26
have you tried turning the watch folders off then deleting the collection.db from the hidden folder and restarting the watch folder option.

There are a couple of threads in the amarok forum which might help also - don't know if you've seen them

[http://amarok.kde.org/forum/index.php/topic,14208.0.html](http://amarok.kde.org/forum/index.php/topic,14208.0.html)

[http://amarok.kde.org/forum/index.php/topic,13693.0.html](http://amarok.kde.org/forum/index.php/topic,13693.0.html)

Edit - folder is here if you don't already know - /home/*user*/.kde/share/apps/amarok

---

### Post by carloslosgrande on 2007-10-26
[FONT="Comic Sans MS"]Forestpixie,[COLOR="DarkOrchid"] thanks [/COLOR]for 1; the edit as I didn't know where those files were
2; the links to amarok forum
3; a solution.
Ok, I tried as you suggested and deleted collection.db after turning off watch folders.
Also tried deleting collection-scan files as suggested in the amarok links.
Turned watch folders back on and same old same old.
Anyway I can just leave those scan/update options off and turn them on when I want/need.
Not the most elegant solution, but then nor am I.[/FONT]:)

---

### Post by funky_beak on 2008-01-08
I am finding the exact same thing !!! how annoying it is cos it really slugs amarok, havnt looked into it yet but from post above dosnt seem promising

---

### Post by carloslosgrande on 2008-01-09
[FONT="Comic Sans MS"][I]Since then I've done a complete reinstall and the problem went away.........for now.
Perhaps the next version will fix it.[/I][/FONT]

---

### Post by hyper_ch on 2008-01-09
furthermore you could use mysql instead of sqlite for your collection. that might speed up things also.

---

### Post by karhulitos on 2008-01-27
I had this same problem some months ago, but cannot remember what was the solution. My Amarok no longer does those scans all the time.

Now, I am in the same laptop but with my wife's credentials and I noticed Amarok doing the same.
While looking up the possible solution I hit the last option of Amarok's Tools menu. The second last is update collection but the last one is something like "survey collection" (sorry my Amarok talks finnish, direct translation).

Now it hasn't done a single update in 15mins. Let's see..

---

