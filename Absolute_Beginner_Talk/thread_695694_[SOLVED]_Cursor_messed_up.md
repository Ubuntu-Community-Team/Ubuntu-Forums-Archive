---
title: "[SOLVED] Cursor messed up"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Meox on 2008-02-13
hey... im new here and i need a bit of help. heres my problem.. i go to change my cursor but it only changes when i go onto firefox or some other window ok than when i go onto my desktop the cursors turns into the white defualt one.. ok and when i go to close/minimize a windows it turns into the red glass cursor.. i have no clue what the problem is i seriously need help its extermely annoying..

~thanks meox

---

### Post by sigge on 2008-02-13
Have you tried to restart x.org by doing ctrl + alt + backspace?

Sometimes these things need to be restarted after changes done in their config files... :)

---

### Post by PurposeOfReason on 2008-02-13
If that does not work make a file in /usr/share/icons called default (sudo mkdir /usr/share/icons/default). It might already be there. Now edit the index.theme, it may be blank (gksudo gedit /usr/share/icons/default/index.theme) and put the following in it:

[Icon Theme]
Inherits=whiteglass

Change whiteglass to the name of your cursor theme. No space between the = and case sensitive. Then restart X.

---

### Post by Meox on 2008-02-13
ok i'll try the second post cause i just restarted.. no luck..

---

### Post by Meox on 2008-02-13
Oh no! i typed in the folder name for icons and i even searched the browser for "icons" and it says this.. process usr/bin/trackerd  exited with status 0 

what now?

---

### Post by PurposeOfReason on 2008-02-13
Don't search as it is nowhere near as reliable as knowledge. I know for a fact that /usr/share/icons exists, tracker might not have put it into its memory. You'll need (or it is far easier) to use a terminal which is why it is better to learn with one. Open one up and type:

mkdir /usr/share/icons/default

This makes a folder called default. It will either work (by saying nothing) or say the file exists, both are good. Then, again in the terminal, type:

gksudo gedit /usr/share/icons/default/index.theme

It will open a text editor. It might have stuff, it might not. If it does, look for a part like I said earlier and change it for your needs. If there is nothing there, copy past what I put in the eirlier post and change it to reflect your cursor theme name. Remeber that it is case sensitive so if it is whiteglass and you type Whiteglass, it won't work.

---

### Post by Meox on 2008-02-13
ok i did all that.. no luck its still the same. white (default), and redglass, and obsidion..

also it wont let me delete any cursors at all. 

this all started yesterday when i installed the mac4lin cursors on there... could that help?

---

### Post by PurposeOfReason on 2008-02-13
> **Meox said:**
> ok i did all that.. no luck its still the same. white (default), and redglass, and obsidion..

also it wont let me delete any cursors at all. 

this all started yesterday when i installed the mac4lin cursors on there... could that help?

Which theme are you trying to use? I need the real name (type nautilus ~/.icons in a termainl). That will open up the file browser in your icon folder, not the user one, which is where it would be installed. Whatever that name is that you're trying to use, take that name (case sensitive) and do the same above. If all that checks out, right click the desktop, choose change background, go to the icons tab, click customize, go to the cursor tab, and see if you can do it there.

EDIT - To clarify what I said earlier does, it makes it so that the default cursor is whatever you tell it to be. You don't actually have to change it in the properties.

---

### Post by Meox on 2008-02-13
ok i went back into the text editor for the icons that you told me to do ok.. i went into the .icons folder like you told me.. i an trying to use the Obsidian (<-- that is the exact name) cursors so i type it in ok and i press save here is what i get 

could not save the file /use/share/icons/index.theme 
unexpected error: file not found 


What do i do?! 

EDIT: i looked in apperance ok.. my default cursor is reglass.. which is odd

---

### Post by Meox on 2008-02-13
ok i was able to make the Obsidian cursor as my default.... but when i go to my desktop it changes to the white default one

what now? 

EDIT: also when it loads a page or something my loading cursor changes to the white cursor 
EDIT: also when i go to the minimize/close button my cursor turns into the reglass cursor

---

### Post by Meox on 2008-02-13
i'll keep checking in.. for now i'll deal with it 

EDIT: Wow this is weird.. if compiz-fusion is off than it will be fine but if its on than it messes up... hmm. i wonder

---

### Post by PurposeOfReason on 2008-02-13
We are close. :)

The file is /usr/share/icons/default/index.theme

You forgot the default. You also typed use and not usr. That will fix everything but the redglass. To fix that, go to the appearance tab again and switch from redglass to Obsidian.

---

### Post by Meox on 2008-02-21
as of a hile ago it just went away so its fixed

---

