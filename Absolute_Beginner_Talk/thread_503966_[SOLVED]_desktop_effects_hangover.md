---
title: "[SOLVED] desktop effects hangover"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by yeastpuppet on 2007-07-18
I started with a fresh install of Ubuntu Feisty and everything worked well.  

A few days ago I enabled desktop effects from the menu and everything still worked well. 

After the wobbly windows finally got on my nerves, I disabled desktop effects and that's where things got goofy.

My apps on the top bar shift around between sessions, at times one or two will completely disappear although they are easily re-installed.  Come to think of it my terminal icon disappeared during a session last night without any actions being taken by me except to switch from one workspace to another.  

At the bottom right sometimes I'll have 2 workspaces, sometimes 4 workspaces.  My windows now open by literally springing from the bottom of the page almost like a cartoon character.

When asked for my password, my screen used to cleanly fade to the "shadow look" now it darkens in three distinct steps.  

I assume that my desktop (Ubuntu) manager has somehow become corrupted.  

Is there some way to "remove" my current manager and re-install a non-corrupt manager without overwriting anything else?

Thanks - Phil

---

### Post by ihristov on 2007-07-19
I used "Desktop effects" myself for a while and then disabled them and have not suffered from the problems you are having.

2 suggestions:

1) Go into the "Desktop effects" setting dialog and turn them on and off again. Maybe you think you turned them off but you didn't really. One bad problem there is that they do not show the status correctly when they are turned on.

2) Maybe you can find out in Synaptic where are the configuration files for these "Desktop effects" stuff. I suspect if you delete them it should back to normal. I suspect they might be somewhere in the ~/.gnome2/ folder. I guess the easiest thing to do to test this is to create a new user and login as that new user. See if the problem is still there for the new user.

---

### Post by yeastpuppet on 2007-07-21
Thanks! You were right about the desktop effects "appearing" to be off while they were still on.

Still waiting for computers to make my life easier and more productive!

Phil

---

