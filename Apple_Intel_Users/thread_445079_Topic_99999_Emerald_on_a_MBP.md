---
title: "Topic 99999: Emerald on a MBP"
date: 2007-05-15
forum: Apple Intel Users
---

### Post by (pr) on 2007-05-15
Sorry for yet another topic on the subject.

I've installed Beryl using the guide I've found  [here]("http://http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m").


First: at the end (following the guide) I have no 'beryl-manager' command. I do have a 'beryl-settings' command.  Most things do work (wobbly - cube - etc.). Did anybody else experience this? Should I just type 'sudo apt-get install beryl-manager' or not. 

The one thing that doesn't work: Emerald themes. I can go to the Emerald settings, click on any of the themes. Nothing happens. I just want Emerald themes; unless it's not possible. 

Any advice?

---

### Post by benanzo on 2007-05-15
you have to install beryl-manager explicitly.  It's not a dependency of Beryl

```
sudo apt-get install beryl-manager
```

When you run beryl-manager you need to select the Window Decorator in the right-click menu of the icon in your status tray.  Make sure that it's emerald, then it will work fine.

---

### Post by (pr) on 2007-05-15
Thx, (you're a great help!)

Though something still doesn't look okay: (I seem to have no decorations at all)

[IMG]http://farm1.static.flickr.com/232/499873628_cd6bfb8ad2_o.png[/IMG]

---

### Post by Gen2ly on 2007-05-15
Shoot.  Is there an emerald-them-manager on your system.\?

---

### Post by ronocdh on 2007-05-15
The problem can be sort of solved by switching to the Metacity window manager. This means that Emerald themes will not work, instead the default Ubuntu ones will display. But that's better than nothing.

For what it's worth, I had the same problem. I later wiped my system and reinstalled, and now the Beryl installation works flawlessly. Which version of Ubuntu are you using? Feisty I assume, but i386 or 64-bit?

---

### Post by (pr) on 2007-05-16
I have an 'older' MBP 2 GHz (using a 256mb Vcard; a X1600 if I'm not mistaken). That's only 32bits so I have installed the i386 version. Emerald theme manager seems to be installed. In fact: switching themes in Emerald does change the small 'lines' I do see on the side. My OS is Ubuntu 7.04.


How is it possible that we all follow the same guide and get different results, using the same computer? :confused:

---

### Post by fractalzero on 2007-05-16
1. Open the beryl-manager. 
2. Right click on the big red diamond icon.
3. Click the menu item which reads "Reload Window Decorator"


Sometimes I have to do this after I switch themes or window managers.

---

### Post by (pr) on 2007-05-16
> **fractalzero said:**
> 1. Open the beryl-manager. 
2. Right click on the big red diamond icon.
3. Click the menu item which reads "Reload Window Decorator"


Sometimes I have to do this after I switch themes or window managers.

I've tried that a few times :frown: I've Googled the subject: even tried Nvidia solutions (editing the xconf.org), tried every option possible in the diamond red icon, ...


Or the guide I'm using is missing some key steps or I'm doing something bizarre wrong. It's getting frustrated: in fact finding the error and undoing it, won't make my system any more productive. Perhaps I should just stop looking.

---

### Post by ronocdh on 2007-05-16
> **ronocdh said:**
> The problem can be sort of solved **by switching to the Metacity window manager. **This means that Emerald themes will not work, instead the default Ubuntu ones will display. But that's better than nothing.

Did you try this, PR?

---

### Post by (pr) on 2007-05-16
Yeah, that works but that doesn't feel like a solution; it's just a mere bypass. 
In fact I'm one those wierdos who has installed Bery simply to start using the Emerald themes.

---

### Post by Gen2ly on 2007-05-16
Personally, I don't think Beryl should be part of the standard install.  It just isn't ready yet.  Also consider that large updates for Beryl won't be happening anytime soon as Beryl and Compiz are in sort of a merger.

---

### Post by ronocdh on 2007-05-17
> **(pr) said:**
> Yeah, that works but that doesn't feel like a solution; it's just a mere bypass. 
In fact I'm one those wierdos who has installed Bery simply to start using the Emerald themes.
Hm, well, by following the same guide you've linked to, I initially had the same results, and had to use the Metacity WM. This meant no Emerald themes, but at least I had basic Beryl effects, like the neato flippycube. After reformatting and reinstalling, then following the same guide, both Beryl effects and Emerald themes work. :!:

I am sorry if that emoticon looks like a butt.

And Dirk, I just think the companies refusing to allow open drivers are the party that's "not ready." Semantics, perhaps, but let's keep the blame where it's supposed to be, if indeed blame is meant at all. I think the Restricted Drivers Manager in Feisty is a huge step forward in marrying the libre software stuff with the real-world pragmatism which you (and many others!) seem to espouse. I think that everyone can in fact get along. ;)

---

