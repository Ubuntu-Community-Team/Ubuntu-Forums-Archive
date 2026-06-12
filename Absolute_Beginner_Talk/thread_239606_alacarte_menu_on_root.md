---
title: "alacarte menu on root"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by goldencako on 2006-08-19
Hey, I'm having this weird problem when I'm logged in as root. In the System>Administration panel, It onyl shows a few menus entries: Device Manager, Network tools, Printing, System log and System Monitor. So i go to the alacarte menu editor, and see if the other options are unchecked, but they are checked thye are just not appearing. So to open any of those I have to open from terminal, and terminal only. I wanted to know if anyone can help me out. Thanks in advance.

---

### Post by ComplexNumber on 2006-08-19
> **goldencako said:**
> Hey, I'm having this weird problem when I'm logged in as root. In the System>Administration panel, It onyl shows a few menus entries: Device Manager, Network tools, Printing, System log and System Monitor. So i go to the alacarte menu editor, and see if the other options are unchecked, but they are checked thye are just not appearing. So to open any of those I have to open from terminal, and terminal only. I wanted to know if anyone can help me out. Thanks in advance.
fire up the commandline and type in the following where 'username' is your username:

chmod -R 700 /home/username/.local/*


that command will give read, write and execute permission to that folder and everything in it. i'm pretty certain its to do with not having read permission to that directory where the menu items are stored.
otherwise, it may be owned by root, but i don't know how that would happen. we'll take from here anyway and see if the above solves it.

---

### Post by goldencako on 2006-08-19
i tried that out and it says the folder doesn't exist

---

### Post by ComplexNumber on 2006-08-19
> **goldencako said:**
> i tried that out and it says the folder doesn't exist
can you see files in your home directory that are preceded by a '.'? if not, run nautilus, go to Edit in the menu, then Preferences, then select the 1st tab and select 'Show hidden and backup files'.

---

### Post by goldencako on 2006-08-19
alright, did that, i can see all files now. also applied that chmod -R command but it didnt work. i still cant see the admin tools

---

### Post by ComplexNumber on 2006-08-19
btw you're not supposed to be able to edit the Admin tools in alacarts> **goldencako said:**
> alright, did that, i can see all files now. also applied that chmod -R command but it didnt work. i still cant see the admin toolsi'm unclear, are you saying that you can't see admin tools in alacarte, or that you can't see admin tools in the menu? 
i hope you realise that you're not able to edit admin tools in alacarte. nobody is. see screenshot.


btw i forgot to say......you mentioned that "when I'm logged in as root". what exactly do you mean by this?

---

### Post by goldencako on 2006-08-20
this is wut i mean:
[IMG]http://i29.photobucket.com/albums/c262/goldencako/Screenshot.png[/IMG]
you see on alacarte i the icons r clicked and should be on the menu, but they are not. sorry for the bifg image, i dont know how to make thumbs

---

### Post by Kilz on 2006-08-20
Ubuntu isnt supposed to have a root login. When you force one it isnt supprising that some things are broken. :D

---

### Post by goldencako on 2006-08-21
ahhhh, didn't know that. well if anyone finds a solution I'd be glad to know

---

### Post by Anivair on 2006-08-24
The solution is to log in under your core account, of course. 

When you set up the system you created a user account.  For all intents and purposes, that is the admin account.  it's not called root, but it works like root, using sudo.  So log in with that account, not this forced root account, and it should give you the admin panel option.

---

### Post by xucchini on 2006-08-25
Is there a way to make the menu changes made with alacarte become 
the default system menus for all users who log in?

---

