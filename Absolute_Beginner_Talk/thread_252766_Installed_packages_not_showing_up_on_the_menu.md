---
title: "Installed packages not showing up on the menu"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Trashy on 2006-09-07
Howdy all.  After years of wishing I had the moxy to stick it to Bill Gates, I have finally made the switch to Linux from XP.  I absolutely love Ubuntu, and I can tell that once I get the hang of it, I'll die happy.

I considered myself a Windows power user, and I literally jumped right into Ubuntu, spending about 15 hours immediately after install pouring over web info and trying things out.  I have uncovered a lot of things I'd like to know, and I suppose the best method is one-at-a-time learning.  So here we go.

I figured out the add/remove system, how repositories work, the four levels of repositories, and synaptic.  But what I can't figure out is why some of the installed packages do not show up in the applications menu.  I know that some of the applications are hidden on the menu, and I looked through those too.  The closest thing I could find on the web was a somewhat muddled reference to it saying it was "easy" to add them manually, but it gave no step-by-step.  Additionally, I am totally confused by the file sytem and directory tree of Ubuntu (if there is one) and I don't even have the slightest clue where to look on my hard drive to find these packages.  I will admit that I am assuming that it works something like a Windows interface where you are basically creating a "shortcut" to a pre-existing file.  Anybody wanna jump up and field this one?  I'd be much obliged.

---

### Post by anaconda on 2006-09-07
just go to aplications/ala-carte menueditor and add your program to the menu. (go the the part of the menu you want to add it to, click file/new menu entry or somethong and type the command that starts the program.) usually all installed programs are in PATH (propably /usr/bin), so you dont have to know where exactly it is installed

or you can start the program from terminal by writing the name of the program..
actually this isn't ubuntus problem.. many programmers just omit the adding to menu phase.

sorry. cant help you more, because Now I have to be in windows.. ( aaaarrgghh  !!)

---

### Post by WalmartSniperLX on 2006-09-07
> **anaconda said:**
> just go to aplications/ala-carte menueditor and add your program to the menu. (go the the part of the menu you want to add it to, click file/new menu entry or somethong and type the command that starts the program.) usually all installed programs are in PATH (propably /usr/bin), so you dont have to know where exactly it is installed

or you can start the program from terminal by writing the name of the program..
actually this isn't ubuntus problem.. many programmers just omit the adding to menu phase.

sorry. cant help you more, because Now I have to be in windows.. ( aaaarrgghh  !!)

LOL I know exatly how that is :p 

But yeah what he said ^ works for me everytime. Sometimes what im looking for isnt in the menu editor so i make one and drag it in :D

---

### Post by Dinerty on 2006-09-07
If you still can't see it, then there a are a few other things you can try:

1. Restart X (ctrl + alt + backspace), restarts X server and updates the neccessary changes

2. Like previously mentioned just run program name in terminal e.g. firefox, amarok, kopete and so forth

3. To see a greater list of programs installed, then go to Synaptic Package Manager (System > Adminstration > Synaptic Package Manager), and search for "menu-xdg", this is the Debian menu and shows a larger list of installed programs.

4. Or like previously mentioned use alacarte menu editor

---

### Post by jordanmthomas on 2006-09-07
Also, you can try to install the `menu` package (from either mulitverse or universe, so you'll need to enable them).  It doesn't get *every* program, but most of them will show up on your menu.

**edit**
Dinerty beat me

---

