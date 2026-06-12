---
title: "help installing somthing"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by jormm on 2007-08-14
(for the record im completely new to Linux i came from xp and have no clue how to work linux other then starting the internet...)
that being said i did some googling and found out that plain shift is the only good mmo for linux so i decided to download it so i download the linux version and when i click the icon on my desktop to install it i get a error message that says...

cannot open /home/gentry/desktop/Planeshift_CBV0.3.019-x86.bin: No application suitable for automatic installation is available for handling this kind of file.

so i download the other one that was marked for Linux with the same error message so i was wondering how do i get this game to work in Linux and if you could plz explain it in the simplest of ways... like i said linux has got me all confused... not used to it yet...

btw on a side not i was wondering how do i know if my gfx card is running normaly on linux i have radion 9200 and just wanted to make sure it is running right before i start playing the game

thanks

---

### Post by Alterax on 2007-08-14
The easiest way to do this is from the terminal.

type

/home/yourusername/andsoon/until/youfindthe.bin

It's case sensitive, but you can speed it along by typing the first few letters and hitting the TAB key to autocomplete.

If the .bin won't attempt to execute, type

sudo chmod a+x /home/yourusername/andsoon/until/youfindthe.bin
Give it your password to set it as an executable file
Then re-try running it.

As for testing your card, this isn't a benchmark or anything but I usually just run glxgears from the terminal.  If the speed and smoothness are decent, you've little to worry about.

---

### Post by jormm on 2007-08-14
ok im a little new to the terminal thing but when you say

/home/yourusername/andsoon/until/youfindthe.bin

i know it go's /home/gentry/

but after that when do i put in for "andsoon" "untill" and "youfindthe.bin" i whent ahead and just did a copy past of what you typed and its said 

bash: /home/yourusername/andsoon/until/youfindthe.bin: No such file or directory

srry for the newbniss

---

### Post by jormm on 2007-08-14
any hlp plz i dont understand it?

---

### Post by crjackson on 2007-08-14
1) Open up a terminal session
2) In the terminal box type: **sudo chmod a+x**
3) Put a space after the command but don't hit enter.
4) Drag the bin file into the terminal box
5) Click your mouse button while inside the box to regain terminal focus
6) Tap the enter key on the key board

This should change the permissions for you.

OR

1) Right click on the file and bring up the properties page
2) Find the check box marked allow executing of the program
3) Close the menu
4) Double click the file
5) Select Run in terminal

---

### Post by jormm on 2007-08-14
omg thank you thank you good thing your not right here in front of me of i'd huge you tell you popped i been trying to get this to work for 4 hours now and your solution is the only one that has worked

-bows-

---

### Post by crjackson on 2007-08-14
You're welcome.  Glad it worked..

---

