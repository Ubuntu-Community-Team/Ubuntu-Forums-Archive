---
title: "Simplifying the UI with windicators"
date: 2010-06-08
forum: Art &amp; Design
---

### Post by lootic on 2010-06-08
I was testing making mockups and well I thought I share the result. Every part except the windicator Icons and the media Icons are from some part of already existing Ubuntu UI(banshee, rhythmbox and software-center). Without the menubar the window looked a bit "thin"(or how to express it), thus the toolbar got the menubars color.

[http://lootic.deviantart.com/art/Musicplayer-Decluttered-166893951](http://lootic.deviantart.com/art/Musicplayer-Decluttered-166893951)
(Read the explanation for details on the windicator menus)

---

### Post by vkontakte on 2010-06-08
> **lootic said:**
> I was testing making mockups and well I thought I share the result. Every part except the windicator Icons and the media Icons are from some part of already existing Ubuntu UI(banshee, rhythmbox and software-center). Without the menubar the window looked a bit "thin"(or how to express it), thus the toolbar got the menubars color.

[http://lootic.deviantart.com/art/Musicplayer-Decluttered-166893951](http://lootic.deviantart.com/art/Musicplayer-Decluttered-166893951)
(Read the explanation for details on the windicator menus)
I can find anything on this mockup but simplifying.

---

### Post by lootic on 2010-06-08
> **vkontakte said:**
> I can find anything on this mockup but simplifying.

I can find any comment more helpful, :p. Why the dislike?

---

### Post by vkontakte on 2010-06-08
It's not clear at all what these signs are about. Well, the volume sign is OK, but others aren't. Indicators and other canonical stuff aren't good thought out and mostly against the HIG. I'm very afraid of Ubuntu's Gnome. Breaking the usability guidelines leads to the mess similar to ones in both KDE and Windows.

---

### Post by lootic on 2010-06-08
> **vkontakte said:**
> It's not clear at all what these signs are about. Well, the volume sign is OK, but others aren't. Indicators and other canonical stuff aren't good thought out and mostly against the HIG. I'm very afraid of Ubuntu's Gnome. Breaking the usability guidelines leads to the mess similar to ones in both KDE and Windows.

It isnt the first Gnome guidelines Ubuntu breaks. I think the diffrence is that Ubuntu actually have in a kind of way, created new HIG to remove mess. I have made the two windicators thats not the sound windicator myself so it is understandable they arent perfectly choosen. I hate menu bars, so I tried to see how banshee could do without them using a few windicators instead.

So you should probably hate me and my design(or lack of it if you wish) made instead of Canonical and Ubuntu. ;)

Btw there is a problem with mac too, it doesnt allow you to do anything, I wanted to remove the file .trash100 on a SDcard with a MAC, I couldnt view hidden files so even though I knew it was there I couldnt get to it in finder. Then when I finally located the SDcard through the terminal, which wasnt under /dev or /media, "sudo rm -rf .trash100/" didnt work at all, giving some error message about that it wasnt allowed. The mac user said he knew the was a way to view hidden files but couldnt remember. So I took the SDcard home and did it in linux instead :p.

---

### Post by vkontakte on 2010-06-08
> **lootic said:**
> It isnt the first Gnome guidelines Ubuntu breaks. I think the diffrence is that Ubuntu actually have in a kind of way, created new HIG to remove mess. I have made the two windicators thats not the sound windicator myself so it is understandable they arent perfectly choosen. I hate menu bars, so I tried to see how banshee could do without them using a few windicators instead.

So you should probably hate me and my design(or lack of it if you wish) made instead of Canonical and Ubuntu. ;)

Btw there is a problem with mac too, it doesnt allow you to do anything, I wanted to remove the file .trash100 on a SDcard with a MAC, I couldnt view hidden files so even though I knew it was there I couldnt get to it in finder. Then when I finally located the SDcard through the terminal, which wasnt under /dev or /media, "sudo rm -rf .trash100/" didnt work at all, giving some error message about that it wasnt allowed. The mac user said he knew the was a way to view hidden files but couldnt remember. So I took the SDcard home and did it in linux instead :p.
I really can't understand what "mess" they are talking about when speak their indicators saved us from. Most apps always work in the way: left click to raise the app, right click to show menu. There were no mess actually. The only app from the default install that broke this rule was Tomboy, but they failed with it when tried to switch it to the indicators, because of the tomboy design and it's still in notification area. I'm sure they could do nothing with this app, because their approach is really bad thought out.

So we have now: tomboy causes the mess as before, and we have rhythmbox and transmission indicators that are less functional than their notification area counterparts. In addition, they are less consistent than tray icons, because there is no common way to raise the app: just check where the RB's "show app" and Transmission "open app" items. They even look different! 
**<sarcasm>So much consistency!</sarcasm>**

Another annoying regression is nautilus copying popup. Just look at this "wonderful" indicator with the only item: open the copying dialog :mrgreen:

PS In the early 1990s the world discovered how inconvenient menus are. In the 2009 bunch of designers with no idea about usability thought they are smarter than guys who had a huge expirience and defined HIG rules. I hope canonical guys are clever and fast learning to realize how wrong they were and refuse from this strange method.

---

### Post by vkontakte on 2010-06-08
In any case there will be a mess until canonical refuse from indicators. Most people who writing desktop apps for linux don't use Ubuntu. So no indicator support.

---

