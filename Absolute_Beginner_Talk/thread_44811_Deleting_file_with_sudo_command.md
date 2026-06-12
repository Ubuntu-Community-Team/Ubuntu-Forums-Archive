---
title: "Deleting file with sudo command"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by kolya on 2005-06-27
Hi I've been a windows user for a while but have wanted to switch to Linux.  I installed Ubuntu yesterday and have been very impressed with the product.  I have been doing my best to answer my own questions by reading on the forum, but I have a minor question.  I did the mouse buttons fix found here: [http://www.ubuntuforums.org/showthread.php?t=3828&highlight=mouse+buttons](http://www.ubuntuforums.org/showthread.php?t=3828&highlight=mouse+buttons)

but accidentally put the imwheelrc file in the Xsession.d folder.  I deleted it by browse files/folders as root user in Nautilus.  However a file named imwheelrc~ still appears in that folder when I search under gedit.  My question is does this matter, is there a way to delete this file and also is there a terminal command to delete files.  Thanks in advance for the help and sorry if I made this post too long.

---

### Post by manicka on 2005-06-27
You can leave it there if you want, it shouldn't effect things. It's just a backup file.

sudo rm /path_to_file/file

---

### Post by kolya on 2005-06-27
Okay, Thanks.

---

