---
title: "Trouble with circles theme on startup"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by Stone_Wolf on 2005-12-09
Hiyas

I do believe i've encountered my first real problem in Ubuntu. I was following a thread here a few moments ago on how to change your themes, icons and login screens. I was working well, until i started removing things. Yep, i do believe it's a serious case of PEBKAC.  I removed some of the standard themes under the "Themed Greeting" tab, but not the circles theme so i don't know what's happening here.

Here's the error i'm getting on startup, just before the logon screen would show.

"There was an error loading the theme circles"
Can't open the file /usr/share/gdm/themes/circles/circles.xml

Click ok and i get this.

There was an error loading the theme, and the default theme could not be loaded. Attempting to start the standard greeter.

That opens, but no matter what option i choose, nothing happens.

How can i fix this without losing anything i've done so far? Any help would be appreciated.

Regards
SW

---

### Post by Stone_Wolf on 2005-12-09
Hiyas

I sorted it out. O.o Rather unconventionally though. I booted up into the rescue mode and managed to copy another theme into the circles folder, obviously renaming the appropriate ".xml" to "circles.xml". I left everything else as is. Now i have my nice new snazzy boot up screen also ;) Hope this helps someone else too.

Regards
SW

---

