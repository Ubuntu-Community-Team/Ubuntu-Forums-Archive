---
title: "Bare Frame when moving a window"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Bloch on 2006-04-19
I''m using a pentium III 800MHz. 
When I move a window it leaves a stepped track after it. Is there an option to make the windows become a frame when being moved or resized?
I think it would look better than having those ghostly lingering edges.

It might also make my system run better,

---

### Post by stuporglue on 2006-04-19
The easiest way is probably to open gconf-editor (from terminal, or the menu). 

In gconf-editor, navigate to /apps/metacity/general and hit the checkbox "reduced_resources"

The info on reduced_resources says

> If true, metacity will give the user less feedback and less sense of "direct manipulation", by using wireframes, avoiding animations, or other means. This is a significant reduction in usability for many users, but may allow legacy applications and terminal servers to function when they would otherwise be impractical. However, the wireframe feature is disabled when accessibility is on to avoid weird desktop breakages. 

I think you can disable specific features individually somewhere too, but I don't see it at the moment.

---

### Post by Mustard on 2006-04-19
You might also want to look into using a lighter desktop environment, like xfce.  It's fairly easy to install xfce using apt-get, as it is referred to by a metapackage called xubuntu-desktop.

---

### Post by Bloch on 2006-04-20
Thanks for that tip stuporglue on how to make windows turn into a frame when moving. I used to use wireframes on windows when on a low resource system, and I was wondering why there was no similar option on ubuntu/gnome.
I have not seen it anywhere recommended for people with low-quality systems, and even the description you quote is odd - should he not say "legacy systems" rather than "legacy applications"? Nowhere does it say it will improve performance.
However I have it working and it is definitely less annoying.

Applications --> System Tools --> Configuration Editor is where it is, though to start it at the terminal it is gconf-editor.

By the way mustard, I'm actually doing it on a friend's computer. He wants the same system as I have on my computer, and to be honest, he doesn't know what a file manager is, or a desktop environment etc. Changing desktop wallpaper is about the height of his configuration ;)  I don't want to scare him away.

---

### Post by stuporglue on 2006-04-20
> Thanks for that tip stuporglue on how to make windows turn into a frame when moving. I used to use wireframes on windows when on a low resource system, and I was wondering why there was no similar option on ubuntu/gnome.

I've found that with Linux, the option is almost always there. It's often just hidden...in the worst case, it's hidden as a flag that needs to be set at compile time. 

> I have not seen it anywhere recommended for people with low-quality systems, and even the description you quote is odd - should he not say "legacy systems" rather than "legacy applications"? Nowhere does it say it will improve performance. However I have it working and it is definitely less annoying.

Yeah, that is interesting. Maybe some legacy apps don't handle having their screens redrawn when they're being moved? I've only been on Linux since 2003, so I can't really comment on "legacy apps".

---

