---
title: "How do I?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by mittomus on 2006-08-26
This is a really, really basic question. How do I get to a command prompt? From anywhere in the computer? I am using Gnome.

Thanks for any help.

Larry

---

### Post by muep on 2006-08-26
Press alt+f2, write gnome-terminal and press enter.

or

Applications->Accessories->Terminal

---

### Post by Jerome36 on 2006-08-26
To get to the terminal click on "Applications" at the top, and it should be under "Accessories," if you're using Dapper Drake.

---

### Post by luv2craftca on 2006-08-26
Hi Larry,

I recently found it myself... click on Applications in top left of your screen then choose Accessories then Terminal.

luv2craftca

---

### Post by mittomus on 2006-08-26
Now for part 2. I am trying to install macromedia flash player and the command line is: ./flashplayer-installer  When I do that, I get "no such file or directory". I suspect I have to tell the command prompt where to find the flash player installer but I don't know how to do that.

---

### Post by muep on 2006-08-26
Where have you downloaded the installer? Is it in the Desktop?

Anyway, it would be better to just use the installer in the repositories.

First, make sure you have Universe and Multiverse repositories enabled. After that run this command in the terminal:

sudo apt-get install flashplugin-nonfree

---

### Post by mittomus on 2006-08-26
The flashplayer installer is in the tmp/flashplyaer folder. I got an error msg that flashplayer won't work on my amd 64.

Stupid newbie question #3: Where do I find the Universe and Multiverse repositories? As I said, I am really new to Linux.

---

### Post by jpkotta on 2006-08-26
[https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by mittomus on 2006-08-26
Thanks all for your help.

---

