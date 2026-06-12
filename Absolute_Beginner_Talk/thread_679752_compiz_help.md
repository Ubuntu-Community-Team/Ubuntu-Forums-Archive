---
title: "compiz help"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Jet8225 on 2008-01-27
I just recently started using compiz and I enabled the desktop cube, but instead of having the whole cube I only have one panel in the back and the front, not even the cube. I guessed that it must be because I don't have 3D enabled or some other problem. Does anyone know what might be the cause of this, or how to enable 3D? By the way, my video card is NVIDIA GeForce Go 6150.

---

### Post by Ub1476 on 2008-01-27
Open Advance Desktop Effects>General Settings>Desktop Size> Set it from 2 to 4.

---

### Post by Jet8225 on 2008-01-27
Thanks a lot. I'm still seeing only two desktops..

---

### Post by ronmarley1 on 2008-01-27
> **Jet8225 said:**
> Thanks a lot. I'm still seeing only two desktops..

The above suggestion should've worked.  Try right clicking on the Workspace Switcher and then clicking Preferences.  Change number of columns from 2 to 4.

---

### Post by Jet8225 on 2008-01-27
I did, that but I'm still getting the same 2 workspaces.

---

### Post by Therion on 2008-01-27
The setting for the cube is **Horizontal Virtual Size** -- not "Number of Desktops".  

Your settings need match the ones in [this picture]("http://blogage.de/files/866/image?cube-settings.png").

---

### Post by Jet8225 on 2008-01-27
It still hasn't done anything new....

---

### Post by Therion on 2008-01-27
Do you have the **Rotate Cube** plugin enabled?

---

### Post by Jet8225 on 2008-01-27
Yes.

---

### Post by Therion on 2008-01-27
Not sure what to tell you then...  If you press Ctrl+Alt while holding down the left mouse button and moving the mouse around, do you see the cube or what?  What happens when you do that combination, is what I'm asking.  

If still no joy, I'm sorry but I'm out of suggestions.

---

### Post by Jet8225 on 2008-01-27
No cube, It's like a piece of paper with the two workplaces on different sides...

---

### Post by Jet8225 on 2008-01-27
bump?

---

### Post by evilc on 2008-01-27
Are you sure you have done what Therion suggested? Make sure it shows 4, I have seen this change back for no reason on it's own.

---

### Post by Jet8225 on 2008-01-27
It is exactly as he told me to put it like. I think it might not appear because I put my graphics to 2D or something. I don't remember too much about that.

---

### Post by jryprt on 2008-01-27
[Forlong's Guide](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)

---

### Post by Jet8225 on 2008-01-27
Thanks but that isn't working either...

---

### Post by Therion on 2008-01-27
> **Jet8225 said:**
> It is exactly as he told me to put it like. I think it might not appear because I put my graphics to 2D or something. I don't remember too much about that.
Well, that's a problem then.  You definitely need to have 3D acceleration enabled.

The first step is to find out whether 3D acceleration is enabled.  To find out if it is or not enter this in a terminal: 
```
glxinfo | grep rendering
```

If 3D acceleration is working, the following will be displayed:
```
direct rendering: Yes
```

---

### Post by Jet8225 on 2008-01-27
apparently it's working.

---

### Post by Jet8225 on 2008-01-27
Thanks to all of those who helped me. I just had to restart the computer.

---

