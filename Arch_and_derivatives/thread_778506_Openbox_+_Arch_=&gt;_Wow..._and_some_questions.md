---
title: "Openbox + Arch =&gt; Wow... and some questions"
date: 2008-05-02
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-05-02
Got openbox running on Arch yesterday. I have already tried many lightweight WMs in the past but never gave any a 'serious' look. I always come back to GNOME. Having used linux full time (at home) about two years now, I now appreciate how **simplicity can also be a beauty**. Openbox has not failed to impress me. Its lightning fast, highly customizable and well documented. I've got everything configured to my liking and need (menu, keybinding, dynamic menus). 

But one thing I noticed is that the multimedia keys on the front panel of my laptop doesn't seem have any effect on the media players. Although mute/unmute works, nothing else do. It would be nice if I could get the play/pause/next/previous buttons working. Can someone point me in the right direction how do I get these configured in Openbox? 

Note: The keys work flawlessly in GNOME environment

---

### Post by Gigamo on 2008-05-02
Try the application called "xbindkeys". That works for me to get my multimedia keys bound.

---

### Post by kpkeerthi on 2008-05-02
Thanks. I read about xbindkeys. I understand how I can bind the keys to a specific application's functions with it. I wonder how can I use it to bind the multimedia keys in a generic way, so when I press the <play> key it activates 'play' funtion in the application that is currently running (and in focus) as I may be using rhythmbox sometimes and vlc some other times. Is this possible?

---

### Post by sarah.fauzia on 2009-01-07
I would like to do the same thing. All of my multimedia keys and special keys (for brightness) are recognized and mapped correctly (checked with xev). However, I need to bind them globally so they work in any application (like kpkeerthi wanted to do). I do use xbindkeys, but I don't know what command would work to play/pause, etc, etc in *any* application. My computer is a Lenovo Thinkpad X61 tablet, and I'm running a command line install of Ubuntu 8.10 (64-bit) with Openbox (not GNOME, so I'm not too keen on using the gnome-settings-daemon).

---

### Post by MisfitI38 on 2009-01-07
[Maybe this archwiki article will help.]("http://wiki.archlinux.org/index.php/Extra_Keyboard_Keys")

---

### Post by SomeGuyDude on 2009-01-09
I'm lazy, so all I did was install GMPC and bind all my keys to it through the preferences dialog. Takes care of volume and the various pause/forward buttons. 

And yes, Arch+Openbox is the sex.

---

### Post by SomeGuyDude on 2009-01-09
.

---

### Post by smartboyathome on 2009-01-09
Use keytouch to bind the keys (see the Wiki for more info). I used it to bind some of my keys which didn't do anything (to what I wanted them to be), and now I am happy. :)

---

