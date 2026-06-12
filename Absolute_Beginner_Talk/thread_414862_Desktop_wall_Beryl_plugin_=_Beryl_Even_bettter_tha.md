---
title: "Desktop wall Beryl plugin = Beryl Even bettter than before"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-04-20
Hi all, i very interesting in having the latest beryl plugins!
I currently use 0.2.0 in KDE but there are some fantastic plugins out lately
especially the desktop wall etc that make beryl even better :
[http://youtube.com/watch?v=6TM7N6JKEvw](http://youtube.com/watch?v=6TM7N6JKEvw)

as i said i have 0.2.0 i think u can have them with version 0.2.1 only (?)
So do I need the repo for 0.2.1?and what that should be?
can anyone help, how to do this? 
many thaks

---

### Post by luctor on 2007-04-26
beryl-plugins-unsupported has the wall plugin

---

### Post by Rinzwind on 2007-04-26
Wow that's cool

*bookmarks*

---

### Post by Rashid584 on 2007-04-30
I have beryl-plugins-unsupported installed and the wall plugin doesn't appear in beryl-settings under Desktop (which is where I assume it should be) or anywhere else in fact.

:S

-Rashid

---

### Post by starcraft.man on 2007-04-30
I am pretty sure from all that I read that 0.21 made only minor changes to Beryl, mostly due to licensing and other documentation issues. Thats why the repos haven't really felt any compelling reason to upgrade to the latest version.

This wall plugin I am not sure but I think it is the Desktop Plane plugin that is renamed... its under Beryl Settings Manager > Desktop > Desktop Plane. I believe there are incompatibilities with Desktop Cube, turn OFF Cube first before turning this off. Anything you do is your responsibility, especially since plane is an unsupported plugin. If its not that, I dunno... go to beryl-project and try to find it yourself, if its experimental and not in repos theres a reason its likely unstable. Desktop cube is proven, I'd stick with it.

Edit: I searched beryl project and google, I don't know where this plugin is but basically it seems like a hack that simply adds more features to plane. It is likely still under development.

---

### Post by Rashid584 on 2007-04-30
Tried the plane plugin and its pretty lame...the hack looks really cool. Hopefully the new wall thing will be compatible with the cube 

-Rashid

---

### Post by 71CH on 2007-04-30
so it this an alternative to the cube or is it something completely different?

---

### Post by starcraft.man on 2007-04-30
The wall plugin from what I've seen is a replacement/hack for the plane option in the Desktop tab of the manager. It must be beta, I don't see it in the repos or download tarballs on beryl project.

---

### Post by crimesaucer on 2007-04-30
This is sort of off topic, but I thought I'd share some Beryl settings that I'm currently using.

For some reason when I upgraded to Feisty, (and had to re-install Beryl from the Feisty repos because I had been using the Beryl svn from Treviño's Beryl-SVN Ubuntu Repository) I had a strange "buggy" effect going on with my cube and the 3D windows effect.

So I turned the 3D plug-in off and the problem went away. 

Next, I realized that I had been using the same effects and settings since January and maybe it was time to try something new.

I turned off my cube and tried to enable my Desktop Wall plug-in. Well, that crashed my system so I turned my cube back on because I didn't really want to use the Desktop Wall plug-in anyway.

Then I tried messing around with all of my settings and came up with something cool.

This is what I did: 

I went in to Desktop-->--Rotate Cube-->--Misc. Options and turned my settings for Acceleration and Rotation Speed to the highest settings of 20 and 50, and Auto Timestep to: 1.0000 then Manual Timestep to: 5.0000

then...in Rotation Cube-->--Behavior, I turned the: Mouse Wheel Scrolls for Rotation to 1 and the Flip Time to 0.

Now you can flip super fast through your 4 desktops with the mouse or ctrl + alt + arrow, and it doesn't waist time showing the cube. It's so fast, and then if you want to see your cube or skydome wallpaper all you have to do is ctrl + alt +right click mouse.

Then I made it even better with General Options-->--Shortcuts-->--Screen Edges: and what I did was to enable them like this:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-47-5.png[/IMG]

Now since I have the Scale plug-in, I can put the mouse arrow in either the top right corner or the top middle and choose between all open apps on either all 4 desktops, or just one desktop, and the top left corner turns them all to hidden.

Then the left side and right side rotate the cube super fast to the next desktop workspace, and the bottom left corner and the bottom right corner will take the current app to the next desktop workspace . 

I was sort of bored with the cube and this is so much faster then the way I had the settings before. And it feels very stable, so I just thought I would share.

---

### Post by Rashid584 on 2007-05-01
That was very helpful to me, but completely not for the reasons you wrote it :P

Actually, it was because I'd been looking for how to configure edges for beryl and couldn't, for the life of me, find it anywhere. Thanks to your post I have :D

I actually use the top left, top right, and bottom left corners for things (mac-style menu, logout button and suse-menu respectively) so only the bottom right is configured for initiate scale.

-Rashid

---

### Post by starcraft.man on 2007-05-01
Ubuntu Forums at its best, supplying quality help with a smile even when not intended at all :p

Might be a good slogan :D

---

### Post by Rashid584 on 2007-05-01
> **starcraft.man said:**
> Ubuntu Forums at its best, supplying quality help with a smile even when not intended at all :p

Might be a good slogan :D

:D

-Rashid

---

### Post by crimesaucer on 2007-05-01
> **Rashid584 said:**
> That was very helpful to me, but completely not for the reasons you wrote it :P

Actually, it was because I'd been looking for how to configure edges for beryl and couldn't, for the life of me, find it anywhere. Thanks to your post I have :D

I actually use the top left, top right, and bottom left corners for things (mac-style menu, logout button and suse-menu respectively) so only the bottom right is configured for initiate scale.

-Rashid

Cool, I'm glad I helped a little Rashid and if you have any other questions I always like to help. 

With those other settings (all of the cube rotations makes it slower), my Beryl becomes like the way my original xubuntu was when it could easily switch workspaces with the pager or a mouse scroll.

The cube still is viewable with my skydome art, all that is pressed is the ctrl + alt + left click. 

And now instead of using the ctrl + alt + arrow, a simple mouse stroke to the side and you have a new workspace, or 4 different workspaces.

---

