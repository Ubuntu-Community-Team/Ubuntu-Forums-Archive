---
title: "Update broke my compliz"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by toasted on 2006-09-04
I installed with the second method on this page:

[http://www.ubuntuforums.org/showthread.php?t=245152](http://www.ubuntuforums.org/showthread.php?t=245152)

It has been working good until this mornings updates. There were a few updates regarding themes, compliz, etc. Now when I log in a compliz session and open a window, the window is stuck at top left of screen, has no top bar, and cannot be moved. The system runs really slow too. Thats about as far as I got in diagnosis other than rebooting a few times.

I have the option to boot into a normal Gnome session as that is the install method I choose. Good thing!

So, what should I do to try to correct this?
Can I remove this mornings updates somehow?

---

### Post by Dinerty on 2006-09-04
[http://www.ubuntuforums.org/showthread.php?t=250444](http://www.ubuntuforums.org/showthread.php?t=250444)

Try my guide at the bottom, csm is being used instead of gconf-editor

---

### Post by toasted on 2006-09-04
Thanks for the info. It seems to be working so far, now I just have to figure out how to configure it all again.

Ya know, this is just rude of whomever does the releases to break peoples machines with no warning. Obviously in this case it was apparent that this would happen. 

They could have let us know not to update till a convenient time or something... they could have done something!!!!

Its like I had nothing better to do this morning then screw with this for hours before I could get anything done. I really dont mind the work, its fun actually, its just the indifference that seems to exist with these people that are doing the releases......

---

### Post by toasted on 2006-09-04
Ok looks like i'm back to normal now. Thanks again for your help!!

So, I still have the icon to configure compliz - the red one on top panel. Looks like this will no longer be functional right? How would we get rid of it I wonder?

---

### Post by toasted on 2006-09-04
Got it, its simple really
In Sessions/Startup Programs simply disable the compiz-tray-icon

Clicking that gl desktop now breaks your running session and the rest of it does nothing. No reason to have it.

---

### Post by Dinerty on 2006-09-04
Glad to see everything is ok, I think if we had of checked the description of the update we could have prevented it effecting us so bad :)

---

### Post by toasted on 2006-09-04
Well I did read, and saw things about compliz updates. There were quite a few updates this time. Maybe there was more there than I read, but with the troubles of last week I took more notice than I used to. I am surprised there arent more posts..... everybody must be sleeping still!!  LOL

There should be a sticky......

---

### Post by Dinerty on 2006-09-04
There are quite a few threads in General support section:

[http://www.ubuntuforums.org/showthread.php?t=250444](http://www.ubuntuforums.org/showthread.php?t=250444)

&

[http://www.ubuntuforums.org/showthread.php?t=250449](http://www.ubuntuforums.org/showthread.php?t=250449)

& finally

[http://www.ubuntuforums.org/showthread.php?t=250489](http://www.ubuntuforums.org/showthread.php?t=250489)

Least we all learnt for next time to read all possible xgl updates :D

---

### Post by stontyro on 2006-09-04
> **Dinerty said:**
> Glad to see everything is ok, I think if we had of checked the description of the update we could have prevented it effecting us so bad :)

I don't think you were being sarcastic enough.  Here are the descriptions from the csm package:

Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>

---

### Post by toasted on 2006-09-04
With the command 'compliz-start' it starts up just fine.
What about stopping it? 
I tried end, quit, stop, terminate, exit, pause
None of them do anything

---

### Post by toasted on 2006-09-04
So far I found that compiz --replace does stop compize but it doesnt work correctly. Should it be more- 

compliz --replace -something 

?

---

### Post by Marsan on 2006-09-04
I had the same problem too this morning. Updated the CMS package with the compiz-packages. Im used to that compiz is releasing new versons and upgrades all the time so i didnt think more of it. Untill i restarted. No windowmanager was loaded, no minimize,close button :( And my keyboard didnt work either because of this new update, just in login. 

What i did was simply to uninstall all the compiz-packages and install them again. That did the trick, but now my plugin-configurations for compiz dont work :( 

If anyone have a better sollution i would be happy :D

---

