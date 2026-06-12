---
title: "firefox and gmail"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by Strongbad on 2005-08-12
Hi all, I know this isn't technicly a ubuntu question, but I can't seem to log on to my gmail account with firefox  :???:. whenever I try to log in, it just sits there loading loading loading........ I did one of those firefox speedup tweaks with chromedit not to long ago, Could that be causing the problem?

-Strongbad-

---

### Post by KingBahamut on 2005-08-12
sure why not.....

not to sound like a Lush, but  that could very well be the problem.

---

### Post by Lord Illidan on 2005-08-12
Can you connect with another browser, like Opera? I can use gmail on firefox with no problems, maybe it is the config you made...

---

### Post by aysiu on 2005-08-12
Have you tried temporarily deleting your profile (you can make a backup first, of course), then relaunching Firefox and seeing if you have the same problem?

Just rename /home/username/.mozilla to /home/username/.mozilla_backup and launch Firefox again. Still have that same problem? If not, it's probably either the tweak you did or some weird buggy extension.

---

### Post by xequence on 2005-08-12
That happened to me awhile ago (with windows though). I think I just refreshed and it worked, though I dont remember exactly.

---

### Post by Kyral on 2005-08-12
Sometimes it just doesn't work. Wait a day it should be back :D

---

### Post by wmcbrine on 2005-08-13
Try logging in with the basic HTML interface, rather than the default Javascript:

[https://mail.google.com/mail?ui=html](https://mail.google.com/mail?ui=html)

(If you don't already have a cookie stored, you may have to log in, then connect again, before it will work.)

I had to do that on one system (Windows XP), while it still worked fine on my other two (Ubuntu, Mac), all using the same version of Firefox with the same extensions. It was just something messed up in the profile. I never did figure it out, and eventually I had to wipe that profile for other reasons, after which Gmail worked fine with a new profile on the same system.

Rebuilding your profile can be tedious, so if you have no other problems, I wouldn't necessarily recommend that. But that's probably what you'll have to do eventually.

---

### Post by ad1138 on 2005-08-14
Just a hint: I had this problem the other day, it never happened before. I messed with anything I could think of, then I just tried to disable ablock: gmail worked fine. Of course, I re-enabled it back right after my "gmailing". :)

---

### Post by Strongbad on 2005-08-15
[QUOTE=wmcbrine]Try logging in with the basic HTML interface, rather than the default Javascript:

[https://mail.google.com/mail?ui=html](https://mail.google.com/mail?ui=html)

(If you don't already have a cookie stored, you may have to log in, then connect again, before it will work.)

I had to do that on one system (Windows XP), while it still worked fine on my other two (Ubuntu, Mac), all using the same version of Firefox with the same extensions. It was just something messed up in the profile. I never did figure it out, and eventually I had to wipe that profile for other reasons, after which Gmail worked fine with a new profile on the same system.

Rebuilding your profile can be tedious, so if you have no other problems, I wouldn't necessarily recommend that. But that's probably what you'll have to do eventually.[/QUOTE]

It will work in basic html but that's it. I tryed renaming my profile file, and it still didn't work with a slate clean. It's got me stumped.  :-? 

-Strongbad-

---

### Post by RastaMahata on 2005-08-15
[QUOTE=Strongbad]It will work in basic html but that's it. I tryed renaming my profile file, and it still didn't work with a slate clean. It's got me stumped.  :-? 

-Strongbad-[/QUOTE]
 I have realized that firefox in ubuntu works way better with a new profile.

backup your bookmarks
firefox -ProfileManager
create a new profile
delete the old one
use your new profile form now on
restore bookmarks

---

