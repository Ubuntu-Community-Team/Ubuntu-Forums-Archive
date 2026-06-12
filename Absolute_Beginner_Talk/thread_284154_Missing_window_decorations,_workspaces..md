---
title: "Missing window decorations, workspaces."
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Seine on 2006-10-25
I had Beryl 0.11 and Xgl working one day and, no idea what I did next, now I have serious issues with the windowed environment.

All of my windows are without edges ... the title bars, menus, window controls are all gone on all windows. They are all docked in the top left by default and I can't move them.

I also have no access to the other workspaces.

If I load without Beryl/Xgl then all works OK. So that's great. After realising I can't fix whatever it is I've broken I tried a complete uninstall of Beryl. After re-installing the problems continue.

Can someone please help me troubleshoot this? I'm at a loss.

---

### Post by simone.brunozzi on 2006-10-25
> **Seine said:**
> I had Beryl 0.11 and Xgl working one day and, no idea what I did next, now I have serious issues with the windowed environment.

All of my windows are without edges ... the title bars, menus, window controls are all gone on all windows. They are all docked in the top left by default and I can't move them.

I also have no access to the other workspaces.

If I load without Beryl/Xgl then all works OK. So that's great. After realising I can't fix whatever it is I've broken I tried a complete uninstall of Beryl. After re-installing the problems continue.

Can someone please help me troubleshoot this? I'm at a loss.

If you look at the *official* guide, there are lots of personalizations.
Maybe you can fix it with that.
Cheers,

---

### Post by Dr. Nick on 2006-10-25
You can run **metacity --replace **to get metacity back over beryl without having to log off/on. 

I would make sure that any old packages and startup scripts used in the past for beryl are gone then try a reinstall of beryl again.

---

### Post by Seine on 2006-10-28
Thanks for your advice guys. It's really appreciated.

I took the opportunity to upgrade to Edgy before trying to fix this again. I guess I was hoping the process would refresh the packages. However after following the guide at [http://www.ubuntuforums.org/showthread.php?t=263851&highlight=edgy+beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=edgy+beryl) it's still broken.

I'd like to try removing old packages, as you suggest Dr Nick, but I'm not sure how.

I'd also like to restore my .Xsession file, as I suspect this may have some bearing on my problem. It currently reads:
```
#!/bin/sh
gnome-window-decorator &
exec gnome-session
```

Can I get some further advice please? Thanks!
Seine

---

### Post by Seine on 2006-10-29
I truly hope I can get some help from the wonderful people here. There are rude people on the Beryl forums.

---

### Post by Dr. Nick on 2006-10-29
I dont know alot about the .Xsession file, but yours looks good. I would search in synaptic for anything named beryl or compiz or xgl and then remove it. I would then look under the System - Prefrences - sessions dialog and check for anything beeryl/compiz in the startup tab.

I looked at my xsesion file and it mentioned stuff about kde when I dont even have kde installed so I am not sure what its problem is.

You used to have to download a custom script to start beryl, that is no longer needed, but you may have it left over on your system. 

My advice would be to also search for the howto you used origionally to set it up, and use that as a guide to undo it.

If that gives you any leads then post back with the results, and remember

metacity --replace

will load the default window manager restoring some titlebars.

---

### Post by Seine on 2006-10-29
Thank you Dr Nick. I shall post back when I get home and have a chance to follow your advice.

Already metacity --replace has helped me a great deal. Thanks for that tip. ;) 

Seine

---

### Post by Dr. Nick on 2006-10-29
Good luck, The thing with beryl is its still very much beta, and alot of getting it to run consisted of "hacks" That is getting better now, but I realized I had a lot of hacked stuff laying around from old versions like custom start scripts, I was surprised when I was able to upgrade it without much issue.

It may just be a matter of cleaning the old up.

Also you may make sure you are booting into the "gnome" session from the login screen and not some custom session


EDIT

I used this tutorial in the end to get mine running
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by Seti on 2006-11-16
In other words, nobody knows how to fix this issue. I have the same problem; no title-bars, window borders, etc.

---

### Post by TorenC on 2006-11-16
I have missing window decorations in my beryl sometimes. I can usually fix it by choosing 'reload decorations manager' in the right click menu off of the little beryl tray icon, or by running:
sudo killall emerald && emerald --replace &
in a terminal. don't leave out the &'s.

---

### Post by Seine on 2006-11-16
Apologies for not replying sooner, but I have not yet attempted to fix this (work+wife severely stifles my time to tinker!)

I have disabled Beryl for now in order to remain productive. A part of me is hoping the next release will automagically fix my issue.

---

### Post by TheRingmaster on 2006-11-16
> **Seine said:**
> I had Beryl 0.11 and Xgl working one day and, no idea what I did next, now I have serious issues with the windowed environment.

All of my windows are without edges ... the title bars, menus, window controls are all gone on all windows. They are all docked in the top left by default and I can't move them.

I also have no access to the other workspaces.

If I load without Beryl/Xgl then all works OK. So that's great. After realising I can't fix whatever it is I've broken I tried a complete uninstall of Beryl. After re-installing the problems continue.

Can someone please help me troubleshoot this? I'm at a loss.
It does that sometimes. You can just right-click on the tab at the bottom and choose move. that should help

---

### Post by viz_e on 2006-11-17
Same problem here: beryl was working fine for a couple of days, but now I have lost the window decorations and some options in the beryl-manager are grayed out. No idea why, since I haven't touched the configuration since the last successful start.

---

### Post by Seine on 2006-11-17
Working through this issue and found the following:

[INDENT]If window borders and decorations are not showing up, try changing DefaultDepth to 24 in the Screen section

Window borders and decorations also won't show up, when you disabled the use of desktop-icons on your desktop. Reenable them... [/INDENT]
From [Install/Ubuntu/Edgy/nVIDIA]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA")

That may help some of you.

---

### Post by 5h4rk on 2006-11-17
Does it work? Cuz with Beryl I got only 1 workspace :(

How to fix it?

---

### Post by Seine on 2006-11-18
No, that didn't work for me. I was already using 24bit colour.

---

### Post by Seine on 2006-11-18
I took Dr Nick's advice and all is well. Here's my experience.

[LIST=1]
[*]Did a complete removal of beryl, xgl and compiz packages
[*]Installed as per the Beryl wiki for Edgy+nvidia
[*]My machine freaked out. Fan went into overdrive, window decorations disappeared and computer locked up
[*]Did a complete remove again...
[*]Installed as per the Beryl wiki for Edgy + aiglx
[*]Things are looking sweet .... for now ;) 
[/LIST]

Cheers
Seine

---

### Post by 5h4rk on 2006-11-18
How do I do a complete removal?

---

### Post by Seine on 2006-11-18
In Synaptic, right click the package and choose "mark for complete removal"

---

### Post by Seine on 2006-11-18
If you have trouble with the number of workspaces, have you tried right clicking the workspace switcher (bottom right of screen) and looking at the preferences? There's a preference to change the number of workspaces.

After plugging my laptop into a Sony Bravia TV I once had my workspaces reduced from 4 to 2. (That was in Dapper, Edgy seems OK). I got it back to 4 by using the method above.

---

### Post by rkn5555 on 2006-11-19
i found that what i beleive was the trick, cuse i went thru so many different things to get beryl working right.'
it was getting rid of old packages..
go to SYSTEM--->Administration--->SYNAPTIC
ok now in the window pane on the right in synaptic.
type 
beryl
(make note of which version of beryl you are currently running, it shows up on the spalsh screen when beryl starts)
now that you see the different :beryl: packages, do not touch the current version, but on any other versions you see(earlier) right click on the box and mark for complete removal.

then after doing that click on apply.

One note,, just before my beryl started working right, it took a few minutes for all the window decorations and animations to come together. at first the themes wouldnt complete. my title bar would have no buttons and other quirky things. it was like trying to jumpstart my old Ford.. but since then, its awesome

---

### Post by paradoxchild on 2006-11-24
ive been using this post and anothers to fix my beryl, one thing ive done is setting your refresh rate at 200 in settings but also have on detect refresh rate. after you've done that maybe even reload window manager (right click on icon). theres also some help at these forums,

[https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy)
[http://www.ubuntuforums.org/showthread.php?t=290841&highlight=download+open+source+ati+driver](http://www.ubuntuforums.org/showthread.php?t=290841&highlight=download+open+source+ati+driver)

save a backup of xorg.conf so you just in case, otherwise just dpkg-reconfigure it if it messes up.

---

