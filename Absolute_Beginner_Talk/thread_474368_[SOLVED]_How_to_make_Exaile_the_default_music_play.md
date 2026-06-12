---
title: "[SOLVED] How to make Exaile the default music player?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-15
I have RhythmBox installed, and my media buttons are configured to open, play/pause etc in RhythmBox. Now I wanted to try out Exaile, but how do I change the media button settings to open Exaile instead of RhythmBox?


I do not want to remove RhythmBox until I am sure, I will keep Exaile.

Thanks.

---

### Post by tipsqueal on 2007-09-20
I was wondering the same thing. I have a really nice Logitech wireless keyboard that I got for free and it has really nice support out of the box for all of the media buttons in Linux. Something that I found surprising. Anyways I also use Exaille because I find it to be very superior to Rythmbox and even Amarok (I don't like Amarok's GUI). I've been searching for a fix to this problem but so far I have found nothing. If anyone can help us out that would be greatly appreciated. 

Thanks,
-Tipsqueal.

---

### Post by tipsqueal on 2007-09-20
I just found a solution on this thread:

[http://ubuntuforums.org/showthread.php?t=457059&highlight=Media+Keys](http://ubuntuforums.org/showthread.php?t=457059&highlight=Media+Keys)

Basically what you have to do is open of the gconf-editor then add in the key for a command under the "global_keybindings" section (I used command 9), then enter in an action for the command under the "keybinding_commands" section (I entered "exaille"). If you need to find what the key is go to system-preferences-keyboard shortcuts then set the key to something and it will tell you what the key is (mine was 0x81) then disable it after you know what the key is.

Another note to make: I cannot get it to work when Compiz Fusion is running. There doesn't seem to be a way to set a custom button for key bindings it seems to lock you into the standard keys on the keyboard or key combinations. There is a setting to make a key binding for command 9 but no way to put in the custom media key I'm using. There's probably a text file I can edit to fix this, but I gotta find it. I will edit this or make a new post if I find a solution to this. 

Hope I helped,
Tipsqueal.

---

