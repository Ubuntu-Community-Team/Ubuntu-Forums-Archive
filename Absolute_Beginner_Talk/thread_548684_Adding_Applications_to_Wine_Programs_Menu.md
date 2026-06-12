---
title: "Adding Applications to Wine Programs Menu"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2007-09-11
I am having some trouble adding programs to the Wine section (quick launch) of the Applications menu.  I've gone to edit menu and tried every combination imaginable, but to no avail.

Anyone know how to do this?

I am trying to add quick launches for MS Office items I run through Wine.

---

### Post by Ink-Jet on 2007-09-11
Why not just use OpenOffice?

---

### Post by ExSuSEusr on 2007-09-11
I can and do, but I am trying to learn how to do everything I can with Ubuntu.... so while I may not really *use* MS Office... I still want to know how to do what I am doing :)

Besides I plan on installing Photoshop (which I think is still a bit superior to Gimp in some ways) and I will need to know how to add it's quick launch to the menu.

---

### Post by ExSuSEusr on 2007-09-11
I figured it out...

For those of you wanting to do the same thing - here is a quick 'How To' that I hope you find helpful.

When you want to add a quick launch to your Applications menu (under the Wine option) do the following:

Right click on the top menu bar -> Choose Edit Menu.

Expand the menu options of Wine and and select Add Menu.  Give it a name and click Close.

Click on it on the left side under the expanded Wine tree. 

Select Add Item from the list on the right side of the interface.

Give your application a name.

Put the following code in the command field.

> env WINEPREFIX="/home/usrname/.wine" wine "C:\Path To EXE File\XXX.EXE"

Select Close.

You can add a comment if you wish.  Just a mouse over that gives you a brief description.

Ok, here's an example.

Right click on menu bar -> Edit Menu -> Scroll down to Wine -> Select Add Menu

Name: MS Office
Click Close

Click on newly formed folder on the left side under the expanded wine tree.

Click on Add Item on the right hand side of the interface.

Name: MS Word

Command: env WINEPREFIX="/home/billybob/.wine" wine "C:\Program Files\Microsoft Office\Office\WINWORD.EXE"

Comment: Click here to use MS Word.

Click Close.

That's it.  You should now be able to access you application from the main tool bar of your desktop.

---

### Post by chrome307 on 2007-09-12
***Excellent tip - just what I was looking for :)***

Now all I need is to find some new icons for my applications!!

---

