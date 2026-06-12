---
title: "Installing Fresh Opera-static"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-06
I recently installed Opera. Been learning and tweaking no end, and rather dug me a hole whilst messing withfonts. I couldn't see a way to 'reset' and go to the default and i didn't know how to undo my mess. The consequence was a lot of dragging and blurryiness when scrolling. I know i only have 256 ram but that isn't it.

To the point:
having istalled it using sudo dpkg -i     , i uninstalled it with sudo dpkg -r   with the intention of starting from scratch. However, when i reinstalled Opera it came back with all bookmarks and previous (messed-up) settings!

i did man dpkg and saw that i could do a deeper cleanse by dpkg --purge

So, i purged Opera seemingly from my system but when i reinstalled, with some confidence, i may add, of a fresh install, i was even more dismayed to find Opera start up with all its previous settings yet again  ](*,) 

So, the question is, at last, why, and more importantly HoW do i actually 'purge' as it were Opera completely so that i can effectively have my fresh install with no previous settings configured?

Is it stored in the cache ? 

i'm totally befuddled, which isn't hard of course, so if it is easy for someone to help me out here, i'd be very much obliged once again 

--

sophtpaw

---

### Post by lol on 2005-09-06
Opera, like all other applications, stores the user settings in your home directory. If you want to start again from scratch, you don't need to uninstall/reinstall the whole application, you just need to delete those settings. For Opera, they are stored in the .opera folder.

So, all you have to do is:
'\rm -r .opera' from your home directory, and start opera again...

---

### Post by sophtpaw on 2005-09-06
[QUOTE=lol]Opera, like all other applications, stores the user settings in your home directory. If you want to start again from scratch, you don't need to uninstall/reinstall the whole application, you just need to delete those settings. For Opera, they are stored in the .opera folder.

So, all you have to do is:
'\rm -r .opera' from your home directory, and start opera again...[/QUOTE]


Ahhh..

thank you Lol

 O:) 

--
sophtpaw

---

