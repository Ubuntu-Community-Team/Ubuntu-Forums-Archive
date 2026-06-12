---
title: "Taskbar Buttons Missing"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by piddubutt on 2007-02-07
I've had a dual boot system going for a few months, but I've been primarily using windows because I haven't quite been able to get over the learning curve yet. One of the problem I'm having is that the taskbar at the top has parts of the menu missing. All three buttons are there, but the Administration menu under System only has 6 options showing;  things like Synaptic, Users and Groups, and Login Screen Setup are missing. This is quite annoying, especially since I'm not very familiar with linux commands. 

Also, the other problem I've had is with user accounts. I've been using the root account because the initial user account has never worked for some reason. Before, the system would boot up into a command prompt, and I would log in using root and my password, then type 'startx' to fire up the GUI. After updating though, it's booting into the gui, which doesn't let me log in as root. When I try to use the initial account, it gives me some errors saying that the account doesnt have a home folder, and then brings me back to the login screen. So instead, I'm using the 'recovery mode' option in the grub menu, which brings me to the command prompt and through which I log in using root and startx.

I would really appreciate any help!

---

### Post by dbbolton on 2007-02-07
edgy or dapper ? (6.06 or 6.10)

also, did you try running 'alacarte' from the terminal ?

---

### Post by piddubutt on 2007-02-09
I already tried using alacarte. All the boxes are checked, but they're just not showing up in the menu.

---

### Post by piddubutt on 2007-02-09
Oh, and I'm using Dapper.

---

### Post by enky4u on 2007-02-17
i also have the same problem, the menu item 'synaptic package manger' is enabled in the Alacarte menu editor, but, its not shown in the top panel,

plz help..

---

### Post by unisol on 2007-02-17
You are missing some important packages

Try this:

Drop to the command line (exit the gui desktop).


Code:
sudo apt-get install metacity
sudo apt-get install nautilus nautilus-data

---

