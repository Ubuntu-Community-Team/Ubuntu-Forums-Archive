---
title: "Media file associations on files on a shared drive"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Shakey_Jake33 on 2008-01-01
Basically, I have my media (which includes everything from .avi to .ts to .vob) on my Vista machine, with the directories shared, and my Ubuntu machine can access it fine.  However, I cannot change the default application which these files open with.  I want them to open with smplayer, but they open with the default Totem application.

Local files are fine, it's just the files on my Vista machine.

I am quite new to this, really looking to make the transition from Windows to Linux, so I'd like to get the basic stuff like this nailed!

Thanks

---

### Post by empthollow on 2008-01-01
file associations in gnome are easy.  not sure why it's only happening on shared files but sometimes it treats network files differently.  here's how to do it. 

right click on the file and choose properties.  Click on the 'open with' tab and select the radio button with the program of your choice.  you may have to do this for example with both .mpg and .mpeg files as they are considered a different extension. hope this helps.

---

### Post by Shakey_Jake33 on 2008-01-01
Thanks, that works a treat on local files, but a no-go for files on the Vista machine.

I did a quick search on the forums and found I'm not the only one who has the problem ( [http://ubuntuforums.org/showpost.php?p=2303456&postcount=5](http://ubuntuforums.org/showpost.php?p=2303456&postcount=5) ).

It's possible it could be a problem on the Vista end, but I'm really not sure where to start tbh.

---

### Post by empthollow on 2008-01-01
well, my best guess is that it's a problem with how linux is seeing the windows files. samba is the program linux uses to read those so it could be that gnome doesn't know how to associate anything because of how the mimetypes are translated.  i could be way off here but that's my best guess.  I've never knowingly had that problem.  i share all stuff with my linux box and look at it with windows.

---

