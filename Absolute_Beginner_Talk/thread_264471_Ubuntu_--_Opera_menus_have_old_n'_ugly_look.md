---
title: "Ubuntu -- Opera menus have old n' ugly look"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Asham on 2006-09-24
Hi forgive me for I am a newbie, trying to migrate to the Linux world.

My favorite browser has some quirks under **U**buntu, for instance the menus look terrible. See attached screenshot.

This does not apply to **K**Ubuntu so I ask you this: how can I fix this problem of mine *without leaving Ubuntu and Gnome?*

I'm loving Linux more and more for each day, and the switch from Windows has been going much better than I ever expected! :D

---

### Post by Omnios on 2006-09-24
I think its GTK-1 and the default gtk-1 theme is but ugly. FOund this fix and it also buitifies Xmms and Mplayer to name a few.

[http://ubuntuforums.org/showthread.php?t=107135](http://ubuntuforums.org/showthread.php?t=107135)

---

### Post by Asham on 2006-09-24
I am too tired for terminal/command-line stuff at the moment, I will give it ago tomorrow. But it does look promising, thanks!

Out of curiosity: is this a common problem (does it affect many applications)?

---

### Post by Colonel Kilkenny on 2006-09-24
Well you could install qt3config and some kde-themes. Then start Opera with "opera --style themename".
Do be able to do this you must use shared version of Opera. So install a package with shared on name instead of static.

---

### Post by Omnios on 2006-09-24
> 
Out of curiosity: is this a common problem (does it affect many applications)?
 There is GTK-1 which is the old graph lib and now I think they use GTk-2 as the gnome norm. This problem is because the default Gtk-1 theme in ubuntu is but ugly. The link I gave you will fix any app using GTK-1 window theme and the right click problems with many programs such as Xmms and Mplayer, now from what I remember the Mplayer right click menu was even uglier. Anyways I moded mine to use the plastic GTK-1 theme and it looks rather pretty lol. 

 Aperently there is still a few mainstream apps that have the gtk-1 problem such as mplayer where the main window looks good but the right click is the ugliest thing you have even seem lol.


 Oh ya there is also a KDE / GNome cross usage fix but I will have to look that up where you can install a kde theme for use in GNome and a Gnome theme to work in KDE.

 Also in kde you can set a GTK theme in KDE.

---

### Post by MWAAAHAAA on 2006-09-24
Just on a side note. Have you ever tried another browser? Why stick with a commercial, closed source, non-free browser. I do understand you are looking for linux ports of programs you used to use in windows. I, and probablym ost other people that switched to linux, did. But there are some very nice browsers available for linux too, browsers that are free. My personal favorite is konqueror. Although it isn't perfect, it does all I need it to do, and it's free. There are many, many others to choose from of course.

---

### Post by skymt on 2006-09-24
@all: Opera uses QT, not GTK 1. Install and use qtconfig to fix up Opera.

@MWAAAHAAA: Opera has a lot of features I depend on that I haven't found in anything else. The ad blocker is the best I've found, Site Preferences rocks, Page Zoom zooms images in addition to text, and it all works without slowing to a crawl, like Firefox does with lots of extensions.

---

### Post by MWAAAHAAA on 2006-09-25
I don't like firefox either for the reason that it is so damn slow. But konqueror does in fact have an adblock plugin! Unfortunately, it does not zoom images. At least not AFAIK.

---

### Post by Thirsteh on 2006-09-25
> **MWAAAHAAA said:**
> I don't like firefox either for the reason that it is so damn slow. But konqueror does in fact have an adblock plugin! Unfortunately, it does not zoom images. At least not AFAIK.

Try Swiftfox for speed :-)

---

### Post by skymt on 2006-09-25
> **MWAAAHAAA said:**
> I don't like firefox either for the reason that it is so damn slow. But konqueror does in fact have an adblock plugin! Unfortunately, it does not zoom images. At least not AFAIK.

All web browsers worth using have ad blockers built in or easily available. However, with Opera, I can right-click a page, choose "Block content" and click whatever I don't want to see. I have yet to see anything like that in another browser.

---

### Post by xpod on 2006-09-25
> can right-click a page, choose "Block content" and click whatever I don't want to see.

Aint you already seen it by then?....lol:mrgreen:

---

### Post by skymt on 2006-09-25
> **xpod said:**
> Aint you already seen it by then?....lol:mrgreen:

The point is that I never see it again. But I'm sure you know that. It's pretty smart, it'll block everything from the same directory as the image you block. This usually works, but I sometimes have to manually edit the pattern to get more of the ads.

---

### Post by Asham on 2006-10-07
> **skymt said:**
> Opera has a lot of features I depend on that I haven't found in anything else. The ad blocker is the best I've found, Site Preferences rocks, Page Zoom zooms images in addition to text, and it all works without slowing to a crawl, like Firefox does with lots of extensions.

Exactly. I don't want to install a hanful of extentions in order to do what I can already do with Opera. I was using Firefox/firebird before but not anymore. 
With that said, I don't want this to turn into a Firefox vs Opera discussion - both have their strength and weaknesses - let's agree on that.. mm kay? :)

I am just about to install QT -- I'll report back shortly (hopefully).

---

### Post by Asham on 2006-10-07
Okay. While it is possible to modify the qt look, isn't there some way of making it integrate nicely with the current GNOME theme?

In Windows the applications get their look and feel from the current theme of the OS but perhaps that is not possible in GNOME? It's not the biggest problem really, I just feel it would be nice having the applications share the visual appearance of the OS.

---

### Post by skymt on 2006-10-07
> **Asham said:**
> Okay. While it is possible to modify the qt look, isn't there some way of making it integrate nicely with the current GNOME theme?

In Windows the applications get their look and feel from the current theme of the OS but perhaps that is not possible in GNOME? It's not the biggest problem really, I just feel it would be nice having the applications share the visual appearance of the OS.

Windows programs all have the same look and feel because they all use the same toolkit. Linux has two main toolkits: GTK (GNOME, Firefox) and QT (KDE, Opera). So, if you want Opera to match the OS, either tweak QT until it looks pretty good, or use KDE.

---

### Post by Asham on 2006-10-07
Now I get it, I think. Well put.

I don't want to leave GNOME behind just yet - I like the UI too much for that - so I'm wondering: can I download KDE just to make the qt applications look nice(r) but still use GNOME for the other, by default installed apps? 

I hope that makes sense, I'm feeling kinda confused; all these alternatives for Window Managers and File managers (Nautilus), different toolkit and menus and what not... too many options for a newbie! :)

---

### Post by skymt on 2006-10-07
> **Asham said:**
> Now I get it, I think. Well put.

I don't want to leave GNOME behind just yet - I like the UI too much for that - so I'm wondering: can I download KDE just to make the qt applications look nice(r) but still use GNOME for the other, by default installed apps? 

I hope that makes sense, I'm feeling kinda confused; all these alternatives for Window Managers and File managers (Nautilus), different toolkit and menus and what not... too many options for a newbie! :)

You don't need to download all of KDE just to make Opera look better. Just install kde-style-klearlook and qt3-config (sudo aptitude install kde-style-klearlook qt3-config). Then run qtconfig (hit Alt-F2, type "qtconfig", and hit enter). In qtconfig, select klearlook and tweak the color options until you like it.

---

### Post by Asham on 2006-10-07
I'm loving these forums already. Thank you so much for the help! :D

"qt3-config" didn't work for me, but "qtconfig" did.

---

### Post by skymt on 2006-10-07
> **Asham said:**
> I'm loving these forums already. Thank you so much for the help! :D

"qt3-config" didn't work for me, but "qtconfig" did.

Sorry, you're right. I'll fix it. I hadn't used it in a while, so I assumed the command name was the same as the package name.

You're welcome!

---

