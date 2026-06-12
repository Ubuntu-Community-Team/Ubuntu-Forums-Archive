---
title: "MPlayer won't play DVDs..."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by feistyfirsttimer on 2007-06-26
I have the dvd codecs so I can play DVD movies on my PC.  I recently instaled MPlayer thru Synaptic.

But when I stick in a DVD, it wants to play in Totem.  How the heck do I make it use MPlayer instead?  Should I uninstall Totem?  Or what? :(

---

### Post by klytu on 2007-06-26
> **feistyfirsttimer said:**
> I have the dvd codecs so I can play DVD movies on my PC.  I recently instaled MPlayer thru Synaptic.

But when I stick in a DVD, it wants to play in Totem.  How the heck do I make it use MPlayer instead?  Should I uninstall Totem?  Or what? :(

If I understand your situation correctly, your subject line is misleading. I think you mean that you want mplayer to play your DVDs automatically when you insert them instead of totem playing them automatcally. Right? You can set the default player for your DVDs by going to System>Preferences>Removable Drives and Media. Click the multimedia tab and in the Video DVD discs command instead of ```
totem %m
``` (or whatever way the totem command is listed there ...)  put ```
gmplayer dvd://
``` for mplayer with a GUI or ```
mplayer dvd:// 
```for mplayer without a GUI. There are other ways to do this if you don´t mind using the terminal console. 

Before you do this, you should confirm that mplayer is actually going to work to play back your DVDs. When you insert a DVD and totem launches, just close it. Then launch mplayer from your Applications>Sound and Video menu and confirm you can play your DVD.

---

