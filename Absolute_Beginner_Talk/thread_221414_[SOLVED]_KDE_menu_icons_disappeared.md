---
title: "[SOLVED] KDE menu icons disappeared"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by wieman01 on 2006-07-23
Hey Guys, 

Silly thing happened... After installing Baghira and customizing my icons some of the icons that are used in menus and have disappeared. What is odd is the fact that only some of them have. So apparenly not all of them have got lost. 

Does anybody know how I'll be able to get them back? I tried changing themes and icon sets, but all in vain. 

Please look at the screenshots so that you know what I am talking about. I am at a loss.

Many thanks in advance!

---

### Post by Jucato on 2006-07-23
I'm not sure about the 2nd screenshot, but in the first screenshot, those menu entries really don't have any icons AFAIK. You didn't really lose anything.

---

### Post by editrix on 2006-07-23
Don't know if this will work for you, but I had something similar happen and fixed it this way:

In .kde/share/config/

There's a file called kdeglobals.

If you look at it in Konq in the Detailed List View, you'll see when it was created, and right below it will be several files that are backups, called kdeglobals[a whole bunch of letters and numbers].new.

Pick the earliest one which will be your settings before you changed things (hopefully). Then, rename kdeglobals to something like kdeglobals.BROKEN and rename the earliest backup to kdeglobals. i.e., 

mv kdeglobalsQ69n7b.new kdeglobals

Log out and back in again.

BTW, I tried mv ~/.kde ~/.kde.old as suggested by someone else, and what came back was nothing like I'd had--even the default apps in the panel.

---

### Post by wieman01 on 2006-07-23
> **Fenyx said:**
> I'm not sure about the 2nd screenshot, but in the first screenshot, those menu entries really don't have any icons AFAIK. You didn't really lose anything.

Mmm... Perhaps this problem relates to my own stupidity. But I saw similar threads on the web that confirm that this has happened before with KDE 3.4 and 3.5. Let's see what other users have experienced.

---

### Post by wieman01 on 2006-07-23
> **editrix said:**
> Don't know if this will work for you, but I had something similar happen and fixed it this way:

In .kde/share/config/

There's a file called kdeglobals.

If you look at it in Konq in the Detailed List View, you'll see when it was created, and right below it will be several files that are backups, called kdeglobals[a whole bunch of letters and numbers].new.

Pick the earliest one which will be your settings before you changed things (hopefully). Then, rename kdeglobals to something like kdeglobals.BROKEN and rename the earliest backup to kdeglobals. i.e., 

mv kdeglobalsQ69n7b.new kdeglobals

Log out and back in again.

Thanks, mate. Sadly there are not backup files of "kdeglobals". Perhaps KDE 3.5 is different from previous versions in this respect. But sounds like something that would have definitely worked.

---

### Post by wieman01 on 2006-07-23
There is another screenshot of my panel (right click). Do these menu items not have icons under normal circumstances?

---

### Post by Jucato on 2006-07-23
On my system, there are also no icons for those. And I don't have Baghira. 

Tell you what I'll do. I'll try running the Kubuntu Desktop/Live CD, take some screenshots of the same stuff you took and let's compare.

Btw, what was that 2nd screenshot? The one with the chat menus?

---

### Post by wieman01 on 2006-07-23
> **Fenyx said:**
> On my system, there are also no icons for those. And I don't have Baghira. 

Tell you what I'll do. I'll try running the Kubuntu Desktop/Live CD, take some screenshots of the same stuff you took and let's compare.

Btw, what was that 2nd screenshot? The one with the chat menus?

Thanks a lot. The second screenshot is Skype. 

Let's see what your desktop says. :-) Maybe it's really as simple as you've said before. Would be funny...

---

### Post by Jucato on 2006-07-23
Sorry I only got up now. Anyway, here are the screenshots. The first two are from the Kubuntu Live CD, the second two are from SimplyMEPIS 6. I didn't include screenies of Skype. :D

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/snapshot1.png[/IMG]

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/snapshot2.png[/IMG]

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/snapshot3.png[/IMG]

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/snapshot4.png[/IMG]

---

### Post by wieman01 on 2006-07-23
Hello Fenyx, 

Just got up a minute ago as well. Same timezone, ey? ;-) 

Thanks for the post, really appreciate it. It seems there is nothing wrong with the system but my concept. Hahaha. Ok, resolved once and forever. Thanks for this one.

He

N.B.: It's odd though that these icons are missing... I was wondering whether I was the first person to ask that kind of question.

---

### Post by Jucato on 2006-07-23
Yeah I just noticed we have the same timezone. GMT/UTC +8 :D

The icons aren't really missing. It's just that there just aren't any icons for those actions at all, at least AFAIK. I guess it's just quite hard to have icons for each and every menu entry. And even most of those that have one are just reused icons or are common icons for other apps.

---

### Post by wieman01 on 2006-07-24
Ok, I don't want to beat a dead horse now, but does anybody know how to disable those icons in the menus, etc.? 

Since I find the annoying anyway I best get rid of them once and forever. Advice is - as always - appreciated.

---

