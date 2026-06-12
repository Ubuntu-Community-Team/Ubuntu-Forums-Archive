---
title: "Zoom Level"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by drunkardivan on 2008-02-19
OK, I have my just-turned-3 year old son running Gutsy on an old Compaq Presario. He has managed to zoom everything in to the "unimaginably large" level. His top and bottom panels are defaulting to 69 pixels, just to give you an idea of the zoom level. 

I tried the "win" key and mouse wheel- nothing.

It's not screen resolution, that's still showing 1024x768. I have no idea how he's managing to do this- I know it's nothing involving the "f" keys, since he has a special child's keyboard that doesn't even have those keys.

So, please help me a. fix the problem and b. let me know if there's a way to lock this task so he can't do it again.

---

### Post by ryanhaigh on 2008-02-19
I believe this is adjusted via control+alt and + or -.

Im not sure whether it is possible to prevent this there is probably some option you can put in xorg.conf like the dont zap option for ctrl-alt-backspace google may help you.

---

### Post by drunkardivan on 2008-02-19
> **ryanhaigh said:**
> I believe this is adjusted via control+alt and + or -.

I had hope. Alas, this was not the solution. Thanks, though!

---

### Post by drunkardivan on 2008-02-20
Bump.

I've tried every concievable fix that Google would show me. I'm feeling very clueless here.

Please help if you can- I really don't feel like re-installing, as it's a pain to get all his kid's websites back.

---

### Post by ryanhaigh on 2008-02-20
I just tried on my own system using ctrl+alt + - and it only worked when using the numberpad keys, perhaps your child has enabled numlock and done it and you have turned numlock of which is why it wont work for you,

The other thing is where are you checking the screen resolution? Unlike windows in Ubuntu it is possible for different users to have different resolutions so you will need to check under system>preferences>screen resolution rather than system>admin>screens and graphics.

Do you have another user on the system? does the screen 'zoom' for that user aswell? What happens when you log him out or restart X?

Thats all I can think of for your zoom issue however it is very easy to backup bookmarks and settings in firefox if that is what you were talking about regarding his kids websites? All you have to do is make a copy of the hidden directory .mozilla/firefox which is in his home directory. You can then copy it back after a fresh install but hopefully it wont come to that.

---

### Post by drunkardivan on 2008-02-20
> **ryanhaigh said:**
> I just tried on my own system using ctrl+alt + - and it only worked when using the numberpad keys, perhaps your child has enabled numlock and done it and you have turned numlock of which is why it wont work for you,

The other thing is where are you checking the screen resolution? Unlike windows in Ubuntu it is possible for different users to have different resolutions so you will need to check under system>preferences>screen resolution rather than system>admin>screens and graphics.

Ryan, thank you for your help here. 

In no particular order- I checked both places. I also looked in System>preferences>universal access, just in case he had it somehow set up for the visually impaired. Hell, I looked in just about everything in system>preferences and system>administration. And I know it's got to be something simple, as he doesn't know the password on that box and, even if he did, he's 3. Typing isn't exactly his strong suit. That's why I think it's got to be a key combination, I just can't figure out which one!

Right now, he is the only user on that system- which is by design. It's our old family desktop 'puter, and I figured he'd eventually do something like this (his powers of destruction are amazing!), and I'd rather have him doing it on something that would just be gathering dust rather than, say, my brand-new Sony Vaio. As soon as I get this issue figured out, there WILL be another user on that box, and it will have permission to do only three things- surf the web, look at pictures, and look at documents.

As for the keypad thing- his keyboard doesn't HAVE a numberpad. That's the frustrating thing here- my ability to correct an error is blocked by a three-year-old boy's ability to push random buttons. 

I might just let him edit the Linux Kernel. He'll either destabilize the system in twelve seconds, or he'll come up with some unheralded fix that would make even the oldest 386 run like a Cray Supercomputer from the NSA.

---

### Post by drunkardivan on 2008-02-20
Oh, and if this helps- it's only his windows and panels- the background image is still sized perfectly.

---

### Post by Twizzle on 2008-02-20
Can you try plugging in another keyboard that does have the numberpad?

---

### Post by drunkardivan on 2008-02-20
Twizzle, I like the way you think... but I tried that last night. No joy.

---

### Post by drunkardivan on 2008-02-26
Bump- one last plea for help on this one before I take the Windows route and re-install.

---

### Post by SOULRiDER on 2008-02-26
You could delete your config, that would be sort of like reinstalling. Create a new user and log into gnome with the new user, see if its all zoomed in.

---

