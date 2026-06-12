---
title: "How to install an icon set?"
date: 2008-08-23
forum: Art &amp; Design
---

### Post by Mashy on 2008-08-23
I downloaded the bws icons set from gnome look, in .tar.gz format, and am having some trouble installing them. 
Everything I've googled seems to suggest that I should either install it like I would a theme (from the system, preferences, appearance, theme window) or to pick an existing theme, click on customize, go to icons and that there should be an install button for icons there. 
But there isn't.

Can someone please tell me what I should be doing to install a set of icons.

Any help will be much appreciated.
Thanks.

---

### Post by OutOfReach on 2008-08-23
Just open up System>Preferences>Appearence and drag and drop the .tar.gz file into the Appearence window and it will ask you if you want to apply the theme and press Yes. :)

---

### Post by Mashy on 2008-08-23
> **OutOfReach said:**
> Just open up System>Preferences>Appearence and drag and drop the .tar.gz file into the Appearence window and it will ask you if you want to apply the theme and press Yes. :)

That's what I've been trying, and how a few sites have said how to do it. I get an error message saying that Icons does not appear to be a valid theme.

---

### Post by OutOfReach on 2008-08-23
Hmm, okay try this:
Extract the .tar.gz file.
Open up the file manager and goto:
~/.icons
Drag and drop the extracted file into file manager.
The folder should show up in the file manager, now goto System>Preferences>Appearence and press the Customize button, goto the Icons tab and your theme should show up, select it and exit.

---

### Post by Mashy on 2008-08-23
> **OutOfReach said:**
> Hmm, okay try this:
Extract the .tar.gz file.
Open up the file manager and goto:
~/.icons
Drag and drop the extracted file into file manager.
The folder should show up in the file manager, now goto System>Preferences>Appearence and press the Customize button, goto the Icons tab and your theme should show up, select it and exit.

Sorry, but where is the .icons folder? I've done a couple of searches of my computer and there are a few folders outside of my home folder with 'icons' in them, but none in the whole system with '.icons' in their name.
Where should I be looking? 


Sorry, I've only been using Ubuntu for a week. XD

---

### Post by OutOfReach on 2008-08-23
Ok I'll make it a little easier, goto Application>Accessories>Terminal and type in:
nautilus ~/.icons
It should bring up the icons folder.
Close the terminal and do what I have instructed. :)

---

### Post by Mashy on 2008-08-23
> **OutOfReach said:**
> Ok I'll make it a little easier, goto Application>Accessories>Terminal and type in:
nautilus ~/.icons
It should bring up the icons folder.
Close the terminal and do what I have instructed. :)

Thanks, I've put the folder there but nothing is coming up in the icons tab.

Sorry for this trouble.

---

### Post by OutOfReach on 2008-08-23
Weird, can you give me the link of the icon set that you downloaded?

---

### Post by Mashy on 2008-08-23
[http://gnome-look.org/content/show.php/BWS_Icons?content=83610](http://gnome-look.org/content/show.php/BWS_Icons?content=83610)

They seem to be a popular set.
Hmm, just looked in the comments and someone said something that each icon needs to be installed manually. Would that involve doing the same as before, just them not being in their folder, do you think?

Edit: Just did that, copied the individual images into the .icons folder and still nothing. Interesting. I'll try it with another set of icons, hopefully it's just the set and not my installation.

---

### Post by OutOfReach on 2008-08-23
Hmm, A very strange pack, you would need to organize them and that would take some time and can be frustrating, and there are only 70 icons, a very very small Icon set. I would suggest downloading another one.

---

### Post by Mashy on 2008-08-23
> **OutOfReach said:**
> Hmm, A very strange pack, you would need to organize them and that would take some time and can be frustrating, and there are only 70 icons, a very very small Icon set. I would suggest downloading another one.

I downloaded another few, a couple seemed to be like the other one, then I got lucky and found one that does work. 

Thank you very much for your help.

---

### Post by OutOfReach on 2008-08-23
Ok no problem.
Glad to help. :)

---

### Post by smartboyathome on 2008-08-24
By the way, Mashy, that icon set you linked to is just a collection of icons, not an icon theme. The guy didn't create a compatible gnome theme at all.

---

### Post by airtonix on 2008-08-25
> Ok I'll make it a little easier, goto Application>Accessories>Terminal and type in:
nautilus ~/.icons

Using the keyboard shortcut for focusing on the location field like you would in firefox is far easier than using the terminal to open nautilus at this location.

1. with the desktop or a active nautilus window focused, press CTRL + L
2. type : ~/.icons
3. press enter 
4. ???
5. Profit

---

### Post by arashiko28 on 2008-08-25
It's on z7 or something like that, the author suggested install via terminal z7p and then address the zip7 to open and move it to /home/icons, go and check the page again.

---

