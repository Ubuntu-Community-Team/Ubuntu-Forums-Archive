---
title: "Wine and I"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by protokaiser on 2007-08-17
Alright I'm fairly new to Linux and I have xubuntu installed on my laptop. I tried getting some programs on using Wine: Reflections (a program for work), utorrent, and internet explorer.
Reflections just doesn't work, I discovered bit torrent alternatives, and have no clue what's wrong with IE. Thus I just want them gone.

I run the Wine uninstaller and the only program that it shows for me to uninstall is IE. When I choose to uninstall it, it only gives me the option to repair it. So what am I doing wrong, and how can I get rid of these programs?

---

### Post by diatribe on 2007-08-17
I believe that the command to uninstall wne programs is uninstaller, alternatively you can go to ~/.wine ; this is where any wine programs will be located

---

### Post by matthew.lns1 on 2007-08-17
Go to your home folder. Press Ctrl + h so you can see hidden directories. Find .wine. Click on .wine and then find and click on program files. Then delete IE. If you need IE you could also try IE4Linux at this link:[http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by protokaiser on 2007-08-17
I went into the /.wine directory and deleted the programs, but when I got into the applications menu, there's still a section that says "Other" and has links to the programs there. Is there a way to get rid of this?

---

### Post by matthew.lns1 on 2007-08-18
Go to System>Preferences>Main Menu. I warn you, this program is tricky so you have to be patient with it! You should see the "other" menu on the sidebar click on it. Then in the box that takes up most of the window you will see the icons you want. Click on them to disable them. WARING: There will be a slight time delay between when you click the icon and when it gets unchecked.

---

