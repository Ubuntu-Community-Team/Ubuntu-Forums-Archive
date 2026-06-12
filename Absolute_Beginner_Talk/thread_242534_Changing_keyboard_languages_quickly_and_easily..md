---
title: "Changing keyboard languages quickly and easily."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by ExploreMN on 2006-08-23
Hi, I'm new to Linux and Ubuntu. I'm having trouble figuring out how to change the keyboard language.  I've found how to load an additional language but not how to implement it.  Here is the situation. My wife is Russian.  She likes to read and write in Russian to her friends and family back home.  However, to surf the net and do anything else she needs English.  Now, on a Microsucks computer its pretty easy because it puts a little keyboard selector in the task bar and you can change the language with a simple keystroke.  
Is there a way to do this in Ubuntu?  If so, can someone please provide detailed instructions on how to implement it?  It needs to be a on-the-fly change too.  None of this going into systems settings every time you need to change languages stuff. :)

Thanks in advance to anyone who can help.

---

### Post by fiver22 on 2006-08-23
This should help you out: [http://ubuntuforums.org/showthread.php?t=129860](http://ubuntuforums.org/showthread.php?t=129860)  - I found it via the search. I've learned that the search function on these boards can be your best friend -especially the advanced search.
Hope that helped you out.

---

### Post by ExploreMN on 2006-08-24
Thanks Fiver, but that doesn't seem to work. I should have stated that this is an older PC and I have xUbuntu installed on it.
All the stuff I have found for xUbuntu doesn't seem to work and I can't find anything in the settings to change it.  I've added Russian language support, but that seems to change the whole operating system while leaving the keyboard set to the US standard. I did the keyboard layout switcher thing in the taskbar, but that only has US in it as an option.  I can't figure out how to edit the xorg.conf file to add Russian to it. I've tried the various "sudo" commands I've found but they all say the directory doesn't exist, yet I can see the directory in my file browser.  I just don't know how to get into it and edit the file I guess.

I hate to say it, but this is why Microsucks still dominates the desktop. In Windows 95 and up I would have been able to accomplish this simple task in about 30 seconds.  In Linux I have been hunting and fighting this for about 4-5 hours over 2 days so far with still no resolution. :(

---

### Post by LadyDoor on 2006-08-24
[http://www.ubuntuforums.org/showthread.php?t=237794](http://www.ubuntuforums.org/showthread.php?t=237794)

Here's a guide by li'l old me for how to do it with **xbindkeys**. Please note that in the part where you select the specific languages you want, you should put whatever language you're trying to switch to instead of the ones I suggested, and that you should pick keybindings you like. Oh, and "Mod4 is the windoze key on my keyboard.

*Shrug*

I hope that helps!

--Door

---

### Post by Glenoligron on 2007-07-03
**ExploreMN**, I wonder if you got any luck with the Russian layout?
That is the first thing I bumped in after installing Ubuntu. I started experimenting without consulting the forum, initially I installed language support - after which nothing happened. That I installed SCIM and than gone into Add to Panel option and added Russian switcher there. It does work now.  
   No luck with a shortcut yet. :(
I am not quite sure if I did it correctly adding SCIM though... :)

---

