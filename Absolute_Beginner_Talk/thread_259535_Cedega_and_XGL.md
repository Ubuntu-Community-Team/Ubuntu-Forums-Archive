---
title: "Cedega and XGL"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-09-17
Hi, this is my third Ubuntu reformat in 3 days (I wont blame Ubuntu for that, but myself.) but noticed some things stopping to work at the same time i installed other things, and by this i'm talking about Steam (Cedega) + XGL;

At about the same time I (successfully) installed XGL, Steam no longer worked, with wine or cedega. I would run it but nothing would happen, can XGL break either Steam or Wine or Cedega?

And if not, will it affect my Counter-Strike 1.6 performance (I reckon both XGL and CS use OpenGL) but you can easily switch from the Compiz Window Manager to the Gnome one when Cedega is installed, if I would switch to the non-xompiz window manager, would counter-strike not be affected by XGL because it is off?


In other note, I am a 100% Ubuntu user now, I tried partitioning my Hard Drive with the Ubuntu installer but it simply corrupted everything, it's amazing how much you learn when you have no Windows to cower back to. :lol: 

Thank you.

---

### Post by Perfect Storm on 2006-09-17
As you well know that XGL is still alpha software and still can give headache ;)

Back to the topic check this hack it might help: [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

---

### Post by Albi on 2006-09-17
It's because XGL uses accelerated graphics, meaning that Cedega can't really do much.

You have to log onto a gnome session for it to work properly (without XGL). 

You do this by logging out--->options--->sessions--->gnome (or failsafe gnome if u didn't make a seperate session for xgl).

If you have an Nvidia card, there was also a guide to fixing this.

---

### Post by alex-desktop79 on 2006-09-17
Read that already, but if it breaks my steam, I cant even get that far so I still need to know if it does that or not.
As for the command, how would one make it work with steam?

nonXgl cedega ~/drive_c/program files/steam/steam.exe -applaunch 10

hows that?
> there was also a guide to fixing this.
link? :)

Thanks for the quick replies!

---

### Post by Albi on 2006-09-17
not sure, but i think just "nonxgl cedega" and running the game using the gui should work as well.

i just quickly switch to a non-xgl session though, it's much easier

Edit: the guide was here [http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

---

### Post by alex-desktop79 on 2006-09-17
How would I make xgl a seperate session?

---

### Post by Albi on 2006-09-17
Well I did it using the Wiki guide, you should probably check to see if it is a seperate session or not first though.

[https://wiki.ubuntu.com/CompositeManager/Xgl?highlight=%28xgl%29](https://wiki.ubuntu.com/CompositeManager/Xgl?highlight=%28xgl%29)

---

### Post by alex-desktop79 on 2006-09-17
Thanks! :D

---

