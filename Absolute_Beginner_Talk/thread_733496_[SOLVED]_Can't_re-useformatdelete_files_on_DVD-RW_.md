---
title: "[SOLVED] Can't re-use/format/delete files on DVD-RW in Gutsy"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Mylorharbour on 2008-03-23
I backed up a dvd to a DVD-RW and now wish to delete the files so I can re-use it. I can't move the files to the trash, I just get a 'Delete immediately' dialog which asks me if I want to delete them, so I click on Delete and I get 'Unable to move to Deleted Items folder: Read only file system'. So after hunting round on here I came across several threads saying I needed to change permissions using Nautilus so I went to the terminal and typed 'gksudo nautilus', clicked on Computer in the window, browsed to the DVD, went to Properties, Permissions and tried to change from 'read only' to 'read and write' That gives another error message 'The permissions could not be changed.- Sorry, couldn't change the permissions of "CD-RW/DVD±RW Drive: <Title>"'

Where do I go from here?

I quite like Ubuntu and would like to recommend it to friends and family but I cant............ It does complex stuff quite well but it does appear the developers haven't put much time into something as simple as deleting files or making it genuinely simple to install or making it play mp3's or dvd's out of the box.

---

### Post by Nano Geek on 2008-03-23
Have you tried one of the dedicated CD/DVD burning programs available?
I can't think of any specific name at the moment, but you should check in **Add/Remove...** there are several that can wipe DVD-RWs.

---

### Post by smartboyathome on 2008-03-23
Some apps to try are K3B and Brasero. Both are exellent at what they do.

---

### Post by Herman on 2008-03-23
:) Hello Mylorharbour,
Hey, you don't even need to bother erasing it first, and you don't probably need any fancy software, (unless you want to try it out, it's all good), just go ahead put the DVD-RW  in as it is (unerased), and try burning files to your DVD using the standard Ubuntu DC/DVD creator program.
Ubuntu is smarter than you think, the program will detect that you already have files in the DVD-RW and ask you if you want to erase it or try another DVD/RW.
Just try it, it will work.

Regards, Herman :)

---

### Post by Nano Geek on 2008-03-24
> **smartboyathome said:**
> Some apps to try are K3B and Brasero. Both are exellent at what they do.Thanks, that's exactly what I was thinking of.

---

### Post by Ocxic on 2008-03-24
actually I think thats a feature of the disk, simply overwrite, no need to erase before hand.

---

### Post by Mylorharbour on 2008-03-24
Thanks guys, Problem solved

---

