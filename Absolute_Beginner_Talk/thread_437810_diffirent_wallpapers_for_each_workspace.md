---
title: "diffirent wallpapers for each workspace ?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Nic- on 2007-05-09
i'm using feisty + beryl , when i change desktop wallpaper , all my workspace change to that wallpaer, how can i use diffirent wallpapers for each workspace.

thank you:)

---

### Post by ikonia on 2007-05-09
its a long time request from gnome.

Log a bug for it to get focus on it in the gnome project.

---

### Post by starcraft.man on 2007-05-09
Ya, I believe ya can do a different one for each with KDE, but with gnome the workspaces just get cloned. Oh well, I like my one wallpaper anyhow.

---

### Post by javierfh on 2007-05-09
Hello,
I have obviously same situation, since seems to be a gnome "feature", but what bothers me, is that in the 4 little icons in the bottom bar(representing the workspaces) i can only see the windows i have in the first one (represented by small white rectangles, like the open windows)
I can move things to these workspaces, and if i move with control- alt - left/right arrow or mouse movement, things are there... but if i go directly accessing one of the four icons in the lower right corner and click one of them...it opens a empty workspace.
Has anyone noticed similar behaviour?

Also i dont know if it is normal or not..the bar with the open applications it is common to all workspaces, is that what it is supposed to happen?

Hope anyone has some comment about it.

Javi

---

### Post by Robynsveil on 2007-05-09
> **javierfh said:**
> Hello,
I have obviously same situation, since seems to be a gnome "feature", but what bothers me, is that in the 4 little icons in the bottom bar(representing the workspaces) i can only see the windows i have in the first one (represented by small white rectangles, like the open windows)
I can move things to these workspaces, and if i move with control- alt - left/right arrow or mouse movement, things are there... but if i go directly accessing one of the four icons in the lower right corner and click one of them...it opens a empty workspace.
Has anyone noticed similar behaviour?

Also i dont know if it is normal or not..the bar with the open applications it is common to all workspaces, is that what it is supposed to happen?

Hope anyone has some comment about it.

Javi
I have exactly the same problem - someone said something about making some change in a setting in Beryl, but I couldn't figure out how to set it... the option as it was described didn't exist... or at least, I couldn't find it, and anyway, at the time I had bigger fish to fry..

---

### Post by Nic- on 2007-05-09
try :
beryl setting manager ---> general options  ---> desktop background ----> make sure uncheck Desktop manager supports viewports

hope this help

---

### Post by javierfh on 2007-05-09
> **Nic- said:**
> try :
beryl setting manager ---> general options  ---> desktop background ----> make sure uncheck Desktop manager supports viewports

hope this help

This doesnt work.. i still get same behaviour.
I think i have two issues here, out of which one im not sure if it is such.

1. No little rectangles in other workspaces, representing the open windows in these other workspaces. 
And related to same thing probably the fact that if i move with the control alt and direction keys, the cube rotates and i can see what it is in other workspaces, but if i click directly with the mouse in one of the workspaces representations, goes to an empty one.

2. No matter in what workspace i am, it shows (down in the application bar) all the open windows that i have. Thats the one i dont know if it should be some other way. I would expect that in every workspace shows only the ones open in that workspace. 

I hope someone can give some tips :)

Thanks in advance.

Javi

---

### Post by Inxsible on 2007-05-09
When I am in the process of rotating the cube, I see only the applications that were open in the workspace I started "rotating" from. But once i stop rotating and go to a different workspace, I see only the apps open in THAT particular workspace.
 
It would be nice if the bottom panel would show the apps in each workspace so I know where to stop rotating to go into a particular application that I have open on another workspace.
 
I don't think its correct behavior.....but then again I don't wanna nit-pick

---

### Post by Nythain on 2007-05-09
not sure if this info is helpfull...
the multiple viewports (sides of cube, desktops, whatever) that beryl/compiz uses arent all of the workspaces/desktops  in your windows manager (metacity, kwin, aquamarine, etc).
What beryl does, is takes  the desktop you are  on when you start it (or the first desktop if you have it auto start when you log in) and clone that so many times into viewports.

now... after popular demand, a while ago, in the svn repo/release then included a plugin allowing for different wallpaper on each viewport
 [http://wiki.beryl-project.org/wiki/Wallpaper_Manager](http://wiki.beryl-project.org/wiki/Wallpaper_Manager)
not sure how outdate that info is since i stopped running beryl about 6 months ago.

as for the desktop monitor workspace shower app you have in your panel... if you use beryl regularly enough, just turn off all desktops but one in your windows manager and use beryls viewports instead... 

its early and im now starting to confuse myself so ill leave it there

---

### Post by Inxsible on 2007-05-09
Nythain,
 
I do have 4 workspaces enabled because I thought I would need it for the "cube". So I will try and change that tonight to see if it works.
 
 
Thanks !

---

### Post by Nythain on 2007-05-09
beryl has its own setting for cube sides
the option is called "Horizontal Virtual Size" in "General Options" (of the "Beryl Settings Manager").
its completely independent of gnome(metacity) workspaces or kde(kwin) desktops... other than the fact that it clones one so many times into different viewports

---

