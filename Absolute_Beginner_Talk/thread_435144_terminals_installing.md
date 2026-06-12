---
title: "terminals? installing"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-05-06
I dont know how many posts ive made, but Im a complete newb to linux. I want to get flash player installed so I could youtube it, but I dont know how to do it. the readme text says:

In terminal, navigate to the unpacked directory and enter:
          + $ ./flashplayer-installer
          + Click Enter key and follow prompts

when i open a terminal through apps > accessories what do i do after. 
How do I navigate to the unpacked directory and enter it, then how do i do the $./flashplayer installer. 

If anyone could give instructions in the most basic terms, id appreciate it greatly, im trying to witch OS's and it woul dbe great if I knew how to do stuff like this.

---

### Post by bobplano on 2007-05-06
cd *whatever/directory/it's/in*
then just use ./flash-installer (no need for $)

---

### Post by em11488 on 2007-05-06
what does that mean. Im a complete newb to linux, do i copy that and just paste it in? what do i do

---

### Post by bobplano on 2007-05-06
cd changes the directory to wherever the location is after the command. for instance let's say you wanted to go to your home folder. then you would put cd /home. that is an absolute location because no matter where you are in the terminal typing cd /home will take you to your home location. but what if you had a folder called let's say flash under your own directory? well by default the terminal opens into your directory so you could just put in a relative location like cd flash. this isn't probably what your asking though. you put the directory with the flash-installer somewhere. so in the terminal you need to change the directory you are in to whatever directory you need to be in. so 
```
cd *path/to/folder*
``` and the path to folder would be wherever you put the flash-installer. once you are there you can use ./flash-installer and that will run it.

---

### Post by aysiu on 2007-05-06
You don't need the terminal to install Flash, but either way (terminal or not), this tutorial will help you get it installed:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by alinuxfan on 2007-05-06
the ./ lets the shell know that you want to run the command from the current directory and not the shell variable (if there is one of that name)

so 
cd /path/to/directory
./flash-installer

---

