---
title: "Moving Firefox bookmarks and toolbar from windows to ubuntu"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2006-01-03
i just installed ubuntu on my system and i was wondering if there was a way i could get my substansial collection of bookmarks from windows into ubuntu, all my bookmarks are in firefox

---

### Post by linear on 2006-01-03
AFAIK, Firefox keeps your bookmarks in a "bookmarks.html" document in your profile, so you should be able to just copy it over.

---

### Post by jimrz on 2006-01-03
Yes, you can. In win go to ff > bookmarks > manage bookmarks > file > export. I sent mine to a FAT32 partition that I use from both Ubuntu and xp, so not sure will work from ntfs but think it should if you have that drive mounted properly. Then fo to ubuntu and use the same proceedure except choose import where you had export on the dark side.

---

### Post by Chipmunk on 2006-01-03
Yes, that's what I did. In windows, the bookmarks.html is in
Documents and Settings\[WindowsUserName]\Application Data\Mozilla\Firefox\[profile name]\bookmarks.html
In Ubuntu it will be in 
~/.mozilla/firefox/[profile name]/bookmarks.html (being a 'dot file', .mozilla is hidden by default in your home directory, you can cd to it in a terminal, or show hidden files in nautilus with ctrl+H (your choice)
Simply copy the one from windows to the correct folder in Ubuntu and restart any firefox sessions you have open.

Note: Profile Name will be something random, fdj8fl5x.default for example. There's usually only one of them unless you chose to have separate profiles for firefox.

Edit: Ignore that, jimrz's answer is a far easier way. :)

---

### Post by Griff on 2006-01-03
[QUOTE=linear]AFAIK, Firefox keeps your bookmarks in a "bookmarks.html" document in your profile, so you should be able to just copy it over.[/QUOTE]
Oh.  My.  God.  I spent probably half an hour copying and pasting 100+ bookmarks into a notepad that I then transfered to the shared partition.:???:

---

### Post by AmboyGuy on 2006-01-03
When I moved mine I exported them (as jimrz recommends) to a floppy, the bookmarks.html file was only 192KB. A really large one could be compressed with zip in windows and unzipped in Ubuntu. It's always nice to have a copy of your bookmarks in case of an error that erases them. ( At one time this was a BIG problem with firefox )

As far as your toolbar or extensions go you'll have to customize the toolbar again and load all your extensions unless you have local copies of them. (MR Techs Local install extension allows you to automatically keep copies of your extensions & themes on your hard disk at the same time you install them from the extension source)

---

### Post by Omnios on 2006-01-03
When I moved mine I put them in my Yahoo bookmarks on the web and then imported them to firefox

---

