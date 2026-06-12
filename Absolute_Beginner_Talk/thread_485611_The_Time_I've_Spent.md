---
title: "The Time I've Spent"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-27
In the time I've spent trying to change my default cursors, and get my boot splash to work I could have built a spaceship, flew it to another planet, pimped out an alien hooker, flew back to earth, make my own cursor package, and boot splash, and use the money I made pimping out the alien hooker to fly Linus Torvalds, and 
Mark Shuttleworth over in a jet to do it for me. I'm not getting discuraged though. I'm acuatly more determend now than ever before. so if you would like to help me out this is where im at in my splash screen problem [http://ubuntuforums.org/showthread.php?t=485465](http://ubuntuforums.org/showthread.php?t=485465)   As far as the cursor thing goes. What can I say? I extract the folders, and drop them in the .icon folder but they don't show up as a cursor selection option. I've also tried  
the drag n drop methed no luck there either. I also tried doing the install option and pointing the install link to the cursor I wanted to use no luck there either. I want to use the silver cursor, but i've tried like 5 diferent packages  
trying to see if they would work. No luck there either. So if you have any ideas let me know. Thanks.

---

### Post by tcoffeep on 2007-06-27
The only one I can't figure out is the cursors. If you get any help, give a shout. *thumsbs up*

---

### Post by Brucevdk on 2007-06-27
> **swoll1980 said:**
> As far as the cursor thing goes. What can I say? I extract the folders, and drop them in the .icon folder but they don't show up as a cursor selection option. I've also tried 

The folder for your custom cursors is *~/.icons*, just grab an iconset and extract the folders from it (e.g. *FoobarCursors.White.Huge*) to that folder and they should show up in *gnome-mouse-properties*.

---

### Post by swoll1980 on 2007-06-27
Thats what I'm saying. When I do that it does not work for whatever reason

---

### Post by swoll1980 on 2007-06-27
bump

---

### Post by aeiah on 2007-06-27
> **swoll1980 said:**
> Thats what I'm saying. 


no, what you said was .icon. not .icons.

---

### Post by swoll1980 on 2007-06-27
Thats what I ment .icons. I looked in there all the folders are there, but non of them are working

---

### Post by tcoffeep on 2007-06-28
> **swoll1980 said:**
> Thats what I ment .icons. I looked in there all the folders are there, but non of them are working
I'm having the same problem. I set up my fonts, and sadly, none of them are working. :(

---

### Post by pistcivet on 2007-06-28
```
gtk-update-icon-cache --force ~/.icons/<name of icon directory>
killall gnome-panel
```

Might work.

---

### Post by swoll1980 on 2007-06-28
Thanks ill try

---

### Post by speeddemon8803 on 2007-06-28
Hey guys, I have been using ubuntu since 6.06...I am not quite sure of how to fix your issue, but know that I am looking into it..and will hopefully be the one to respond back with the correct fix later. Anyways, dont let a small bump ruin your fun with Ubuntu!

---

### Post by eentonig on 2007-06-28
I hope this is not a showkiller for you. Because frankly....I personally find it a bit a silly thing to make or break acceptance for an OS. 

But then, who am I to judge what people should value.

Can you show the output of 

> ls -Al ~/.icons

And inform us which one (or all) has problems? And where you got it. If I've got time, I'll download it myself to see if it works for me.

---

### Post by vegetable on 2007-06-28
> **swoll1980 said:**
> In the time I've spent trying to change my default cursors, and get my boot splash to work I could have built a spaceship, flew it to another planet, pimped out an alien hooker, flew back to earth, make my own cursor package, and boot splash, and use the money I made pimping out the alien hooker to fly Linus Torvalds, and 
Mark Shuttleworth over in a jet to do it for me...

this is the first thing i would've done, noob :roll: ;)

---

### Post by Delirious on 2007-06-29
Not sure what the problem is.  But have you made sure that the icon folder isnt a folder inside or a folder, like /youricons/youricons/iconfiles or is it youricons/iconfiles when you copy it to.icons? 

Sounds like you already know this but thought i would throw it out there.

---

