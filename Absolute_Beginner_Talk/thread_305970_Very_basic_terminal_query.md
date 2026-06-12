---
title: "Very basic terminal query"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by NotoriousTF on 2006-11-24
Hey all!

Just looking for some basic help with a simple terminal command. When trying to access folders via terminal using the 'cd' command, any folder which is named with more than one word won't open. For example the folder 'College' will open with the command "cd College", but the folder 'My Pictures' will not open with the command "cd My Pictures". It claims that theres no such command or directory. I'm extremly confused here?!

Oh I should also point out that I'm a completely new to linux, and have been on Windows for the last 12 or so years!

---

### Post by jrings on 2006-11-24
Either put " " around the folder name, or you can use "\ " to write a whitespace.
So either type cd "My Pictures" or cd My\ Pictures.

---

### Post by bodhi.zazen on 2006-11-24
> **NotoriousTF said:**
> Hey all!

Just looking for some basic help with a simple terminal command. When trying to access folders via terminal using the 'cd' command, any folder which is named with more than one word won't open. For example the folder 'College' will open with the command "cd College", but the folder 'My Pictures' will not open with the command "cd My Pictures". It claims that theres no such command or directory. I'm extremly confused here?!

Oh I should also point out that I'm a completely new to linux, and have been on Windows for the last 12 or so years!

3 options:[list=number][*]Use tab completion. cd My<tab> will give cd My\ Pictures.[*]Use a \ to "escape" the white space. cp my\ Pictures.[*]Use quotes cd "My Pictures"[*]Change the name. Either just Pictures, MyPictures, or My_Pictures[/list]There that was 4 ! :lol:

---

### Post by NotoriousTF on 2006-11-24
Thanks a lot for the help and the speedy replies!

---

