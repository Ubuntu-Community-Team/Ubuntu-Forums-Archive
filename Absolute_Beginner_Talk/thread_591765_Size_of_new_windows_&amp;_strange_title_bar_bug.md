---
title: "Size of new windows &amp; strange title bar bug?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Trebaruna on 2007-10-25
Even after quite some usage I still run into basic problems...

Anyway, these two have been bothering me for some time now:

Quite often when I open new windows (mostly Synaptic and Nautilus? not sure, still testing) the window will be roughly the size of a maximised one, but will in fact be a window. So, I can't just move it around without first resizing it. What's more, the right border sticks out a bit from the workspace, so the window is visible and in the taskbar in the next workspace to the right. This is confusing and annoying.
Resizing and closing the window helps for the next time that I open it, but it seems to be back to its annoying state after a reboot or something alike.
Am I missing some obious setting to fix this? I don't think I've done something that would affect the drawing of new windows...
7.04 did it (running metacity) and now 7.10 does it too, with compiz (somewhat tweaked using the compizconfig settings manager).

Also, sometimes the titlebar of a window turns grey-ish, the same color as the main toolbaer, and the title itself disappears and most of the close-maximize-minimize buttons get a bit silly. I am not sure exactly how to trigger it, but I think it happens when the title of the window gets updated.
Again, it has been doing that in 7.04, and it persists in 7.10.
And also, for this one I don't see what I might have done... :(

For both of these: I have a 7800GTX videocard and use the restricted drivers provided by Ubuntu. The only changes I've made to xorg.conf is to remove the unused wacom stuff and tweak the mouse section to make the forward-back buttons work.

I hope anyone can untangle this post and give me some helpful advice :) Thanks in advance!

---

### Post by Trebaruna on 2007-10-28
bump?

---

### Post by gwhitener on 2007-10-28
I am having sort of the same issues.  Now, all my titlebars have lost all functionality from the top right corner of the windows.

So far, I don't have an answer either...

---

### Post by treris on 2007-10-29
Same here, on both accounts, my windows sometimes seem to stick out to the right and the window border will change color and loose the actual title,

All in all its not terribly annoying, but it does irk sometimes

---

### Post by mdpalow on 2007-10-29
I have the same problem with Title Bar Bug.

I posted a similar question and got a reply you can view at:

[http://ubuntuforums.org/showthread.php?t=55286&page=2](http://ubuntuforums.org/showthread.php?t=55286&page=2)

LOOK FOR POST NUMBER 20 in this thread.

I just don't know what I'm supposed to do with this little script. If you find out, pls Private Message me the answer.

Thanks in advance...

---

### Post by Inxsible on 2007-10-29
I have both the above mentioned problems too. I don't care much about the window being a bit bigger. I simply maximize it.

But the title bar becoming gray is annoying.

---

### Post by treris on 2007-10-30
That thread seems to be about wine applications not regular gtk applications, so I don't suppose the script will do me much good

---

### Post by khurrum1990 on 2007-10-30
Hi, this is actually a bug in Ubuntu and the Nvidia drivers, the problem existed in Ubuntu 7.04 and carried over to 7.10. Try using emerald window manager and the problem will go away so its actually a metacity bug. I hope I helped and u can install emerald window manager by typing:
sudo apt-get install emerald
You can download ubuntu themese for fiesty fawn which work on gutsy by searching on yahoo for ubuntu emerald themes.

---

### Post by CoolDreamZ on 2007-10-30
emerald does not seem to reliably fix the problem, especially not on dual-head systems. See this post:

[http://ubuntuforums.org/showthread.php?t=566765]("http://ubuntuforums.org/showthread.php?t=566765")

Do you have any more information on the bug?

---

### Post by treris on 2007-10-30
The trick described here:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

seems to have done it for me!

(just scroll to 'Troubleshooting' for the instructions)

Hope that it works for you as much as it did for me!

---

### Post by treris on 2007-11-01
Contrary to my earlier statements, it's still not fixed, it's just less frequent unfortunately.......

---

### Post by positroniks on 2007-11-15
I've been having this problem (greyed out titlebar, missing title text, disappearing window widgets) myself in default Gutsy using the Glossy theme with Compiz-Fusion effects enabled. I've been using Ubuntu for almost 2 weeks now and it's been a constant annoyance. :( 

Mostly in Firefox, but other apps as well. I've noticed it only seems to happen in maximized windows, especially when hovering the mouse pointer around near window widgets, and when opening links in new Firefox tabs. Things will reappear if I hover the mouse pointer over where the window widgets should be. I've tried some of the fixes found in this thread and in others, but it hasn't worked out yet. Hope this info might help some of you 'oldbies' to point us newbies in the right direction for a fix.

---

### Post by Incredulous Moose on 2008-02-01
This is kind of a mini thread jack but it might be relevant and it isn't a problem enough to create a whole new thread.

Every time I start my PC the titlebar alternates between a normal size and tiny. Does anyone know why that might be? 

I'm running Gutsy. Monitor - Acer P193w with the resolution set to 1280x800. GeForce 6600.

---

### Post by yaztromo on 2008-02-04
> **Trebaruna said:**
> 
Quite often when I open new windows (mostly Synaptic and Nautilus? not sure, still testing) the window will be roughly the size of a maximised one, but will in fact be a window. So, I can't just move it around without first resizing it. What's more, the right border sticks out a bit from the workspace, so the window is visible and in the taskbar in the next workspace to the right. This is confusing and annoying.
Resizing and closing the window helps for the next time that I open it, but it seems to be back to its annoying state after a reboot or something alike.
Am I missing some obious setting to fix this? I don't think I've done something that would affect the drawing of new windows...
7.04 did it (running metacity) and now 7.10 does it too, with compiz (somewhat tweaked using the compizconfig settings manager).

Bug is in launchpad [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156055](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156055)

> Also, sometimes the titlebar of a window turns grey-ish, the same color as the main toolbaer, and the title itself disappears and most of the close-maximize-minimize buttons get a bit silly. I am not sure exactly how to trigger it, but I think it happens when the title of the window gets updated.
Again, it has been doing that in 7.04, and it persists in 7.10.
And also, for this one I don't see what I might have done... :(

This one is also in launchpad, quite a showstopper [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508)

---

### Post by forumkiller on 2008-04-22
> **treris said:**
> The trick described here:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

seems to have done it for me!

(just scroll to 'Troubleshooting' for the instructions)

Hope that it works for you as much as it did for me!

i typed that into terminal but how do i restart X?

---

### Post by enchantedsky on 2008-04-22
I have the title bar bug as well, and I'm running Compiz-Fusion. The only program it affects is OpenOffice.......it's ironic, but it IS fixed in Firefox 3.0 Beta 5.

I started another thread about it, but received no replies. I believe it is a bug in Compiz-Fusion, where the Workaround plugin should fix all Window problems, but does not properly fix Open Offices window bar from disappearing as you move your mouse over minimize/maximize widgets on the upper right of the window.

Will this be fixed soon?

---

### Post by forumkiller on 2008-04-22
> **enchantedsky said:**
> I have the title bar bug as well, and I'm running Compiz-Fusion. The only program it affects is OpenOffice.......it's ironic, but it IS fixed in Firefox 3.0 Beta 5.

I started another thread about it, but received no replies. I believe it is a bug in Compiz-Fusion, where the Workaround plugin should fix all Window problems, but does not properly fix Open Offices window bar from disappearing as you move your mouse over minimize/maximize widgets on the upper right of the window.

Will this be fixed soon?

yeh i don't understand why this hasn't been fixed. It seems to be the biggest problem out there, and yet there are many ways to fix it. I have already fixed this twice before and still have no lasting solution. Hopefully in the next ubuntu update it will be solved. Either that or i'm gonna have to move to Fedora or something, i only use this OS for fun anyway lol

---

