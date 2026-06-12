---
title: "Macbook Pro Keyboard Help"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by speedemonV12 on 2008-05-19
hi everyone, just switched to Ubuntu a couple of days ago, and I had a few questions about the keyboard...

1) How can i change the control key to the command key? Like how it is in OS X compared to Windows, all actions done with the control key in windows are done with the command key in OS X, and I would like to use the command key in ubuntu for all of the control key actions also. How do i do this?

2)This one is kind of an application question. I use quicksilver in mac, and i have the shortcut set to command-space. I want to set up Gnome-do to do the same thing, how can i do this?

3) Last, but probably the most important, how can i set it up in firefox, so that when i hit the delete key, it will go back a page?

4) One more, is it possible to make delete a file be command + delete key?


Thanks for the help !

---

### Post by cyberdork33 on 2008-05-20
> **speedemonV12 said:**
> 1) How can i change the control key to the command key? Like how it is in OS X compared to Windows, all actions done with the control key in windows are done with the command key in OS X, and I would like to use the command key in ubuntu for all of the control key actions also. How do i do this?
This only swaps the Left side I think, but this is how to do it:
[http://ubuntuforums.org/showpost.php?p=4579588&postcount=4](http://ubuntuforums.org/showpost.php?p=4579588&postcount=4)

> **speedemonV12 said:**
> 2)This one is kind of an application question. I use quicksilver in mac, and i have the shortcut set to command-space. I want to set up Gnome-do to do the same thing, how can i do this?Skipping this one because I have no idea.

> **speedemonV12 said:**
> 3) Last, but probably the most important, how can i set it up in firefox, so that when i hit the delete key, it will go back a page?
I find this very annoying also... In firefox, type in the address bar "about:config". Once in the config, type "backspace" in the filter. Set the value for "browser.backspace_action" to 0

> **speedemonV12 said:**
> 4) One more, is it possible to make delete a file be command + delete key?I sure it is possible, but do not know where.

---

### Post by speedemonV12 on 2008-05-20
thanks for the firefox and the link to the keyboard mapping.. i will try and figure that one out... i actually was just about to edit my post to add the fact the i want Ctrl + Click to be right click, which is what he was looking for, but never figured out how do it.

---

### Post by cyberdork33 on 2008-05-20
> **speedemonV12 said:**
> thanks for the firefox and the link to the keyboard mapping.. i will try and figure that one out... i actually was just about to edit my post to add the fact the i want Ctrl + Click to be right click, which is what he was looking for, but never figured out how do it.
Honestly, I don't think that one can be done without modifying something (synaptics?) You can multi-finger-tap to middle and right click (i.e tap three fingers), you can map a keyboard key to right click as mentioned in the Macbook wiki, or you can use the modified synaptics module to get fingers+click working like in OSX: [http://launchpad.net/~mactel-support/+archive](http://launchpad.net/~mactel-support/+archive)

---

### Post by speedemonV12 on 2008-05-20
hmm .. there has to be a way!!! 

but i tried the swap link that you gave me, but no luck.. any other suggestions?
this has got to be a common problem, i can imagin lots of people running ubuntu on macbook would want to change those two keys..

---

### Post by cyberdork33 on 2008-05-20
> **speedemonV12 said:**
> hmm .. there has to be a way!!! 

but i tried the swap link that you gave me, but no luck.. any other suggestions?
this has got to be a common problem, i can imagin lots of people running ubuntu on macbook would want to change those two keys..
Make sure you run xmodmap with your config file:
```
xmodmap ~/.xmodmap
```Adding this command to your sessions startup will enable it on every boot. See the Macbook Pro Wiki for a similar process for another function.
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by speedemonV12 on 2008-05-22
i dont have a xmodmap file in my home directory.. do i need to create it, and then just put this in the file and save as .xmodmap in my home directory?

!
! Swap Control_L and Super_L
!
remove mod4 = Super_L
remove control = Control_L
keysym Control_L = Super_L
keysym Super_L = Control_L
add mod4 = Super_L
add control = Control_L

---

### Post by cyberdork33 on 2008-05-22
> **speedemonV12 said:**
> i dont have a xmodmap file in my home directory.. do i need to create it, and then just put this in the file and save as .xmodmap in my home directory?

!
! Swap Control_L and Super_L
!
remove mod4 = Super_L
remove control = Control_L
keysym Control_L = Super_L
keysym Super_L = Control_L
add mod4 = Super_L
add control = Control_Lyep

---

### Post by speedemonV12 on 2008-05-24
ok, so i have that file saved in my home directory, 
and this is in my session startup :

xmodmap ~/.xmodmap

but it did not change anything, the command keys still dont give me what the ctrl key does.  any ideas?

---

### Post by speedemonV12 on 2008-05-30
ok, so i have figured out what i am going to do .. but i have a problem.. where can i get a list of all the commands that i can make a key do? So like i have a keycode, and i am going to put that code into .xmodmap, but where can i find a list of choices that i can make that key do ?

Like i want the right apple key to have the function of the control key
I want the enter key right next to the right apple key to be my delete key. 
And i want to make the ctrl key right click( i figured out how to make the right apple key right click, but im going to change it to the left control key)

---

### Post by speedemonV12 on 2008-06-01
anyone? there have got to be a lot of mac users that want this, and some that have figured it out?

---

