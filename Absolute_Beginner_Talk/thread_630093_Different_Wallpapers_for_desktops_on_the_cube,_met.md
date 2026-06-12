---
title: "Different Wallpapers for desktops on the cube, methods searched did not work for me"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by onikun86jp on 2007-12-03
Hi,
I'm a total Ubuntu beginner, and I barely even know how to work the terminal and I havent even made one successful compile. The thing I want to do I see everywhere, yet no matter what method I try it doesn't work. I'm using Gutsy Gibbon Ubuntu 7.1 i386 or something with Gnome stuff on my Dell Inspiron 1505. 
I know its so redundant to ask this, but I can't do it. A different wallpaper on each side of the cube. That's all I want to do to complete my custom setup. I've got a nice theme with Beryl, etc. I just want different wallpapers on each side of my cube.
So far I've tried the option of disabling Nautilus from drawing the desktop. That works, but it removes the icons. I'm too much of an icon person to not have them,
I've also tried Wallpapoz, but it fails miserably. It doesn't switch the wallpaper until seconds after I switch to that side.

Well, any advice to help a noob? I see so many people around who can do it, with their teaser videos but no explanations on youtube. I really want to do this. Any help?

Please help me find any of the following:
1 A plugin that just allows multiple desktops, or
2 something that will fix the icons if i disable Nautilus desktop 
3 something else entirely I overlooked that would be helpful

If I have to compile or patch anything, please explain how!
Why can't there be a simple deb for this...

---

### Post by jordanmthomas on 2007-12-03
I've never been interested in multiple wallpapers, so I haven't looked too much into it.
I can tell you, though, that you will not be able to get icons on your desktop if you disable nautilus.  Nautilus is what puts the icons there.

There is a plugin for compiz that allows you to have multiple wallpapers, but as you said, nautilus needs to be disabled.

This isn't the final answer (as in someone could likely come and prove me wrong) but I believe the easiest way to get multiple wallpapers going would be to use KDE since it has support built in.

---

### Post by Thanoulis on 2007-12-03
I tried multiple backgrounds myself, but seems that GNOME isn't familiar with that thing. Ican live with that. But if you **REALLY** want to have multiple desktop backgrounds, you'll have to move to KDE (it has native support).

---

### Post by Keen101 on 2007-12-03
You might want to try looking into a program called "wallpapoz".

[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)


My system doesent support the fancy compiz effects, so i'm not exactly sure if it works with compiz. (but the website says it does) But for me, wallpapoz is great for setting different backgrounds per each workspace in Gnome. I had to compile it from source, but it only took a few seconds. It was really easy.

I just had to extract it, and then browse to it with the terminal and issue the following command


sudo ./setup.py install

and after it compiled I had to install something else it needed for python. (i used synaptic to find it)

and the only thing I had to do next was go to >System >Prefrences >Sessions and make a launcher to launch "daemon_wallpapoz" every time the computer started up.



EDIT:


whoops, I didn't read that you had already tried Wallpapoz. Sorry, in that case either wait until gnome is faster at setting backgrounds (a future release hopefully), live without it, or move to KDE.

---

### Post by virtualnite on 2007-12-05
I am running compiz with kde and still am relegated to one wallpaper - how would one use multiple wallpapers in kde?

Thanks :)

---

### Post by jordanmthomas on 2007-12-05
Change the "setting for desktop" in the wallpaper-changing screen to the workspace you want to change.

---

### Post by russo.mic on 2008-05-19
Compiz and KDE's kwin don't talk quite right, as a result compiz only "sees" one virtual workspace.  As a result, no dice unless you want to give up having icons on your desktop.

There is no good way that I know of to get this feature.

Russo

---

