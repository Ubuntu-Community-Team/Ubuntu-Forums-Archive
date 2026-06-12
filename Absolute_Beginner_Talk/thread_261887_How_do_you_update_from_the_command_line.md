---
title: "How do you update from the command line"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by louieb on 2006-09-20
[SIZE="2"]I noticed that the orange square has appeared in the upper right corner of my Gnome desktop. It appears to include a kernel update. The last few times I have updated the kernel X refused to start and I had to run
```
sudo dpkg-reconfigure xserver-xorg
``` and hope that fixed things. 
[COLOR="Red"]I've read somewhere that the configuration utility does a better job of hardware detection if it is run from the command line. Is that correct?[/COLOR]
I know I can get there by doing a cntl-alt-backspace or booting in recovery mode. 
if I run ```
sudo apt-get update
sudo apt-get dist-upgrade  
``` does it do the same updates I would get if I ran update manager from the GUI. And does it make a diffrence how I get a command line prompt.[/SIZE]

---

### Post by skymt on 2006-09-20
Where did you read that? It doesn't make much sense.

---

### Post by louieb on 2006-09-23
It did not make much sence to me either. But personal experience is that "x" broke when updating through the GUI update manager. To fix "x" I ran the configuration manager from the command line. I don't remember where I read  it. But that is not the question. 
  My question is about updating through the command line (not a terminal window) is:
 :confused:  does it do the same updates I would get if I ran update manager from the GUI. And does it make a diffrence how I get a command line prompt.

---

### Post by bulldog on 2006-09-23
When you click at the orange box you should see a list with the updates.
Just uncheck the ones you don't want to install.

Live is not that hard:cool:

But if you have trouble starting X-server after a kernel update try

sudo uname -r

make a note of the output

sudo aptitude install linux-restricted-modules-output

---

