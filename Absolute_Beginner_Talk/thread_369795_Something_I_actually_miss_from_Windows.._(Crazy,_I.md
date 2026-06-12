---
title: "Something I actually miss from Windows.. (Crazy, I know...)"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by StarscreamD on 2007-02-25
When you press the right mouse button in Windows and drag, you could create a field in which, whichever is selected could be "right-clicked". I find myself doing this often and it doesn't work with this OS. If you need to right-click many objects, you must first select all of them, and *then* right-click them. Seems like you can skip a step by integrating this borrowed idea from Windows.

What do you guys think?

---

### Post by NewOldTimer on 2007-02-25
try holding left down, works for me

---

### Post by StarscreamD on 2007-02-25
I'm sorry. Do you mean, hold down the left mouse button? That only highlights the selction. If you could right-click and drag, you could execute a batch command, such as delete or cut or whatever. Am I the only one? :P

---

### Post by NewOldTimer on 2007-02-25
my bad

---

### Post by undertakingyou on 2007-02-25
StarscreamD,

You know what, your right.  I have tried several things and I can't get it to work like it would in windows.  I don't use this feature much, so I don't feel hurt.  Usually, if I want to do something like that I either use CTRL + A or do a shift click for what I want.

Very interesting though. . .

---

### Post by StarscreamD on 2007-02-25
I've been using Ubuntu Edgy for over a week and this right-click issue is the only gripe I have! I started computing on Apple II's, then used Windows PC's up until a week ago.

What I'm trying to do, ultimately, is build value in Ubuntu for myself because for all Ubuntu has provided for me, a right-click issue seems petty in comparison.

Are there any other things that you guys really liked when recalling certain Windows features that aren't utilized by Ubuntu?

---

### Post by cantormath on 2007-02-25
> **StarscreamD said:**
> When you press the right mouse button in Windows and drag, you could create a field in which, whichever is selected could be "right-clicked". I find myself doing this often and it doesn't work with this OS. If you need to right-click many objects, you must first select all of them, and *then* right-click them. Seems like you can skip a step by integrating this borrowed idea from Windows.

What do you guys think?

works for me, I dont get it.

---

### Post by undertakingyou on 2007-02-25
One thing that I miss, I can't seem to find a place that will tell me what users are currently logged into this machine, either remotely or locally.  I know right where it is in windows, I don't in ubuntu.

---

### Post by gtratter on 2007-02-25
> **undertakingyou said:**
> One thing that I miss, I can't seem to find a place that will tell me what users are currently logged into this machine, either remotely or locally.  I know right where it is in windows, I don't in ubuntu.

From the command line at any time type

```
w
```
or
```
who -a
```
or
```
users
```

These are just a few to get you started :)

---

### Post by StarscreamD on 2007-02-25
> 
Quote:
Originally Posted by StarscreamD View Post
When you press the right mouse button in Windows and drag, you could create a field in which, whichever is selected could be "right-clicked". I find myself doing this often and it doesn't work with this OS. If you need to right-click many objects, you must first select all of them, and *then* right-click them. Seems like you can skip a step by integrating this borrowed idea from Windows.

What do you guys think?
works for me, I dont get it.

So you are telling me when you right-click, hold down the button and drag the mouse, a field opens for you? What kind of crippled Ubuntu software did I end up with?

---

### Post by shareMenaPeace on 2007-02-25
> **StarscreamD said:**
> Are there any other things that you guys really liked when recalling certain Windows features that aren't utilized by Ubuntu?

Maybe, always when i manualy copy files from 1 to another folder and the target folder is "full" stucked up with some files i have to manualy need to switch from nautilus view "list mode" to "icon mode" because if i dont do that i cant find a empty field where i just rightclick and choose "past".

In windows you can rightlick in between the lines i think, but want work on files under ubuntu. Works on folders though.

Well  :)

---

### Post by kittyhawk63 on 2007-02-25
The left mouse button does it for me also.

---

### Post by StarscreamD on 2007-02-25
> **kittyhawk63 said:**
> The left mouse button does it for me also.

What does the left-mouse button do for you? Open a right-click menu? Explain your post please.

---

### Post by Darklighter137 on 2007-02-25
What exactly are you talking about?  Are you tryin to select a bunch of items and then use the pop-up menu on all of them by clicking?  Or is it some other issue?

---

### Post by shareMenaPeace on 2007-02-25
> **Darklighter137 said:**
> What exactly are you talking about?  Are you tryin to select a bunch of items and then use the pop-up menu on all of them by clicking?  Or is it some other issue?
If you refering to my post, its a yes.
I select a couple of "items" -- "files" and STRG + C to copy or rightclick ....

---

### Post by StarscreamD on 2007-02-25
> **StarscreamD said:**
> When you press the right mouse button in Windows and drag, you could create a field in which, whichever is selected could be "right-clicked". I find myself doing this often and it doesn't work with this OS. If you need to right-click many objects, you must first select all of them, and *then* right-click them. Seems like you can skip a step by integrating this borrowed idea from Windows.

What do you guys think?

> **Darklighter137 said:**
> What exactly are you talking about?  Are you tryin to select a bunch of items and then use the pop-up menu on all of them by clicking?  Or is it some other issue?

I want to click the right mouse button and hold it down, then I want to drag it over to create the field that will make a selection, *then* execute a right-click on said selection by releasing the right-mouse button. Crystal?

---

### Post by steve.horsley on 2007-02-25
What StarscreamD is saying is that instead of this sequence which is required in Gnome:
> Left button down
Drag rectangle to select
Left button up
Move to one of the selected items
Right button down to get a menu
he wants to be able to do this:
> Right button down
Drag rectangle to select
Right button up to get a menu
This is not possible in Gnome at the moment because right-button down gives a menu instantly. 
What his proposed change would mean is that since right-button-down would no longer open a context menu immediately, instead of:
> Right button down - menu appears
Move to menu item
Right button up
the following would now be necessary:
> Right button down
Right button up - menu appears
Move to menu item
Right button down
Right button up

Personally, when I right click things, I generally release the button, then navigate the menu, then click again to select the menu item, so there would be no change to my use of right-click. Others may be in the habit of keeping the button down while navigating the menu.

Anyway, that's what he's talking about.

---

### Post by kittyhawk63 on 2007-02-25
.

---

### Post by StarscreamD on 2007-02-25
> **steve.horsley said:**
> 
This is not possible in Gnome at the moment because right-button down gives a menu instantly. 


Is there any way to change the function of the right-click in Ubuntu Edgy at the moment?

Such as: if right mouse button is pressed and held **and** drug, a selection field would open that would select and would then right-click said selection?

---

