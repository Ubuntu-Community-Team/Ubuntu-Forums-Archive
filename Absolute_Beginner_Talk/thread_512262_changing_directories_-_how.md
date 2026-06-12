---
title: "changing directories - how?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by paker on 2007-07-29
1) When I first select Terminal < Accessories < Applications, I get this:

**rust@rust-desktop:~$ **

Am I on home? or am I on desktop?

2) How do I move up or down? I am trying to get into the "TEMP" directory where I dragged diswrapper-1.47-tar.gz to with mouse (from desktop).

Thanks.

---

### Post by mikewhatever on 2007-07-29
By default you are in the home directory. To move up use > cd ..
to move to the Desktop > cd ~/Desktop
You can also switch to any directory directly,for example > cd /home/your_user_name/Examples

---

### Post by anewguy on 2007-07-29
The username@xxxxxxxxx is showing the logged in user and the computer they are logged on to.  To see the directory you are in, type   pwd      (that's print working directory).   You can use "ls -al" to see all of the files and folders in your current directory.   You use "cd"  (change directory) to set your default to another directory.:)

---

### Post by meierfra on 2007-07-29
You are in your home folder. ( The ~ stands for your home folder)  You change directories via cd  (change directory). For example


```
cd Desktop
```
gets you to the deskop folder. And then 

```
cd TEMP
```

moves you to the folder  TEMP on the Desktop.

 you can also get there in one step:

```
cd Desktop/TEMP
```

---

### Post by paker on 2007-07-29
Thanks. 
"cd Desktop/Temp" moves me 2 steps down.:)
How do I more 2 steps up? I mean from Temp to home?
I tried cd Desktop/home, but it didn't work.
Thanks.

---

### Post by meierfra on 2007-07-29
```
cd
```

moves you back to your home folder ( from any where)

```
cd  .. 
```

Moves you one step up.

---

### Post by livingtarget on 2007-07-29
Some quick tips:

~ this character, the tilda ~ is equivalent to the directory /home/your_username/, so typing it like this "cd ~" will move you to your home directory.

What's in a directory? You can type "dir" to see what's there. You can use more advanced commands like "ls", but I never use those a lot.

Using tab completion is great. Just press tab when you started to type something. For example: typing "cd Desk" and then hitting tab from my home directory it changes the command automatically to "cd Desktop". It's really great, I don't know if this is switched on in a default install or not.

If you want to move 2 steps up from "/home/your_username/" to "/" then just type "cd .." twice or type "cd ../../" 

Moving up a directory means moving from /directory_1/directory_2/directory_3/ to /directory_1/directory_2/ down to /directory_1/ etc. Think of your directories as a tree, you move up the tree when you move up a directory.

Hopefully that helps, I just spit out a lotta info there. Hope it helps a bit.

---

### Post by paker on 2007-07-29
Thanks. I have been using ubuntu for 6 months, and I have avoided terminal just because of the directory confusion. Now I feel much more comfortable in the terminal mode.

---

