---
title: "Dual boot help"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by jc87 on 2005-09-14
Today i installed windows (on the same hard drive where is unbuntu) , but without delecting the ubuntu partition .

The problem was that it automatically inicializates as windows , without asking me if i want to boot unbuntu or windows.

I delected the NTFS partition , but then dind´t boot at all (and i was forced to delect and reinstall unbuntu):

I would like to know how to make so after windows being installed (being unbuntu already installed first) i could choose between unbuntu and windows.

I heard something about recording grub on a disk as a solution?

I dont even want to install windows , but as a gamer i dont e have another solution :? .

I will apreciate any help you can give me in this area.

---

### Post by aysiu on 2005-09-14
Have you tried [this Google search](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=site%3Aubuntuforums.org+reinstall+grub+howto&btnG=Search)?

---

### Post by adunphy on 2005-09-20
you'll either need to install grub and let it autodetect the windows and linux OS.  or... you could use the NTLDR and create a bootsect.lnx file and modify your C:\boot.ini  to reflect it.

let me know if you need the details

---

### Post by linbetwin on 2005-09-20
If you want an easy solution and if you don't have any important data stored on the Ubuntu partition, you can re-install Ubuntu on the same partition it is now.

As a rule, though, never install Windwoes after a Linux distro! Or else, Bill will shut the gates on the poor wittle penguin.

I hope that helps.

---

