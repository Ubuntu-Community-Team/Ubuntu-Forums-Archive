---
title: "GNOME 3- before I give up on it completely..."
date: 2011-11-20
forum: Any Other OS
---

### Post by Rubicon421 on 2011-11-20
I've been using GNOME 3 for a few days now and there are so many things about it I don't like, that I'm just about to give up on it completely. But before I do, I thought I'd get some community input on it and see what everyone else has done to be able to live with it an if you eventually end up liking it. 

I'm not looking for specific fixes for each issue I am about to list, because if each one requires some extra package or tweaking of a config file to get around the issue, then why even run GNOME 3, right? I'm more so looking for any kind of overall fix, something like gnome-tweak-tool but with more options. 

So far, here's what I don't like and can't figure out how to change:
move window buttons to left
modify menu in bottom toolbar
open as administrator is missing from nautilus context menu
edit options for panels
customize themes (change icons independently of window borders, etc...)
slider bar for icon size is missing in nautilus
can't set folder background image in nautilus


By the way, I know some of these features are not there by default in GNOME 2. I just upgraded from Linux Mint 11 to 12 so I am more so referring to the differences GNOME 3 has in LM12, not GNOME 3 in Ubuntu. Overall, GNOME 3 just seems very locked down. I don't mind the defaults being different than what I'm use to there's just not enough options available to the user to change those defaults.

---

### Post by sanderd17 on 2011-11-20
> **Rubicon421 said:**
> I've been using GNOME 3 for a few days now and there are so many things about it I don't like, that I'm just about to give up on it completely. But before I do, I thought I'd get some community input on it and see what everyone else has done to be able to live with it an if you eventually end up liking it. 

I'm not looking for specific fixes for each issue I am about to list, because if each one requires some extra package or tweaking of a config file to get around the issue, then why even run GNOME 3, right? I'm more so looking for any kind of overall fix, something like gnome-tweak-tool but with more options. 

So far, here's what I don't like and can't figure out how to change:
move window buttons to left

This can be done from the gconf (or dconf) tool.
> 
modify menu in bottom toolbar

Don't know what menu you mean.
> 
open as administrator is missing from nautilus context menu

This was never default in Nautilus. This has always been an extension/plugin.
> 
edit options for panels

You can't edit them directly, that's what extensions are made for.
> 
customize themes (change icons independently of window borders, etc...)

Isn't this in Gnome Tweak tool?
> 
slider bar for icon size is missing in nautilus
can't set folder background image in nautilus

That's with the new nautilus indeed
> 


By the way, I know some of these features are not there by default in GNOME 2. I just upgraded from Linux Mint 11 to 12 so I am more so referring to the differences GNOME 3 has in LM12, not GNOME 3 in Ubuntu. Overall, GNOME 3 just seems very locked down. I don't mind the defaults being different than what I'm use to there's just not enough options available to the user to change those defaults.

Gnome3 is just very free in my opinion, but there isn't a graphical interface for most settings yet. You need to change the code (directly or via installing extensions). But the code is quite easy, it's just like a website.

---

### Post by Perfect Storm on 2011-11-20
Moved to Other OS/Distro Talk.

---

### Post by Rubicon421 on 2011-11-20
> **sanderd17 said:**
> 

Gnome3 is just very free in my opinion, but there isn't a graphical interface for most settings yet. You need to change the code (directly or via installing extensions). But the code is quite easy, it's just like a website.


I think you missed the point of my question, but you ended up answering it anyway. I don't want to have to tweak every little thing that annoys me about GNOME 3. I don't want a specific fix for every little issue. I was looking for an overall fix, GUI or some other kind of tweaking tool to give me more control over GNOME 3. But if there isn't a GUI like you said, then that answers it for me, so thank you. 

IMHO, as someone who is not a power user, if there is no GUI to change settings out of the box, then GNOME 3 is at least somewhat locked down. I suppose for someone who knows what config files to edit and knows all the terminal commands then it may seem very open, but from that perspective, you could say Windows and OSX are open as well.

---

### Post by jerrrys on 2011-11-20
"open as administrator is missing from nautilus context menu"

this has always been an addon and not part of the default install

[ATTACH]207628[/ATTACH]

---

### Post by Rubicon421 on 2011-11-20
> **jerrrys said:**
> "open as administrator is missing from nautilus context menu"

this has always been an addon and not part of the default install

[ATTACH]207628[/ATTACH]

Like I said in the first post, I'm using LinuxMint, not Ubuntu. I'm pretty sure that is one of the added packages in the default Mint install but I may be mistaken.

---

### Post by Anastasis on 2011-11-20
You guys may want to check out Mint again. There's a lot of updates that have been passed down just in the last few days.

Mint looks like their trying to really streamline Gnome 3 and fully integrate it with MATE. If MATE is ported to GTK3..dudes, this things gonna go viral.

I can't really believe what I'm seeing here. And I'm not sure everyone understands what this implies. Unless I'm mistaken, I'm seeing Linux history in the making.

This is cool. And man, did we need it. I just know there are some IT and server specialists right now leaping for joy. 

And somebody get Debian on the horn and tell em what up. :popcorn:

Nice job, Perberos. You should get TUX of the year award for this.

---

### Post by sanderd17 on 2011-11-20
> **Rubicon421 said:**
> 

IMHO, as someone who is not a power user, if there is no GUI to change settings out of the box, then GNOME 3 is at least somewhat locked down. I suppose for someone who knows what config files to edit and knows all the terminal commands then it may seem very open, but from that perspective, you could say Windows and OSX are open as well.

There is a big difference between
[LIST]
[*]Changing config files, and reloading the environment
[*]Changing source code and recompiling everything
[*]Not being able to change anything
[/LIST]

Gnome 3 is very strong at the first point, for the moment they are just lacking GUI tools to change the settings. But give them some time to mature. A lot of open source apps fit in the second category, where you can do everything by changing the source, but that's not trivial. Even not for power users. And MS Windows but certainly OSX and iOS fall under the third one. Where you aren't able to do anything.

So if you don't have the time to search through configuration files yourself, let others do it, and wait while they get used to it and develop tools for it.

---

### Post by cbowman57 on 2011-11-20
Getting Open as Administrator back in Nautilus 3:

```
sudo ln -s /usr/lib/nautilus/extensions-2.0/libnautilus-gksu.so /usr/lib/nautilus/extensions-3.0/libnautilus-gksu.so
```

Source [Ask Ubuntu]("http://askubuntu.com/questions/78116/where-is-the-open-as-administrator-option-in-nautilus-gone")

---

### Post by BigCityCat on 2011-11-20
One thing that makes usability a whole lot better it install the dock extension or install something like Avant to launch your programs. So you don't have to go to activities every time you want to switch between apps.

---

### Post by sanderd17 on 2011-11-21
> **BigCityCat said:**
> One thing that makes usability a whole lot better it install the dock extension or install something like Avant to launch your programs. So you don't have to go to activities every time you want to switch between apps.

Mint has a task-bar by default in Gnome Shell. So I don't think the OP needs a dock.

---

### Post by jimrew111 on 2011-11-22
[LEFT] don't use shell just use fallback mode.
then you will love it.   
[/LEFT]

---

### Post by collisionystm on 2011-11-22
Dude...

Just install KDE or something.

With KDE you can move the panel the top of the screen if you prefer that look. It has so many more things to modify.
Gnome 3 is fancy but its pretty basic right now. It is still getting developer attention so it will take some time for better features to roll out.

Or... if you are into the whole minimalist, follow torvolds thing you can install xfce or lxde.

---

### Post by thatguruguy on 2011-11-22
> **Rubicon421 said:**
> Like I said in the first post, I'm using LinuxMint, not Ubuntu. I'm pretty sure that is one of the added packages in the default Mint install but I may be mistaken.

If this is a LinuxMint-specific feature, why aren't you asking your questions on the LinuxMint forum?  I'm not bashing, I'm just curious.  Wouldn't they be able to help you better with regards to questions about that particular OS?

---

### Post by jimrew111 on 2011-11-22
use XFCE its more like g2 then really anything.
its funny that xfce has a mac os9 theme lol.

---

### Post by BrokenKingpin on 2011-11-25
> **jimrew111 said:**
> use XFCE its more like g2 then really anything.

++

I am sure you may be able to resolve those Gnome3 issues, but what is the point if there is something out there that already does the job.

---

### Post by ernestj on 2011-11-26
I agree with XFCE. I tried Linx Mint 12 RC and did not like it. It is not that the developers did anything wrong, it is just that GNOME 3 is awful. It needs a lot, I mean a lot of work. Linux Mint tried to make GNOME 3 livable, but still in the end GNOME 3 is in it's infancy. I, personally gave up. I love Ubuntu, I love Unity. I did, however, try XFCE and I am completely hooked. I am running Xubuntu with AWN dock and would not trade it for GNOME 3. The best thing you can do is wait for elementary os Luna to come out in February. Pantheon hopefully will do the trick.

---

