---
title: "Putting the buttons together?"
date: 2008-10-18
forum: Art &amp; Design
---

### Post by Osborn on 2008-10-18
I am wondering how to put the back and forward-buttons together like in mac OS X?
Is it possible do do it?

Look how the buttons are here:
[IMG]http://developer.apple.com/documentation/Carbon/Conceptual/ProvidingUserAssitAppleHelp/Art/help_viewer_window.jpg[/IMG]

---

### Post by Hairy_Palms on 2008-10-19
as far as i know you cant without some serious nautilus hacking, you can customise it a little bit tho by editing as root
/usr/share/nautilus/ui/nautilus-navigation-window-ui.xml specifically the "Toolbar" section

---

### Post by sethvath on 2008-10-19
Remove the button spacing in nautilus, that will affect all your nautilus buttons too. In your icon set, search for the left and right navigation icons and modify them such that they appear next to each other. 

Finally in your nautilus menu preferences, disable show text under icon to mimic the OSX buttons.

---

### Post by thongstele on 2010-11-21
> **Osborn said:**
> I am wondering how to put the back and forward-buttons together like in mac OS X?
Is it possible do do it?

Look how the buttons are here:
[IMG]http://developer.apple.com/documentation/Carbon/Conceptual/ProvidingUserAssitAppleHelp/Art/help_viewer_window.jpg[/IMG]

Your demand is same to me. unfortunately i dont know how to do it though i find the way in gconf-editor (like registry in windows) to modify them. 
In my Ubuntu, i use transformation program to convert to Mac (Macbuntu) and use elementary theme for Nautilus. I looks very nice but i want to go further is move back and forward buttons near together (as the picture above in Finder). But i cannot know the way up to now...
Anyone know, please tell me...hic,hic

Email: [email]tchauthong@yahoo.com[/email]

---

### Post by overdrank on 2010-11-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

