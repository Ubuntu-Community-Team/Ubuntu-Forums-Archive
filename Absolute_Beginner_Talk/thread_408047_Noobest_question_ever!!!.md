---
title: "Noobest question ever!!!"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by makinasvp on 2007-04-12
[B][COLOR="Black"]Hi guys. 
First of all I want to say that I switch from 64bit to 32bit today and my oh my!!! Ubuntu is like the best invention ever!!! 
Now for the noob question...
I intended to move my trash can which was located on the bottom right, to the desktop. So I selected "move from panel", and now my trash can disappeared... :(
Now the noob question is: Can anyone teach me how to have a trash can icon back? To the desktop please?
Thank you.[/COLOR][/B]

---

### Post by Malakia on 2007-04-12
Right click on the taskbar and select Add to Panel and you should find the icon for the trash can there.

---

### Post by makinasvp on 2007-04-12
> **Malakia said:**
> Right click on the taskbar and select Add to Panel and you should find the icon for the trash can there.

Thank you very much!! Now do you happen to know  how I can move that icon to the desktop?

---

### Post by tonyr1988 on 2007-04-12
Applications >> Accessories >> Terminal and type:

> gconf-editor

In the left pane, navigate to apps >> nautilus >> desktop

Look for "trash_icon_visible" in the right pane. Check the box next to it. 

Close the window.

Should be good to go! :D

---

### Post by makinasvp on 2007-04-12
> **tonyr1988 said:**
> Applications >> Accessories >> Terminal and type:



In the left pane, navigate to apps >> nautilus >> desktop

Look for "trash_icon_visible" in the right pane. Check the box next to it. 

Close the window.

Should be good to go! :D

Well sir, that did the job! :) Thank you very much. :)

---

### Post by zeddock on 2007-04-14
Along the same lines.....

I am on ubuntu feisty beta. Last night I was cleaning up some unneeded files and started to fall asleep.
Short Story: I deleted a list of files from the wrong directory. I need to recover them!

I think I may have a chance because I deleted them through the GUI, where it says Move To Trash.

Is there a record of what I deleted? and from where?

I see many files in the trashcan, but I do not see a restore or indication as to WHEN they were deleted.

Please help?

Thanx.

zeddock.

---

### Post by DaDave on 2007-04-14
If you have Thunar File Manager you can open the trash with it, go to the item in question. Right click on the item and one of the menu selections is "restore". Click on restore and Thunar will put that trashed item back where it came from.

---

### Post by zeddock on 2007-04-14
Thanx! Tried that, but the folder opened within Thundar, called Trash, had NOTHING in it, so it must be looking somewhere other than where the regular trash folder is under the standard ubuntu.

Anybody else?
Wasn't there a log of the selection and mov  of those files through the gui?

---

### Post by chalex on 2007-04-14
I just tried deleting a file using Ubuntu and looking in the Trash; it doesn't look like it remembers where the file came from.  As for when it was deleted you can look at the "ctime" using something like "stat ~/.Trash/filename"  
the Change line will tell you when the file was moved to the Trash.

---

