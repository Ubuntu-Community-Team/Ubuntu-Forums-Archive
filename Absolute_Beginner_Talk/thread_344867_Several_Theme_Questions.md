---
title: "Several Theme Questions"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by mdumka on 2007-01-23
Hi there ...

I am quite new to Linux and found Ubuntu one of the best versions out there for me.

But I have been playing around and was looking to change my theme, I went to the website [www.gnome-look.org](www.gnome-look.org) and found tons of stuff ... now to my questions.

1) I installed Ubuntu with Xfce ... which I am guessing is Gnome, correct? 

2) Does that man that I can download any theme from [www.gnome-look.org?](www.gnome-look.org?)

3) I have been reading that you can to install your themes from the theme dialog box or by using the file system, I can access the home\myname\.themes folder (sorry for the windows like use!) and drop stuff in there ... but I can not access usr\share\themes folder ... is there a difference?

4) When you do use the them dialog box ... some times I get a incorrect file message. I understand that this may because the tar.gz is not packed correct, how is it supposed to be packed and what file is the dialog looking for?

5) Sort of silly but can Gnome use the Beryl themes? The reason I am asking is the ones I have downloaded all com in bin files.

6) And last but not least ... I have seen several themes that have the OSX like dockbar ... how do I do that?

Thanks for all your help.

Mike

---

### Post by maddog39 on 2007-01-23
No, if you installed with XFCE, then you are using a totally different desktop enviornment. You cang et XFCE themes at [www.xfce-look.org](www.xfce-look.org). Also when you install beryl, you are using a different window manager unrelated to GNOME/XFCE/KDE itself. Meaning it doesnt matter which desktop enviornment you are using then. However you must install beryl themes with the beryl themes manager. Instead of the default one. Also, you must unpacked your .tar.gz's sometimes with themes, because some of them are theme packs, which come with several variants of the theme you downloaded in one.

---

### Post by lyceum on 2007-01-23
> **mdumka said:**
> Hi there ...

I am quite new to Linux and found Ubuntu one of the best versions out there for me.

But I have been playing around and was looking to change my theme, I went to the website [www.gnome-look.org](www.gnome-look.org) and found tons of stuff ... now to my questions.

1) I installed Ubuntu with Xfce ... which I am guessing is Gnome, correct? 

[QUOTE=mdumka;2054043]2) Does that man that I can download any theme from [www.gnome-look.org?](www.gnome-look.org?)

No, you need to go to XFCE-look.org

> **mdumka said:**
> 3) I have been reading that you can to install your themes from the theme dialog box or by using the file system, I can access the home\myname\.themes folder (sorry for the windows like use!) and drop stuff in there ... but I can not access usr\share\themes folder ... is there a difference?

You should be able to use synaptic package manager to load the Gnome, then use "sessions" in the log-in manager to switch.

> **mdumka said:**
> 4) When you do use the them dialog box ... some times I get a incorrect file message. I understand that this may because the tar.gz is not packed correct, how is it supposed to be packed and what file is the dialog looking for?

see above

> **mdumka said:**
> 5) Sort of silly but can Gnome use the Beryl themes? The reason I am asking is the ones I have downloaded all com in bin files.

Yes, if you are using Beryl with Gnome (not trying to be smart, that it how it works, you use them together, you would not log out to use beryl)

> **mdumka said:**
> 6) And last but not least ... I have seen several themes that have the OSX like dockbar ... how do I do that?

gDesklets. Add/Remove or synaptic package manager. 

> **mdumka said:**
> Thanks for all your help.

Mike

you are wlcome.

---

### Post by mdumka on 2007-01-23
Hi Guys ...

Thanks for all of the help.

Some more follow up questions for both of you.

1) Beryl ... I am guessing a window manager that controls the way the interface looks? If so, where can I download that from and does it work with my configuration.

2) gDesklets ... I downloaded gDesklets-0.35.3.tar.bz2 from there website, but have no idea how to install it. I clicked add / remove but I could not choose the file on my desktop. As well ... in that list in the add / remove programs I had a program called Synaptic ... but how do I run it?

Thanks again folks ... here from you soon.

Mike

---

### Post by lyceum on 2007-01-24
I do not know too much about Beryl. You may want to look in the "How To" tips and tricks section. As for gDeskets, they are in add/remove. Synaptic package manager is a more powerful add/remove. Use it wisely. Be careful what you install or uninstall, but really you just click on what you want and it will be added or removed once you click on apply. You can get gdesklets from either. Once you have the program loaded, go to Aplications/accessories/gdesklets. Set them up the way you want. The easiest way I have found to load the mac-like icon bar is to right click on the program you want, set it to desk top then drag it to the gdesket tool bar. The delete the icon. I am sure there is a better way to do that, but I am too lazy to look for it. :)

---

### Post by mdumka on 2007-01-26
OK ... thanks for the help guys!

I have found Synaptic Page Manager .... But I cant figure out how to install gDesklets with it.

I have tried draging it to the application but it just floats to the desktop.

Is installing all programs this hard?

Thanks again for all your help.

Mike

---

### Post by Pobega on 2007-01-26
Actually lyceum, GTK themes work alongside Xfce themes to make a working skin. Xfce themes are just window decorations, while GTK (Gnome) themes are still the core of your skin. So he should be getting themes from both [http://xfce-look.org](http://xfce-look.org) and [http://gnome-look.org](http://gnome-look.org). The Gnome themes are selected in Applications -> Settings -> User Interface Settings and the Xfce themes are in Applications -> Settings -> Window Manager Settings.

---

